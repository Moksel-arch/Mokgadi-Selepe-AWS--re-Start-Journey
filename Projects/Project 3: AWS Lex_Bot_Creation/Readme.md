# Amazon Lex Quiz Bot

##  Overview
Serverless conversational AI built with Amazon Lex V2 to deliver interactive quizzes in English (South Africa).  
Bot asks questions, validates answers, and provides feedback using custom slots and multi-intent branching.

##  Tech Stack
- **Cloud**: AWS Lex V2
- **Language**: English (ZA)
- **Skills**: Intent Design, Slot Management, Conditional Branching, Conversation Flow

##  Key Features
- Multi-question quiz flow using separate intents to overcome 4-branch limit
- Real-time feedback: Correct/Incorrect responses
- Strict slot naming and validation to prevent build failures
- No Lambda dependency - runs natively in Lex for faster response

##  Challenges & Solutions
| Challenge | Solution |
| --- | --- |
| 4-branch limit per intent | Grouped wrong answers to default path + split into multi-intent structure |
| Build failures from slot errors | Enforced strict naming standards: `UserAnswer` case-sensitive |
| Unnecessary Lambda calls | Disabled `FulfillmentCodeHook` to run directly in Lex |

##  Key Learnings
- How to design within platform constraints for stable AI experiences
- Importance of error handling and detailed logging in conversational AI
- Building scalable chatbot flows for customer self-service applications

##  Banking Relevance
Applicable to banks customer service bots, fraud awareness quizzes, and financial literacy tools.

---

# Project Name: Amazon Lex Quiz Bot

## Project Overview

This project is a chatbot built using Amazon Lex V2. We designed it to act as a quiz tool that can ask questions, understand user answers, and provide feedback based on whether those answers are right or wrong. Our main goal was to use custom slots and conditional branching to create a smooth, interactive experience.

---

## Challenges We Encountered

Building this bot wasn't always easy. We ran into several technical hurdles during the development process:

* **Branching Limits:** Amazon Lex V2 has a limit of only 4 branches per intent. This made it difficult to design a quiz with many different response paths.
* **Build Failures:** We faced many errors where the bot wouldn't build. Most of these were because we tried to reference "slots" (user inputs) that didn't actually exist in that specific part of the intent.
* **Case Sensitivity:** We realized that Lex is very picky about names. For example, using "UserAnswer" in one place and "userAnswer" in another caused the system to crash.
* **Syntax Errors:** We initially used the wrong symbols for logic, like using "==" instead of the single "=" that Lex requires for its conditional expressions.
* **Lambda Conflicts:** Our tests kept failing because a setting called "FulfillmentCodeHook" was turned on. The bot was looking for a Lambda function that we didn't actually need for this project.
* **Flow Issues:** Trying to move from Question 1 to Question 2 caused "ghost" branches and conflicts within a single intent.

---

## Our Solutions

To get the bot working correctly, we implemented the following fixes:

* **Simplified Logic:** To stay under the 4-branch limit, we grouped all incorrect answers into one "default" path instead of giving every wrong answer its own branch.
* **Naming Standards:** We picked one naming style for our slots and updated everything to match perfectly, making sure the capitalization was identical everywhere.
* **Fixed Code Syntax:** We updated all our logic to use the correct Lex Boolean syntax, such as `{UserAnswer} = "A"`.
* **Removed Lambda Dependency:** We disabled the FulfillmentCodeHook. This allowed the bot to run directly within Lex without needing external code.
* **Multi-Intent Structure:** Instead of cramming everything into one intent, we split the quiz into multiple parts (like S3Quiz and S3Quiz_Q2). This solved the branching limit and made the flow much more stable.
* **Configuration Clean-up:** We double-checked every slot type and "required" flag to make sure the bot knew exactly what to ask for and when.

---

## What We Learned as a Group

This project was a great learning experience for our team. Here are our key takeaways:

* **Error Messages are Useful:** We learned to stop guessing and start reading the Lex build error messages. They usually tell you exactly what is broken.
* **Attention to Detail:** We now understand how strict Lex is with slot references and case sensitivity. One small typo can break the entire bot.
* **Working Within Constraints:** We learned how to be creative with our design when faced with platform limits, like the branching cap.
* **Proper Project Scope:** We confirmed that you can build a powerful, working bot using only Lex configurations without always needing to add complex Lambda functions.
* **Structured Design:** We saw firsthand how much easier it is to manage a project when you break a long conversation into smaller, organized intents.

---

## Final Project Status

The bot is now fully functional and builds successfully in the English (South Africa) locale. The quiz works from start to finish:

1. The user triggers the quiz.
2. The bot asks a question and saves the answer.
3. The bot gives specific feedback based on that answer.
4. The bot moves smoothly to the next question using a second intent.

Everything is tested and ready for the final demonstration.

***
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
