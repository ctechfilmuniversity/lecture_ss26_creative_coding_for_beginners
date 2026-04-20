---
layout: default
title: Exercise 02
parent: Exercises
nav_order: 2
---


# Creative Coding For Beginners
  
Prof. Dr. Lena Gieseke \| l.gieseke@filmuniversitaet.de  
  

# Exercise 02 - Program Flow & Interaction - 20 Points

This session is due on **Tuesday, May 5th** before class.  


## Task 02.01 - Inspiration - 5 Points
  
Find a publicly available p5 example, e.g., from [OpenProcessing](https://openprocessing.org/discover/#/trending), that you like. Briefly describe why you like it.  
  
*Submission*: Add in your OwnCloud file a link to the sketch and your reasoning for your choice.
  

## Task 02.02 - Scripts

Recap the slides:

* [Chapter 04 - Flow & Interaction](../01_slides/ccfb_ss26_04_flow_slides.html)
* [Chapter 05 - Conditionals](../01_slides/ccfb_ss26_05_conditionals_slides.html)
* [Chapter 06 - Variables](../01_slides/ccfb_ss26_06_variables_slides.html) (only if we covered this topic in class)


*Submission*: -



## Task 02.03 - Errors - 5 Points

[This code](https://editor.p5js.org/legie/sketches/2wzE7ba4V) has three errors. Can you find and fix them? Make sure to read the error messages, they might (or might not) help you find the issues.

Briefly explain what the code does.


```js
function setup() {createCanvas(400, 400);colorMode(HSB);noStroke();
  // Properties for the
  // text() command
  // https://p5js.org/reference/p5/text/
  // https://p5js.org/reference/p5/textAlign/
  textAlign(CENTER, CENTER);textSize(36);}

function draw() // hour() returns the current hour

  // from 0..23
  // https://p5js.org/reference/p5/hour/
  if( hour() < 5 ) {
    
    // Night
    background(240, 100, 40);fill(50, 40, 100);text('⭐️ Good Night! ⭐️', 200, 200);} else if (hour() < 12) { // Morning
    background(200, 20, 100);fill(42, 100, 100);text('☀️ Good Morning! ☀️, 200, 200);} else if (hour() < 16) {
    
    //Midday
    background(210, 60, 100);    
    
    fill(42, 60, 100);text('🌼 Good Afternoon! 🌼', 200, 200);} else {
    
    //Evening
    background(210, 100, 80);    
    fill(100);
    text('🍿 Good Evening! 🛋️', 200);
  }}
```

*Submission*: Add in your OwnCloud file a link to your sketch and a brief explanation about what the code does.


## Task 02.04 - Interaction & Conditionals - 10 Points

Create a sketch up to your liking and that uses **interaction** and **conditionals**.

  

*Submission*: Add a link to your sketch in your OwnCloud file.

---

*Happy Flowing!*

