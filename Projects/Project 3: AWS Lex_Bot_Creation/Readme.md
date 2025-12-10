AWS Lex Chatbot Project

Hi, I am sharing my project from the Praesignis AWS re/Start program.

It’s called Project 3: Create Your Interactive Chatbot Using AWS Lex.

I built a simple chatbot that can answer questions about Amazon S3 and even run a quiz on it. I did this to learn about AWS services and how to make AI chatbots.

What the Project Is About

In this project I learned how to create a chatbot using AWS Lex. It’s split into two parts:

- Part 1: a basic bot
- Part 2: a quiz bot with a presentation

The bot helps users learn about AWS services like S3 through conversations.

What I Learned

I gained these skills from the project:

- How to design and build interactive chatbots with Amazon Lex
- Problem-solving by making quiz flows with branching logic for different user answers
- More about AWS services, especially Lex and its role in AI chats
- How to explain technical stuff to people who aren’t tech experts through presentations

Project Steps

Part 1: Basic Chatbot

I followed these steps to make a simple bot:

- Log in to AWS and go to the Management Console
- Search for "Lex" and open Amazon Lex
- Click "Create bot"
- Name the bot (I used something relevant like "S3Bot") and set the language to English (ZA)
- Choose "None" for advanced settings and select "Create"
- Add one intent: Click "Create intent" and name it (like "S3Info")
- Add utterances: Enter one phrase like "What is S3?" that relates to Amazon S3
- Set a response: Add something like "Amazon S3 is a cloud storage service that lets you store and retrieve any amount of data from anywhere"
- Save the intent, build the bot, and test it in the test window

Part 2: Quiz Chatbot with Presentation (Challenge)

This part was harder, like a real challenge. I pretended to work for a company called Cloud Learners Inc. They wanted a quiz bot for learning about S3.

Steps I followed:

- Set up the scenario: The client wants a quiz on S3 with feedback for right and wrong answers, and it should be fun
- Create a new intent: Name it "S3Quiz"
- Add utterances like "Start quiz", "Quiz me on S3", or "I'm ready for the quiz"
- Add the first question: Response like "What does S3 stand for?" with choices A) Simple Storage Service, B) Secure Server Storage, C) Smart Storage System. Prompt: "Choose A, B, or C"
- Use branching logic: For correct (A), say "Correct! S3 stands for Simple Storage Service. Would you like the next question?" For wrong, say "Incorrect. The correct answer is Simple Storage Service. Would you like to try the next question?"
- Add another question: "What is Amazon S3 mainly used for?" with choices A) Cloud storage, B) Web hosting, C) Cloud computing. Use the same logic
- Test the quiz: In the Lex test window, try utterances, correct and incorrect answers, and make sure the flow lets users retry or move on

Project Requirements

PowerPoint Presentation

I made a short presentation covering:

- Introduction to Amazon Lex: What it is, its features, and how it builds chatbots
- Client Requirements: What Cloud Learners Inc. needs, like an interactive quiz for students
- Solution Overview: How I built the bot, its structure, user interactions, feedback, and flow
- Technical Approach: How I used intents, utterances, and branching. I mentioned challenges I faced and fixed

Live Demo

- Open Amazon Lex and show the bot working
- Type quiz utterances to start
- Show responses to correct and incorrect answers
- Highlight the smooth quiz flow

If you have questions or want to see my bot, feel free to reach out!
