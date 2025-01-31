---
layout: essay
type: essay
title: "From forum posts to AI prompts"
# All dates must be YYYY-MM-DD format!
date: 2025-01-30
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

![Stack Overflow Logo](img/stack-overflow-logo-png-transparent.png)
![OpenAI Logo](img/open-ai-logo.png)
![Google Gemini Logo](img/Google_Gemini_logo.svg)

## The lost art of posting good questions on forums

The internet has continually grown and changed ever since its conception, and it will continue to. In an earlier age than now, programmers used primarily Stack Overflow for asking the tech community questions about bugs in their code, how to work specific software, and theoretical computer science questions. Depending on a person's use of Stack Overflow, it could be incredibly helpful. When I was in high school, I used it for debugging - as a "lurker," never posting myself, but finding other people's previous questions and answers were similar to mine when googling error messages and general questions. However, for the last multiple years I have completely stopping using Stack Overflow, both because I am googling for answers less, and Google prioretizes it in results less. The reason: generative AI as a replacement. For debugging I usually just use ChatGPT, and when Googling a general programming question, instead of reccomending relevant websites and having a blurb at the top of the page taken directly from a website, this has been replaced with Google's AI results feature, which usually summarizes the possible context and answers well enough to remove any futher neccessity to look through the websites listed below it - including Stack Overflow. 

## Platforms may change, but good questions will always perservere

This all might make one think that considering what is a good question for a forum is outdated, but in actuality, good questions are good no matter the platform, and so good forum questions from the 2000's and 2010's will also make good AI prompts for the 2020's. Reccomendations for a good forum post almost completely apply to AI prompts as well. Here are some examples.

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



## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how he would, in short, create a desktop application with Facebook.

```
Q: Facebook Desktop Notifier

I am a beginner programmer that have never used anything other than what's included in a language.

I am trying to create a desktop application that notifies me anytime I get an update onfacebook. 
How should go about doing this? Thanks in advance.

edit Sorry I was not clear. Is there any way to make a DESKTOP application with facebook?
```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to Facebook’s developer website. The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we rely on others’ generosity and expertise to provide answers to our questions, it should hold that the question we ask should be one that leads to efficient and effective help that not only benefits us, but also the people we ask and others who might ask the same question in the future. Thus, if you have a question… make it a smart one! Asking questions may not always get you the best answer, but asking them in a way that will make others want to answer them will increase the success of finding a good solution and make it a positive experience on all sides.
