**AWS Lex Chatbot Project**

Hi, I am sharing our project from the Praesignis AWS re/Start program. 

It’s called Project 3: 

- Create Your Interactive Chatbot Using AWS Lex.
- We built a simple chatbot that can answer questions about Amazon S3 and even run a quiz on it.
- We did this to learn about AWS services and how to make AI chatbots.

What the Project Is About:

In this project we learned how to create a chatbot using AWS Lex. It’s split into two parts:
- Part 1: a basic bot
- Part 2: a quiz bot with a presentation

The bot helps users learn about AWS services like S3 through conversations.

What We Learned:

We gained these skills from the project:
- How to design and build interactive chatbots with Amazon Lex.
- Problem‑solving by making quiz flows with branching logic for different user answers.
- More about AWS services, especially Lex and its role in AI chats.
- How to explain technical stuff to non‑tech people through presentations.

Project Steps:

*Part 1: Basic Chatbot:

We followed these steps to make a simple bot:
- Logged in to AWS and went to the Management Console.
- Searched for “Lex” and opened Amazon Lex.
- Clicked Create bot.
- Named the bot (we used something relevant like “S3Bot”) and set the language to English (ZA).
- Chose None for advanced settings and selected Create.
- Added one intent: clicked Create intent and named it (e.g., “S3Info”).
- Added utterances: entered a phrase like “What is S3?” that relates to Amazon S3.
- Set a response: added something like “Amazon S3 is a cloud storage service that lets you store and retrieve any amount of data from anywhere.”
- Saved the intent, built the bot, and tested it in the test window.

*Part 2: Quiz Chatbot with Presentation (It was a little beat Challenging):

This part was harder, like a real challenge. We pretended to work for a company called Cloud Learners Inc., which wanted a quiz bot for learning about S3.

Steps we followed:
- Set up the scenario: the client wants a quiz on S3 with feedback for right and wrong answers, and it should be fun.
- Created a new intent: named it “S3Quiz”.
- Added utterances like “Start quiz,” “Quiz me on S3,” or “I’m ready for the quiz.”
- Added the first question: “What does S3 stand for?” with choices
A) Simple Storage Service
B) Secure Server Storage
C) Smart Storage System
Prompt: “Choose A, B, or C.”
- Used branching logic:
    - For correct (A) we said, “Correct! S3 stands for Simple Storage Service. Would you like the next question?”
    - For wrong answers we said, “Incorrect. The correct answer is Simple Storage Service. Would you like to try the next question?”
- Added another question: “What is Amazon S3 mainly used for?” with choices
A) Cloud storage
B) Web hosting
C) Cloud computing
Using the same logic.
- Tested the quiz in the Lex test window, trying both correct and incorrect answers to ensure the flow let users retry or move on.

*Project Requirements:

***PowerPoint Presentation:*

We made a short presentation covering:
- Introduction to Amazon Lex: what it is, its features, and how it builds chatbots.
- Client Requirements: what Cloud Learners Inc. needs – an interactive quiz for students.
- Solution Overview: how we built the bot, its structure, user interactions, feedback, and flow.
- Technical Approach: how we used intents, utterances, and branching. We mentioned challenges we faced and fixed.
- Live Demo preparation: we planned to open Amazon Lex and show the bot working.

Live Demo:
- Opened Amazon Lex and showed the bot working.
- Typed quiz utterances to start.
- Showed responses to correct and incorrect answers.
- Highlighted the smooth quiz flow.

If you have questions or want to see our bot, let us know!

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com


