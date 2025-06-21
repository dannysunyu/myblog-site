+++
title = 'CMU: Intro to Ml Notes'
date = 2025-04-26T11:24:57-06:00
draft = false
[params]
math = true
+++

# 第一课

Artificial Intelligence (AI): Getting Computers to Behave Intelligently

Do things that people do well (better than computers)
A moving target! But usually involves:
- Perceptron
- Control
- Planning
- Human language (recognize, understand, respond to, generate)

### Example Tasks:
- Identify objects in an image
- Translate from one huamn language to another
- Recognoize speech
- Assess risk (e.g. in loan application)
- ...

### 1st Attempt: "Knowledge-Based AI" (1960s — 1980s)
 = Write programs that simulate how people do it.
Problems: 
- Will never get better than a person
- Requires deep introspection 
- Sometimes requires experts ("expert systems", "knowledge elicitation")
- Often we don't know how we do things (e.g. ride bicycle)
  - Difference between knowing and knowing-how-we-know
- Sometimes we _think_ we know, but we're wrong

Didn't work as well as hoped.

### Alternative: "Data-Based AI" (a.k.a Machine Learning) (1980s — today)
= Write programs that learn the task from examples.

+ You don't need to know how to do it yourself
+ Performance (should) improve with more examples

But:
- Need lots of examples! (millions and billions)
- When it finally works, you may not understand how

# Lecture 2

ML: Learn a task from experience (examples)
- Get better at the task with experience

Medical Diagnosis:
f: Patient Info -> {Categories}, Classification

Predict Tomorrow's Temperature
f: (Input) -> R, Regular Regression

**ML = Learning a function.**


