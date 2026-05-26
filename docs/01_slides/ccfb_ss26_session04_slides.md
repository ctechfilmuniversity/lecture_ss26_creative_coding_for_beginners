name: inverse
layout: true
class: center, middle, inverse
---

# Creative Coding For Beginners

#### - Session 04 -

<br />
### Prof. Dr. Lena Gieseke | l.gieseke@filmuniversitaet.de  

#### Film University Babelsberg KONRAD WOLF


---
layout:false

## Session 4

* Recap by coding

--

* Homework

--

* Loops

--

* (Images)



---
### Line Drawing Algorithm

.center[<img src="./img/intro/brera_poster_b_01.png" alt="brera_poster_b_01" style="width:36%;">]

---
### Line Drawing Algorithm

.center[<img src="./img/intro/brera_poster_a_01.png" alt="brera_poster_a_01" style="width:36%;">]

---
### Line Drawing Algorithm

<iframe width="1024" height="640" src="https://editor.p5js.org/legie/full/9WDwO8l1U"></iframe>


---


## Example *Line Drawing Algorithm*


.left-even[

<iframe width="512" height="320" src="https://editor.p5js.org/legie/full/9WDwO8l1U"></iframe>

]

.right-even[

> What do we see?
]


---


## Example *Line Drawing Algorithm*


.left-even[

<iframe width="512" height="320" src="https://editor.p5js.org/legie/full/9WDwO8l1U"></iframe>

]

.right-even[

> What do we see?

* Which shapes?
* Which movement?
* Which coloring?

]

---


## Example *Line Drawing Algorithm*

--

* One line is drawn each frame

--

* With each new draw, the line’s start and end points  are moved by adding fixed values, also the color is slightly changed

--

* If the start or endpoint of a line is hitting a canvas boundary, change its direction

???
We are not animating a line directly. We are animating two points.
The line is the visible consequence of their relationship.
Once we understand that, the sketch becomes much less mysterious and much more programmable.

That is a lovely computational lesson, because many generative systems work exactly like this:
* define simple agents or values
* let them evolve
* observe the form that emerges

---


## Example *Line Drawing Algorithm*

The setup

--
* One line, defined by a start and an end point:

--
    * Each endpoint has a position in x and y

--
    * Each endpoint has a step value in x and y

--
* A color with a step value for it

---


## Example *Line Drawing Algorithm*

The animation

--

* Every frame:

--
    * Draw the line

--
    * Add the step value to the color

--
        * Constrain it to the range 0–255

--
    * Add the step values to both endpoints

--
        * If an endpoint hits a canvas edge, reverse its step direction

---
template:inverse

### *Let's Go Step by Step*


???
https://editor.p5js.org/legie/sketches/WqkHTwyZZ


---
.header[Example *Line Drawing Algorithm*]

## Steps

--

1. Setup & Draw a Line
2. Line Variables
3. Move Start and Endpoints Randomly
4. Keep in Bounds
5. Setting Color
6. Color Drift
7. Pause Key `p`


---
.header[Example *Line Drawing Algorithm* | 1. Setup & Draw a Line]

--

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  strokeWeight(2);
  background(32);
}

function draw() {
  line(100, 100, 300, 200);
}
```

---
.header[Example *Line Drawing Algorithm* | 2. Line Variables]

--

```javascript

let lineStart, lineEnd;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(255);

  // The first line
  lineStart = createVector(random(windowWidth), random(windowHeight));
  lineEnd = createVector(random(windowWidth), random(windowHeight));
}

function draw() {
  line(lineStart.x, lineStart.y, lineEnd.x, lineEnd.y);
}
```

???
* https://p5js.org/reference/p5/createVector/
* https://p5js.org/reference/p5/p5.Vector/


---
.header[Example *Line Drawing Algorithm* | 3. Move Start and Endpoints]

--

```javascript
//...
let lineStartStep, lineEndStep;
let rangeStep = 5;

function setup() {
    //...
    // Step to the next line 
   lineStartStep = createVector(random(-rangeStep, rangeStep), 
                                random(-rangeStep, rangeStep));
   lineEndStep = createVector(random(-rangeStep, rangeStep), 
                              random(-rangeStep, rangeStep));
}

function draw() {
  //...
  // Move the line a bit
  lineStart.add(lineStartStep);
  lineEnd.add(lineEndStep);
}

```


---
.header[Example *Line Drawing Algorithm* | 4. Keep in Bounds]

--

```javascript
function draw() {
//...

  if (lineStart.x < 0 || lineStart.x > width) {
    lineStartStep.x *= -1;
  }

  if (lineStart.y < 0 || lineStart.y > height) {
    lineStartStep.y *= -1;
  }

  if (lineEnd.x < 0 || lineEnd.x > width) {
    lineEndStep.x *= -1;
  }
}
```


---
.header[Example *Line Drawing Algorithm* | 5. Setting Color]

--

```javascript
let rgb;

function setup() {
  //...
  // The current color
  rgb = createVector(random(255),random(255),random(255));
}

function draw(){
  stroke(rgb.x, rgb.y, rgb.z, 80);
  //...
}
```



---
.header[Example *Line Drawing Algorithm* | 7. Color Drift]

--

```javascript
let rangeColor = 50;


function draw(){
  //...
  // Increase the color values by a random number
  rgb.add(
      createVector(
        random(-rangeColor, rangeColor),
        random(-rangeColor, rangeColor),
        random(-rangeColor, rangeColor)
      )
  );

  rgb.x = constrain(rgb.x, 0, 255);
  rgb.y = constrain(rgb.y, 0, 255);
  rgb.z = constrain(rgb.z, 0, 255);
}
```

???
```
  rgb.x += random(-rangeColor, rangeColor);
  rgb.y += random(-rangeColor, rangeColor);
  rgb.z += random(-rangeColor, rangeColor);
```


---
.header[Example *Line Drawing Algorithm* | 8. Pause Key `p`]

--

```javascript
let pause = false;

function draw() {
  
  if (pause) return;
  //...
}

function keyPressed() {
  if (key === 'p') pause = !pause;
}
```

???
https://editor.p5js.org/legie/sketches/WqkHTwyZZ


---
.header[Example *Line Drawing Algorithm*]

## Possible Adjustments

--

* Make the line thicker or thinner or adjust alpha over time.


--

* Give both endpoints the same step value so the line moves rigidly.

--

* Replace random color drift with a gradual color cycle.

--

* Add a key that changes some of the values.

--

* Have multiple lines

--

* Change the line to a Bézier curve.


---
.header[Example *Line Drawing Algorithm* |  Possible Adjustments]

## Bézier Curves

Reference: [bezier](https://p5js.org/reference/p5/bezier/)


```javascript

function setup() {
    noFill();
}

function draw() {

  bezier(
    0, 0,
    lineStart.x, lineStart.y, lineEnd.x, lineEnd.y,
    windowWidth, windowHeight
  );
}
```

???
What is a Bézier curve
* Start point → where the curve begins
* End point → where it ends
* Two control points → define how it bends

The curve does not pass through the control points but they act like "directional forces".

---
.header[Example *Line Drawing Algorithm*]

## Creative Control

> Which aspects would you want (interactive) control over?

???
Motion (endpoints as agents)
* Step magnitude (rangeStep): overall speed and turbulence.
* Step anisotropy: separate ranges for x vs y to bias motion (e.g., mostly horizontal).
* Coupling between endpoints: make end follow start (rigid-ish line) vs independent (wild geometry).
* Step evolution: keep steps constant, or slowly drift them (random walk on velocity).
* Smoothing / inertia: interpolate position toward target (adds “mass”, reduces jitter).
* Time modulation: scale speed by sin(t) or noise for breathing-like tempo.

Boundary behavior (what “bouncing” means)
* Reflect vs wrap: bounce off edges, or teleport to opposite side (toroidal space).
* Soft walls: instead of flipping instantly, gradually steer back (spring force near edges).
* Energy loss: damp the step on bounce (velocity *= 0.98) for “cooling” dynamics.
* Sticky edges: pause or slow briefly on contact for a glitchy “edge obsession.”

Color dynamics
* Color step size (rangeColor): rate of chromatic drift.
* Color model: RGB drift vs HSB/HSV drift (HSB gives more perceptual control over hue cycling).
* Palette constraints: snap to a palette or restrict hue bands (less randomness, more art direction).
* Alpha as a parameter: trail density and ghosting are mostly stroke(..., alpha).

Temporal accumulation (memory)
* Clear mode: never clear (infinite memory) vs clear every frame (no memory).
* Decay background: draw a translucent rect each frame to fade trails gradually (finite memory).
* Frame rate: lower FPS makes “steps” more legible, higher FPS makes silk.

Geometry choice
* Line vs Bézier: switch between direct connection and curvature control.
* Control-point mapping: treat endpoints as Bézier controls (as you started), or as anchors, or both.
* Stroke weight dynamics: thickness tied to speed, distance between points, or time.

Reproducibility and performance
* Seed control (randomSeed, noiseSeed): rerunnable “editions” of a run.
* Spawn/reset triggers: key press to re-roll steps/color, or periodic resets for structured chapters.

---
## Homework

#### 1. Write a sketch with the following output:

<br />
.center[![](../02_exercises/03_variables/img/square-fill-1.gif)]

???

https://editor.p5js.org/legie/sketches/xsEOyK6fK



Notes
* The colors are set randomly
* There is no increase of speed for the smaller squares - that is an optical illusion.

--

<br />

#### 2. Change the coloring up to your liking.
  
---
## Homework

#### Task 03.03 - Animation - 15 Points


---
template:inverse 

# *The End*

### Prof. Dr. Lena Gieseke | l.gieseke@filmuniversitaet.de  

#### Film University Babelsberg KONRAD WOLF

