---
layout: post
title: Writing Programs
date: '2016-01-22 23:37'
tags:
  - testing
  - learning
  - software design
categories:
  - programming
---

This evening I was browsing [reddit](www.reddit.com) and came across an interesting question: "[Groovy] As a new developer in a highly skilled development team, I am struggling to keep up with them... Any tips or suggestions to improve?".

# A Quotable Post
The [post](https://www.reddit.com/r/learnprogramming/comments/426e7a/groovy_as_a_new_developer_in_a_highly_skilled/) in question. The top [comment(s)](https://www.reddit.com/r/learnprogramming/comments/426e7a/groovy_as_a_new_developer_in_a_highly_skilled/cz8669h) from [/u/DoomGoober](https://www.reddit.com/user/DoomGoober) do not disappoint.

> You can write basic functions, right? The trick is breaking every problem down into basic functions that you know how to code.
>
> For example, let's say you work at a dating site and you want to send emails to every two people who are compatible. Sounds simple, right? But how do you start? Well first, you need to break down what compatible means. Well, compatible means two people have the same personality score. Ok, how do you I get the personality score? Well, you call the database. How do you call the database? Well, there's a function called GetPersonalityScoreFromDatabase(int id)! Ok, now we build back up. What did I want from the personality score? Well, I want to find all ids for scores that are the same. How do I do that? Well, I could use a dictionary to bucket all of the people with the same scores: score to id. So I need to move all id,score pairs into the dictionary. How do I do that? Well, I have a list of all of the users from GetIDs() so I write a loop... etc.
>
> Break everything down, build it up. Start with the complex question and keep asking "how do I do that?" for each step, until you say, "I know how to code that!" Then you start coding.
>
> The part where experience really comes into play is knowing what tools are available. For example, until you use it, you probably wouldn't know a dictionary would be good to match ids to scores. And you might not know that the function GetIDs() exists. That comes from: 1) Experience. 2) Good documentation 3) Google (learning how to phrase programming questions so you get the answer from Google/Stackoverflow is a great skill!)

And his follow-up: (slightly edited)

> There are some tricks to achieving what I said in my original comment. The two most obvious are coding stubs and writing everything down as a hierarchy. I'll briefly describe coding stubs, cause it's similar to hierarchy but you're actually writing code.
>
> Start with this function that does nothing. It's called a stub:
>
> SendEmailToCompatiblePairs()
>
> Add some stubs to the stub:

```
SendEmailToCompatiblePairs() {
    GenerateListsOfCompatiblePeople();
    EmailPeople();
}
```

> Don't worry about what those two new stubs are going to do! You'll worry about that later.
>
> Now start to stub out the insides of GenerateListsOfCompatiblePeople():

```
List<List<int>> GenerateListsOfCompatiblePeople() {
    Dictionary<int, List<int>> scoreToIDs;
    foreach (id in ids) {
        AddPersonTo(scoreToIds, id);
    }

    return DictionaryToListOfLists(scoreToIds);
}
```

> etc. Each time you come to a new step, you write a new function name down. You don't care how that function will work -- just assume it works. Write out all of the steps in your current function. Then choose one of your empty non-working functions and do the whole thing again, until you have all actual working code. Then go back up the hierarchy and fix the functions to pass data from one to the other. In my example, GenerateListsOfCompatiblePeople() needs to give a list of ids to EmailPeople().

Maybe this isn't the best to admit, but for as long as I've been writing code I can't say I've approached it this way. I usually just dive in writing full functions, if not just straight procedure all the way through. Granted, up until relatively recently, much of what I have written are scripts, not full applications. The response above also goes along with the idea that really I ought to be writing more tests as I go...

The whole thing struck me enough to want to write up a post on it to capture the information....

# Reading Material
A couple people suggested a few books (like I really need to buy more):

- [Growing Object-Oriented Software Guided by Tests](http://amzn.com/0321503627)
  - [website](http://www.growing-object-oriented-software.com/)
  - after reading the reviews I ordered a copy (physical)
- [Clean Code: A Handbook of Agile Software Craftsmanship](http://amzn.com/0132350882)
  - I already own this book, I believe Util had shown it at one of the Perl meetings.
  - I need to go back and read over it again.
- [Head First Design Patterns](http://amzn.com/0596007124)
  - I don't think I have this; may have a soft copy...
- [Code Complete: A Practical Handbook of Software Construction, Second Edition](http://amzn.com/0735619670)
  - I believe I've seen this mentioned in other places...

- Came across this post a bit later on, saving it here as I'm headed to bed.
  - (How to be a great software developer](http://peternixey.com/post/83510597580/how-to-be-a-great-software-developer)
