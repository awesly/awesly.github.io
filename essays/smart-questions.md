---
layout: essay
type: essay
title: "Crafting a Question: From Forum Posts to AI Prompts"
# All dates must be YYYY-MM-DD format!
date: 2025-01-30
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<div style="display: flex; justify-content: center; align-items: center; gap: 20px;">
    <img src="../img/stack-overflow-logo-png-transparent.png" alt="Stack Overflow Logo" width="200">
    <img src="../img/open-ai-logo.png" alt="OpenAI Logo" width="200">
</div>

## The lost art of posting good questions on forums

The internet has continually grown and changed ever since its conception, and it will continue to. In an earlier age than now, programmers used primarily Stack Overflow for asking the tech community questions about bugs in their code, how to work specific software, and theoretical computer science questions. Depending on a person's use of Stack Overflow, it could be incredibly helpful. When I was in high school, I used it for debugging - as a "lurker," never posting myself, but finding other people's previous questions and answers were similar to mine when googling error messages and general questions. However, for the last multiple years I have completely stopping using Stack Overflow, both because I am googling for answers less, and Google prioretizes it in results less. The reason: generative AI as a replacement. For debugging I usually just use ChatGPT, and when Googling a general programming question, instead of reccomending relevant websites and having a blurb at the top of the page taken directly from a website, this has been replaced with Google's AI results feature, which usually summarizes the possible context and answers well enough to remove any futher neccessity to look through the websites listed below it - including Stack Overflow. 

## Platforms may change, but good questions will always perservere

This all might make one think that considering what is a good question for a forum is outdated, but in actuality, good questions are good no matter the platform, and so good forum questions from the 2000's and 2010's will also make good AI prompts for the 2020's. Reccomendations for a good forum post almost completely apply to AI prompts as well. Here is an example.

## A good question

[Link](https://stackoverflow.com/questions/40480/is-java-pass-by-reference-or-pass-by-value) to a good question on Stack Overflow.
Here, a Stack Overflow user asked the question: 
```
Q: Is Java "pass-by-reference" or "pass-by-value"?

With the text body:
I always thought Java uses pass-by-reference. However, I read a blog post which claims that Java uses pass-by-value. I don't think I understand the distinction the author is making.

What is the explanation?
```

While the reiterating at the end that a question is being asked is not reccomended because it is redundant and may annoy other users, it is a small enough error to look past. This question was effective, and therefore a good question, because it was clear in exactly what the question was, the user's current understanding of the context, and even hyperlinked "a blog post" so that others could know what misunderstanding caused the question to arise. This was short and sweet, letting other users know important information about the question and nothing else.

The top answer received was:

```
A:

The terms "pass-by-value" and "pass-by-reference" have special, precisely defined meanings in computer science. These meanings differ from the intuition many people have when first hearing the terms. Much of the confusion in this discussion seems to come from this fact.

The terms "pass-by-value" and "pass-by-reference" are talking about variables. Pass-by-value means that the value of a variable is passed to a function/method. Pass-by-reference means that a reference to that variable is passed to the function. The latter gives the function a way to change the contents of the variable.

By those definitions, Java is always pass-by-value. Unfortunately, when we deal with variables holding objects we are really dealing with object-handles called references which are passed-by-value as well. This terminology and semantics easily confuse many beginners.

It goes like this:
[continues with a code example]

```
 
The user received many answers to their question, over 7,000 upvotes, and currently 2.8 million views on the post, which shows how good a question it was for Stack Overflow at the time. Another aspect of the question that makes it such a good one is that it is interesting to programmers, as it is both a theory and "behind the scenes" understanding question, and actually helps programmers to understand the language they're using and how to use it. This makes it a post that many users would also like to know the answer to or share even more clarification for, and the clear phrasing of the question allows it to show up in search results for those who may have the same question in the future. 

While there may be official resources designated to answering this very same question that could have been read from a Google search before posting the question, it is still an effective question as many people struggle to learn from more formal or academic resources and would benefit from community explanations and discussion. This entire topic carries through to the current use of generative AI instead of Stack Overflow, as a clear and concise question that includes the context will prompt generative AI such as ChatGPT or Google's Gemini for a good response, and many users would prefer the formatting of these to official resources or websites.


## A not so good question

While with current generative AI technologies even a subpar question may result in a useable answer, on past forum sites including Stack Overflow, a bad question could lead to no usable reccomendations or even disasterous effects. Posting with a bad attitude, missing context or unclear phrasing could cause other users to feel their time was wasted and give negative responses. Even when given the benefit of the doubt, if the responders don't have a clear idea of what the question is really for, they'll be unable to answer it well. Here is an example.

[Link](https://stackoverflow.com/questions/79401639/i-am-attempting-to-use-django-ninja-for-the-first-time-and-running-into-a-strang) to a not so good question on Stack Overflow.
Here, a Stack Overflow user asked the question: 

```
Q: I am attempting to use Django Ninja for the first time and running into a strange error

With the text body:

I cant quite understand error I am receiving. I am simply trying to setup a model schema for my model. I am an old Django hand but ninja is new for me. What am I doing wrong here? Would love some help and feedback.

My model is this
[continues with multiple segments of code]
```
This question is not very effective. First, the title is not descriptive about that the actual error is, and in the description the user also didn't explain what they've tried to do to fix it so far and what they understand of the problem. Other users might see this post and either not be able to understand what the poster's problem is, or they might simply see the formatting and phrasing of it and give up while they're ahead. So far this post is only a day old, with 13 views, but not a single other user has responded or commented at all, and it is likely that they won't ever. 

Generative AI assistance instead of other people on forums is faster and is seen by some as more effective for tailored answers to specific questions. However, even with AI promps a user must ask a good question. If important context is left out for example, ChatGPT often assumes quite a bit about the situation, which may be fine if it assumes correctly or if the user can tell that the response was not accurate to their problem and that they need to prompt with a better question. But if the user is truly lost or is even simply in the learning stage, the response to a bad question could lead them astray, wasting their time and effort and ultimately being worse than not asking the question at all.
