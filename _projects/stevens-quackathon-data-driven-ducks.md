---
title: "Stevens IT Quackathon: Data-Driven Ducks"
excerpt: "A Spring 2025 Stevens IT Quackathon team project building an Azure-based AI academic and career guidance assistant."
---

## One-line Summary

A team-built Azure AI prototype that combines student intake data, curriculum RAG, and a fine-tuned GPT-3.5 Turbo model to generate personalized course recommendations, academic planning guidance, and career-path suggestions.

## Context

The Stevens Institute of Technology CIO Advisory Committee and Division of Information Technology hosted the IT Quackathon during the Spring 2025 semester. The event combined hackathon-style problem solving with an innovation expo, with teams working on Stevens-centered problems using Microsoft AI technology.

Data-Driven Ducks was listed as one of the Quackathon teams.

## Problem

Students often make course, academic-planning, and career decisions using fragmented information sources: course catalogs, course descriptions, syllabi, degree requirements, personal interests, academic goals, and professional goals. The project explored how an AI assistant could collect structured student inputs and turn them into more personalized academic and career guidance.

## System Overview

The team developed an Azure-based academic and career guidance prototype organized around an end-to-end data and AI workflow:

- Collected student profile data through Microsoft online forms, including interests, academic goals, career goals, and related planning preferences
- Stored and managed user-submitted data and generated artifacts in Azure Blob Storage
- Built a retrieval-augmented generation workflow over Stevens course-related materials, including course schedules, course descriptions, and syllabus content
- Used GPT to generate structured JSON datasets from curriculum and advising-related materials
- Fine-tuned a GPT-3.5 Turbo model on structured academic-planning and recommendation data
- Combined RAG outputs and the fine-tuned model to produce course recommendations, academic route suggestions, and career-path guidance
- Connected the intake, storage, processing, model, and response-generation stages through Azure pipeline-style workflows

## My Contribution

- Participated as a member of the Data-Driven Ducks team
- Helped shape the project into a student-facing academic and career guidance system rather than a generic chatbot
- Contributed to the AI workflow design, including how student intake data could be connected with curriculum context and recommendation logic
- Supported the use of RAG and fine-tuning to make the assistant more grounded in Stevens course information and student planning goals
- Helped frame the system pipeline from user data collection to final personalized guidance output

## Technical Stack

`Azure` `Azure Blob Storage` `Azure Pipelines` `Microsoft Forms` `OpenAI` `GPT-3.5 Turbo Fine-tuning` `RAG` `JSON Dataset Generation` `NLP` `Recommendation Systems` `Academic Planning` `Career Guidance`

## Team

Data-Driven Ducks: Olajide Yusuf, Yogarajan Sivakumar, Nicholas Ofoe, Longzhao Gong, Shrishgovind Revankar.

## Results / Current Status

The project was presented as a Stevens IT Quackathon team prototype for AI-assisted academic and career planning. This portfolio page records the system design and prototype direction; it should be read as an event prototype rather than a production Stevens platform.

## Links

- [Stevens IT Quackathon](https://www.stevens.edu/it/quackathon)
- [Projects Overview](/projects/)
