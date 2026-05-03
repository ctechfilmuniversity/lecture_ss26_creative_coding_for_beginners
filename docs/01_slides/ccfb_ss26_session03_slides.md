name: inverse
layout: true
class: center, middle, inverse
---

# Creative Coding For Beginners

#### - Session 03 -

<br />
### Prof. Dr. Lena Gieseke | l.gieseke@filmuniversitaet.de  

#### Film University Babelsberg KONRAD WOLF


---
layout:false

## Session 3

* Recap Session 2
* Exercise

--

* Variables


--
* Follow-Along Coding Examples

---
.header[Follow-Along Coding Examples]

.center[
<iframe width="1000" height="600" src="https://editor.p5js.org/legie/full/pA5Ddli51"></iframe>
]

---
.header[Follow-Along Coding Examples]

.center[
<iframe width="1000" height="600" src="https://editor.p5js.org/legie/full/9WDwO8l1U"></iframe>
]


---


## Recap Session 3




---
## Recap Session 3

`{ }`

--

* Define blocks of code
    * Help you to understand the flow of a program
    * Indent code inside of the blocks!

---
## Recap Session 3

Working with functions consists of two parts: 

--

1. The definition of that function (title line with `{}`)
2. Calling that function to execute it

--
  
```js
function functionname() {
    // Code that is executed when we call the function
}
```  
```js

functionname(); // Calling the function
```


--

One of the steps might be done by p5.


---
## Recap Session 3

There are two color system: RGB (default) and HSB:

--
  

* Set HSB by calling `colorMode(HSB);`
* You can set custom ranges for each channel  
    `colorMode(HSB, 1000, 100, 100);`



---
## Recap Session 3

We can structure the program flow with user input:

--


* `mousePressed()`
* `mouseX`, `mouseY`
* `keyPressed()`
* `key`


---
## Recap Session 3
  
We can structure the program flow with with a conditional statement:

--
  
* `if(condition is true){  }`

--

<br />
To create conditions, we use operators

--
* Comparison
    * `>`, `>=`, `<`, `<=`, `==`, `!=`

--
```js
if ((mouseX > 50) {
    //...
}
```

???
https://editor.p5js.org/legie/sketches/7WsRFWTNH


---
.header[Conditionals]

##  The if-else Statement

--


```js
if(condition 1 is true){

    // do something

} else if(condition 2 is true){

    // do something else

} else {

    // do a third thing for all other cases
}
```

???
  

* https://editor.p5js.org/legie/sketches/HDWQbzDU8



---
.header[Conditionals | The else-if ladder]


.center[<img src="./img/flow/ch02_03.png" alt="ch02_03" style="width:74%;">]
.imgref[[[quora]]([https://www.quora.com/Can-if-else-be-considered-as-a-loop])]



???

* Understand and explain [this code](https://editor.p5js.org/legie/sketches/0lByVe-mH).
* https://editor.p5js.org/legie/sketches/0lByVe-mH


---
.header[Conditionals]


## Chaining Operators

With `&` you can chain conditions together:

```js
// Pseudo Code

if(condition1 is true & condition2 is true & condition2 is true) {
    // We get here
}
```

--

Only if all conditions are true the if-code is entered!


---
.header[Conditionals]


## Chaining Operators

With `|` you can chain conditions together:

```js
// Pseudo Code

if(condition1 is true | condition2 is false) {
    // We get here
}
```

--

Only one of all conditions needs to be true to enter the if-code!

---
## Exercise

* [Task 02.03 - Errors](https://editor.p5js.org/legie/sketches/2wzE7ba4V)

--

* Task 02.01 - Inspiration
* Task 02.04 - Interaction & Conditionals


---
## Example

* Example [Color Lines](https://editor.p5js.org/legie/full/EIsuZr5gBI)




???




* Full Screen (variable): 
* No variable: https://editor.p5js.org/legie/sketches/mGfAGEncY



```
function setup() {
    createCanvas(300, 300);

    // We set the value ranges to run from
    // H:0..300 (same as the width of the canvas)
    // S & B:0..100
    colorMode(HSB, 300, 100, 100);
    background(100);
    //strokeWeight(8);
}

// Without mouse input (see below)
// nothing is happening
function draw() {}


//function mouseDragged() {
function mousePressed() {
  
    strokeWeight(random(2,18));
  
    // Set the color of the line
    // to the hue that is on the 
    // hue color spectrum from 0..300
    // at the x position of the mouse
    stroke(mouseX, 100, 100);
  
    // Draw a line from the top edge of
    // the canvas (y = 0) to the bottom
    // edge of the canvas (y = 300)
    // at the x position of the mouse
    line(mouseX, 0, mouseX, 300);
}
```

```
function mouseDragged() {
  
  if(keyIsPressed & key == 'c'){
    stroke(0,0,100);
  } else {
    stroke(mouseX, 100, 100);
  }
  
  
  strokeWeight(random(1,10));
  line(mouseX, 0, mouseX, 400);
}
```


---
template:inverse 

# *The End*

### Prof. Dr. Lena Gieseke | l.gieseke@filmuniversitaet.de  

#### Film University Babelsberg KONRAD WOLF

