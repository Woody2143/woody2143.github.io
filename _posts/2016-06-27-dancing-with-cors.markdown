---
layout: post
title: Dancing with CORS
date: '2016-06-27 21:40'
tags:
  - perl
  - dancer
  - dancer2
  - CORS
categories:
  - programming
---

I imagine if you are on this page you have heard of [Dancer](https://metacpan.org/pod/Dancer) (and/or [Dancer2](https://metacpan.org/pod/Dancer2)). If you didn't know; go read the docs on it; I'm not going to take the time to list their virtues here.

I have a couple of apps written using Dancer on the backend, serving up JSON via AJAX requests. I ran in to an issue with one of the apps that the backend was hosted on a different server than the front end page was served from. Why? Cause reasons, it happens. I fired up the page and attempted to get it to pull data but the browser complained at me and some digging lead me in to reading about [Cross-Origin Resource Sharing](http://enable-cors.org/) (CORS). Which boils down to the fact that I need the backend to tell the browser that other origins are allowed to make requests to it. This is done by adding an HTTP header:

```
Access-Control-Allow-Origin: *
```

As you can guess, the wild card means that any origin can make a request. You can, and I'm guessing likely should, list specific URLs. I can't say I've ever done it as these tools are internal and I don't really care who requests/uses the data.

Ok, so how the question then became, how do I get Dancer to serve up this header. It ended up being pretty simple. It was just a matter of putting in the 'header' keyword in the route that was being called.

```
get '/send/header', sub {
    header 'Access-Control-Allow-Origin' => '*';
}
```

That gets the job done well enough; but isn't very DRY. The nice thing with Dancer is that there is a way to have a block of code ran before each route, and that is with a 'before' hook.

```
hook 'before' => sub {
    header 'Access-Control-Allow-Origin' => '*';
};
```

So now, no matter what, CORS should be enabled.

Well....

Almost.

The one problem I ran in to after this was the fact that when I sent an error back (a non '200 OK' response to a request) the CORS header wasn't there and the browser isn't a fan of that.

I attempted to use the 'error' hooks that Dancer provides but all my attempts to send the header via Dancer failed. So, it was back to the web. As with every problem, ever, someone else had to have run in to this before me.

My searching lead me to this fine page: [http://enable-cors.org/server_perl.html](http://enable-cors.org/server_perl.html). If a gun was to my head I doubt I'd be able to explain [Plack](http://plackperl.org/) beyond that first paragraph on the page says. But I know I am using it to fire up Dancer. So I pulled down the package specified, [Plack::Middleware::CrossOrigin](https://metacpan.org/pod/Plack::Middleware::CrossOrigin) and added it to the psgi builder block as specified.

```
use Dancer2;
use MyWebApp;
use Plack::Builder;

builder {
    enable 'CrossOrigin', origins => '*';
    dance;
};
```

It's worth noting that at some point I had switched over to CURL to view the headers instead of looking in a browser. So I knew that the 'header' keyword in Dancer was working so I pulled that out after adding this plack module and retested.

```
$ curl --verbose http://localhost:5000/
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 5000 (#0)
> GET / HTTP/1.1
> User-Agent: curl/7.40.0
> Host: localhost:5000
> Accept: */*
>
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Date: Sat, 18 Jun 2016 04:35:30 GMT
< Server: HTTP::Server::PSGI
< Server: Perl Dancer2 0.200001
< Content-Length: 375
< Content-Type: text/html; charset=UTF-8
```

While searching around and looking at things related to this issue I had seen posts complaining that this specific Plack module did not work. So I wasn't surprised to see that it didn't work right off the bat. So I decided to dig in to the module itself to see what was up.

I'd like to say I immediately saw the offending bit of code, but I had to play around with it a little bit before it hit me that the it was looking for the 'HTTP_ORIGIN' header.

```
#Plack/Middleware/CrossOrigin.pm
sub call {
    my ($self, $env) = @_;
    my $origin = $env->{HTTP_ORIGIN};
    my $continue_on_failure;
    if ($origin) {
        $continue_on_failure = $self->continue_on_failure;
    }
```

So I looked up how to send the header via curl and retested.

```
$ curl -H "Origin: http://blah.com" --verbose http://localhost:5000/
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 5000 (#0)
> GET / HTTP/1.1
> User-Agent: curl/7.40.0
> Host: localhost:5000
> Accept: */*
> Origin: http://blah.com
>
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Date: Sat, 18 Jun 2016 04:35:30 GMT
< Server: HTTP::Server::PSGI
< Server: Perl Dancer2 0.200001
< Content-Length: 375
< Content-Type: text/html; charset=UTF-8
< Access-Control-Allow-Origin: *
< Access-Control-Expose-Headers:
```

So now we are back at the same point as when Dancer was sending the header. Now to test sending an error.

```
#In Dancer
send_error("Not logged in", 401);
```

And here we see Plack::Middleware::CrossOrigin is doing what I need it to do.

```
$ curl -H "Origin: http://blah.com" --verbose http://localhost:5000/
*   Trying 127.0.0.1...
* Connected to localhost (127.0.0.1) port 5000 (#0)
> GET / HTTP/1.1
> User-Agent: curl/7.40.0
> Host: localhost:5000
> Accept: */*
> Origin: http://blah.com
>
* HTTP 1.0, assume close after body
< HTTP/1.0 401 Unauthorized
< Date: Sat, 18 Jun 2016 04:36:12 GMT
< Server: HTTP::Server::PSGI
< Server: Perl Dancer2 0.200001
< Content-Length: 463
< Content-Type: text/html; charset=UTF-8
< Access-Control-Allow-Origin: *
< Access-Control-Expose-Headers:
```

I went the long way around to get here, but figured it was at least worth writing up in case someone else has trouble with Dancer and CORS.
