### Homework 5 (due Monday, February 19, 2017)

In this homework assignment, you'll get some practice with arrays and then complete your visual musical instrument.

#### Arrays (due Monday)

Following up on our in-class exercises with arrays, make the following modifications to the programs below. Complete this assignment **individually**, not with your group. If you haven't yet, make sure you watch Daniel Shiffman's array tutorials:

- 7.1: [What is an Array?](https://www.youtube.com/watch?v=VIQoUghHSxU&index=23&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA)
- 7.2: [Arrays and Loops](https://www.youtube.com/watch?v=RXWO3mFuW-I&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=24)

Also make sure you look at the code we used in class; that's available in the "Week 5" section of the [main course repository](../README.md).

##### Water “drip” from a pipe.

**Assignment**: `water-arrays.js` modify the code below, adding arrays to the data model, so that there are many independent drops visible at any given time. Consider giving each drop a small, random `x` and `y` speed. What range works well for those speeds?

```javascript
var x = 230;
var y = 220;

function setup() {
  createCanvas(400, 400);
  colorMode(HSB)
}
  
function draw() {
  background(0);
  noStroke();

  // draw pipe
  rect(0, 200, x, 20);
  
  // draw drip
  ellipse(x, y, 10);
  
  // down 3 pixels each frame, but maybe should be accelerating?
  y = y + 3
  
  // if invisible for a full “height” amount…
  if (y > height*2) {
    // reset
    y = 220;
  }
}
```

##### Two ellipses changing size, with random probability.

**Assignment**: `ellipses-arrays.js` modify the code below, adding arrays to the data model, so that there are 50 different circles arrayed around the canvas. Bonus points for having that pattern be interesting in some way.

```javascript
var x1 = 100;
var y1 = 200;
var d1 = 100;

var x2 = 300;
var y2 = 200;
var d2 = 30;

function setup() {
  createCanvas(400, 400);
  colorMode(HSB)
}
  
function draw() {
  background(255);
  noStroke();

  // draw two ellipses
  fill(120, 60, 100);
  ellipse(x1, y1, d1);
  
  fill(240, 60, 100);
  ellipse(x2, y2, d2);
  
  // 1% of the time
  if (random() < 0.01) {
    // random diameter between 10 and 400
    d1 = random(10, 400);
  }
  
  // 2% of the time…
  if (random() < 0.02) {
    // random diameter between 10 and 400
    d2 = random(10, 400);
  }
}
```

##### Rotating square “smoke” from a smokestack.

**Assignment**: `smoke-arrays.js` modify the code below, adding arrays to the data model, so that there are 100 squares rotating and rising. Consider adding additional data to the model: perhaps an `xSpeed`, judiciously used, will give the smoke some volume?

```javascript
var x = 210;
var y = 290;
var r = 0;

function setup() {
  createCanvas(400, 400);
}
  
function draw() {
  background(0);
  noStroke();

  // draw smokestack
  fill(255);
  rect(195, height, 30, -100);

  // darker as it gets closer to 0
  push();
  fill(y);
  translate(x, y);
  rotate(r);
  rect(-10, -10, 20, 20);
  pop();
  
  // up 3 pixels
  y -= 3;
  
  // rotate 0.05 radians ~= 2.8 degrees per frame
  r += 0.05
  
  // if reach past the top a bunch
  if (y < -150) {
    y = 290;
  }
}
```

#### Visual musical instrument (due in class Wednesday)

Finalize your visual musical instrument, and be ready for your in-class critique net week.