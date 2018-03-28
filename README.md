# CCA Programming & Electronics, Spring 2018

This course repository contains homework assignments, useful guides, and code for "Programming & Electronics" at CCA, Spring 2018.

Also included in this repository is the official [course syllabus](syllabus.pdf).

### Week 1: Wednesday, January 17, 2018

Lecture:
- Introductions
- What is programming?
- Goals & course details

Hands-on activities:
- Human Embodiment of Programmer & Robot
  - Programs generally run line-by-line.
  - Repetition, decision making, and recipes break that up.
- [Solving Puzzles](puzzle-sheets.pdf)

#### Building Blocks of Code

In class, we discussed the four basic building blocks of code: actions & recipes, remembering, making decisions, and repetition. 

[Here are some notes.](building-blocks-programs.md)

#### Inspiration

Finally, here are some inspirational videos to get you excited for our class if you're not already:
- Creative Code
  - [Interviews with Practitioners](http://www.youtube.com/watch?v=eBV14-3LT-g)
  - [Casey Reas](https://www.youtube.com/watch?v=_8DMEHxOLQE)
- Basic robots
  - [Coffee-can robot](http://www.youtube.com/watch?v=b0mIshBIbvI#t=24)
  - [Tree-climbing robot](http://www.youtube.com/watch?v=zkpH1BjD6Wc)
  - [Self-balancing robot](http://www.youtube.com/watch?v=Tw9Jr-SPL0Y)
  - [Insect robot](http://www.youtube.com/watch?v=tOsNXg2vAd4#t=120)
  - [Treadbot](http://www.youtube.com/watch?v=YblSltHDbIU)
  - [Velociraptor robot](http://www.youtube.com/watch?v=lPEg83vF_Tw)
- Installations
  - [The Bay Lights](http://thebaylights.org/)
  - [Murmur Wall](http://www.future-cities-lab.net/projects/#/murmurwall/)
  - [Floating Couch](http://vimeo.com/72826106)
  - [Wooden Segment Mirror](https://www.youtube.com/watch?v=BZysu9QcceM#t=36)
  - [Generative design](https://www.youtube.com/watch?v=pNkz8wEJljc)
- Art & Music bots
  - [Textile weaving](https://vimeo.com/71044541)
  - [ReacTable](https://www.youtube.com/user/marcosalonso)
  - [Projection mapping](https://www.youtube.com/watch?v=czuhNcNU6qU)
  - [Laser harp](http://www.youtube.com/watch?v=sLVXmsbVwUs#t=20)
  - [Cubli: Floating Cube](https://www.youtube.com/watch?v=n_6p-1J551Y)
  - [Arc-o-matic](http://vimeo.com/57082262#at=130)
  - [Robo Faber](http://vimeo.com/78771257)
  - [Eggbot](https://www.youtube.com/watch?v=w4cdbV2oaEc)
- Drink-makers
  - [Textspresso](http://www.youtube.com/watch?v=kx9D74t7GD8#t=89)
  - [The Inebriator](http://www.youtube.com/watch?v=WqY7fchs7H0)
- Computer Numerical Control (CNC)
  - [Shapoko / tinyg](http://www.youtube.com/watch?v=pCC1GXnYfFI#t=11)
  - [Makerbot Replicator](http://www.youtube.com/watch?v=NAbiAzYhTOQ)
- Vacuuming
  - [Roomba](https://www.youtube.com/watch?v=0DNkbZvVYvc)

[Homework for Week 1](hw/week1.md)


### Week 2: Wednesday, January 24, 2018

In-class:
- Homework review.
- Translating "pseudo-code" into real code with [Rudy](http://rudy.zamfi.net); here are some notes on the [building blocks of code](building-blocks-code.md).

Workshop:

1. Work through the Rudy puzzles with a partner. Make sure you understand the syntax.

2.  **Challenges**: On puzzle 9, the open canvas:
    1.  Draw four rectangles of various sizes on the canvas.
    2.  Draw 10 parallel vertical lines, 20 squares long, 3 squares apart.
    3.  Define a function, `rect`, that takes four parameters: `x`, `y`, `width`, and `height`, and draws a rectangle on the canvas, at location (`x`,`y`) with the corresponding `width` and `height`.
    4.  Modify the `rect` function so that it takes a fifth parameter, a color to draw the outline with.
    4.  Modify the `rect` function so that it fills in the rectangle instead of just drawing the outline.
    5.  **Extra Challenge**: Define a `line` function, that takes four parameters: `x1`, `y1`, `x2`, and `y2`, and draws a line between the point defined by (`x1`,`y1`) and the point defined by (`x2`,`y2`). There are many ways to approach this challenge! You may find some Internet research instructive.
    6.  **Extra Challenge**: Define a `circle` function that takes three parameters: `x`, `y`, and `r`, and draws a circle of radius `r` centered on the point defined by (`x`,`y`). You find trigonometry helpful for this exercise.

[Homework for Week 2](hw/week2.md)

### Week 3: Wednesday, January 31, 2018

In-class:
- Homework Review.
- Understanding statement evaluation.

Workshop:

#### Class Quilt

Make a patch for the class quilt! Start with the following code:

```javascript
function yourPatch(x, y) {
  noFill();
  stroke(238);
  rect(x, y, 100, 100);
  
  // your code here!
}

background(255);
yourPatch(0, 0); // draw patch at upper-left

background(255);
yourPatch(width-100, height-100); // draw patch at lower-right
```

Modify the `yourPatch` function, replacing `// your code here!` with drawing commands that draw inside the 100-by-100 pixel square. Use `x` and `y` to get yourself started -- all your shapes should appear within the rectangle bounded to the left by `x`, above by `y`, to the right by `x+100` and below by `y+100`. That means that you'll need `x` and `y` (or other variables you create that *depend on* `x` and `y`) in every parameter to every painting function you use.

We'll then take all our functions and pattern them together into a class quilt! Making your functions depend on `x` and `y` means that we can place them anywhere in the quilt by "passing in" the appropriate `x` and `y` coordinates for that place in the quilt.

When you like what you have, change the call your `yourPatch` to draw your patch at `(0, 0)` and `(100, 100)` -- make sure your drawing moves along with the coorinates.

Feel free (but not compelled) to remove the border rectangle when you like what you have!

Here's an example that I came up with for myself:

```javascript
function zamfiPatch(x, y) {
  noFill();
  stroke(238);
  rect(x, y, 100, 100);
  
  // blocky J
  fill(238);
  noStroke();
  rect(x+20, y+20, 60, 20);
  rect(x+40, y+40, 20, 40);
  rect(x+20, y+60, 40, 20);
  
  // overlay of lines
  stroke(0);
  var lines = 3;
  while (lines < 50) {
    line(x+lines, y, x, y+lines);
    lines = lines + 5;
  }
  stroke(200);
  while (lines < 100) {
    line(x+lines, y, x, y+lines);
    lines = lines + 3;
  }
  stroke(255, 127, 0);
  lines = 0;
  while (lines < 50) {
    line(x+100, y+lines, x+lines, y+100);
    lines = lines + 4;
  }
  stroke(0, 64, 127);
  while (lines < 100) {
    line(x+100, y+lines, x+lines, y+100);
    lines = lines + 4;
  }
}
```

You don't have to understand exactly how the code above works -- but do notice that **every single coordinate** parameter of every shape and line has `x` or `y` in it -- usually something added to `x` or `y` -- and that's so that every shape is drawn **relative to `(x, y)`**. That way, whether I run `jdPatch(0,0)` or `jdPatch(100, 100)`, all my shapes are offset by the correct amount.

**Challenge**: Make an animated patch! Draw something slightly different every time your function is called. You can accomplish this using the `random` function, or by keeping variables outside your function, using them to position or color shapes, and then updating them each time your patch function is called. NB: use variables names that are unique to you: preface them with a nickname, for example!

#### Working with Loops

Here's one way of working with loops, and figuring out how to turn a pattern into code:

1. Write down the coordinates of the shapes you want to create in your loop.
2. Find the pattern for those coordinates
  a. Where does it start?
  b. Where does it end?
  c. How much does it change each time?
3. Use that pattern in a *for* loop: `for (var i = START; i < END; i = i + CHANGE) { ... }`
  
For example, to create the following sketch:

![triangle of lines](img/triangle.png)

...start by writing down some endpoints for those lines:

```
(20, 20) -> (20, 20)
(20, 30) -> (30, 20)
(20, 40) -> (40, 20)
(20, 50) -> (50, 20)
(20, 60) -> (60, 20)
(20, 70) -> (70, 20)
(20, 80) -> (80, 20)
.
.
.
(20, 480) -> (480, 20)
```

...from these coordinates, we can find a pattern for each of the four parameters we need to draw a line:

- `startX`: always 20
- `startY`: starts at 20, ends at 480, goes up by 10 each time
- `endX`: starts at 20, ends at 480, goes up by 10 each time
- `endY`: always 20

...from this pattern, we can generate a loop that draws these lines, by creating a variable that starts at `20`, ends at `480`, and goes up by `10` each time. We won't call the variable `x` or `y` beacuse we don't use it exclusively for either coordinate.

```javascript
for (var i = 20; i <= 480; i = i + 10) {
  var startX = 20;
  var startY = i;
  var endX = i;
  var endY = 20;
  line(startX, startY, endX, endY);
}
```


#### Loops Workshop

Today, we'll practice loops:

1.  Together, we'll make vertical lines:
    
    ![vertical lines](img/vertical-lines.png)

2.  Then, with a partner, you'll make horizontal lines:
    
    ![horizontal lines](img/horizontal-lines.png)
    
3.  Try these concentric circles too:
    
    ![concentric circles](img/concentric-circles.png)

4.  And this cone:

    ![cone of lines](img/cone-of-lines.png)
    
5.  Also this diamond:

    ![diamond](img/diamond.png)
    
6.  What about these taller lines?
    
    ![doubles](img/doubles.png)
    
7.  **Challenge**: For this you'll need a **loop within a loop**:
    
    ![artdeco](img/artdeco.png)

8.  **Challenge**: Now try this grid of circles; you'll need **nested loops** for this one too!
    
    ![circle grid](img/circle-grid.png)

9.  **Extra Challenge:** Using a technique called the "exponential moving average", we can create a smooth easing animation like this:
    
    ![easing position](img/easing-position.gif)
    
    The technique works by one variable to store intermediate values for another variable. For example, in the sketch above, the *x-* and *y-* coordinates of the circle are stored in variables `x` and `y`, which are **eased** to the target values given by `mouseX` and `mouseY`.
    
    "Exponential moving average" is a fancy way of saying: first, pick a fixed **rate** at which the easing occurs for a variable reaching its target. That rate controls how much impact the target has on the value each frame. For exampe, if the rate is 10%, then the new value each frame is 10% the target value and 90% the old value of the variable. Here's some sample code; the key is in the line `x = target*rate + x*(1-rate);`:
    
    ```javascript    
    var rate = 0.1;
    var x = 0;
    var target = 100;
    
    while (true) {
      ellipse(x, 100, 15, 15);
      x = target*rate + x*(1-rate); // rate is 0.1, or 10% -- (1-rate) is 0.9, or 90%
    }
    ```
    
    Each frame, x gets 10% closer to its target.
    
    Modify this code to create a circle that follows the mouse as in the anigif above.

[Homework for Week 3](hw/week3.md)


### Week 4: Wednesday, February 7, 2018

In-class:
- Homework Review
  - State machines, briefly: you are keeping state based on user inputs, and drawing based on that state. Input -> computation -> output.
- Programming for Interaction

#### Class Quilt!

Here's what we have so far -- if you haven't sent me your quilt patch yet, please do so ASAP!

![class quilt](img/class-quilt.png)

Thanks to all who submitted!

#### Programming for Interaction

So far we've been focusing on the "output" part of programming. Today we'll work with the "input" part.

p5 enables a few different ways of getting user input. In the homework we used keyPressed to handle color changes, but there is a full list of input functions in the [p5.js reference](https://p5js.org/reference/)

For today's workshop, we'll consider a few sketches. First, let's extend one of the exercises from homework. Starting with this code from the homework:

```javascript
function setup() {
  createCanvas(400, 400);
  background(255);
  colorMode(HSB);
  noStroke();
}

var diameter = 10;

function draw() {
  if (mouseIsPressed) {
    ellipse(mouseX, mouseY, diameter);
  }
}

function keyPressed() {
  print(key);
  if (key == 'R') {
    fill(0, 100, 100);
  } else if (key == 'G') {
    fill(100, 70, 100);
  } else if (key == 'B') {
    fill(210, 100, 100);
  } else if (key == 'T') {
    fill(180, 100, 100);
  } else if (key == 'Y') {
    fill(60, 100, 100);
  } else if (key == 'P') {
    fill(310, 100, 100);
  }

  if (key == 1) {
    diameter = 10;
  } else if (key == 2) {
    diameter = 20;
  } else if (key == 3) {
    diameter = 30;
  }

  if (key == 'E') {
    diameter = 30;
    fill(0, 0, 100);
  }
}
```

**Exercise:** Can we modify this code so that the painting only happens while the corresponding key is pressed?

Next, consider this sketch: https://alpha.editor.p5js.org/jd/sketches/SkyDECDIz

Let's add a few more sounds, and extend this sketch:

**Exercise:** Add three more sounds to the assets folder, and play different sounds based on different keypresses.

**Exercise:** Use `mousePressed` to change something about the sounds or how they are played.

Now, consider this sketch: http://alpha.editor.p5js.org/jd/sketches/S1n5FmOLz

**Exercise:** Add some per-key visual feedback. In the current code, there's a single "playing" variable that tracks whether any key is playing. Change this "state" so that there's a state per key!

**Exercise:** Do something fun or interesting with this sketch.

[Homework for Week 4](hw/week4.md)

### Week 5: Wednesday, February 14, 2018

Today's topic is data modeling & simulations. These are super powerful concepts! Turns out a lot of what you actually do with a computer involves some data that models something, and which you “simulate”.

In p5.js, this manifests itself as the data-draw synergy. Think of stop-motion animation. You have some state of the world, some clay you’ve placed, and you take a photo. Then you move the clay, and you take another photo. Move the clay, take another photo.

Variables are the “clay”. The draw() function is the camera taking the photo. In draw(), after you “take the picture” by drawing all your stuff based on your “clay”, you can move around your clay by changing your variables.

Here’s an introductory example:

```javascript
var x = 45;
var y = 50;

function setup() {
  createCanvas(400, 400);
}
  
function draw() {
  background(0);
  noStroke();

  // draw ellipse
  ellipse(x, y, 10);
  
  // move right 3 pixels
  x = x + 3;
  
  // move down 1 pixel
  y = y + 1;
}
```

**Exercise:** make it rebound at the edges. There's a trick! We'll need to keep track of direction also.

What’s the “data model”? We're draing to a canvas, and the data is `x` and `y` coordinates. What’s the `draw`? `ellipse` function. What’s the “simulation”? How does it change each step?

**Group Exercise:** create your own “data model” / “stop-motion animation” with this concept. 

Ask yourselves these questions:
- What data do you need?
- What “simulation” do you need? What changes each frame? And how does it change?
- How do you draw it?

Here are some more examples:

##### Water “drip” from a pipe.

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


#### Arrays

Arrays are lists of regular variables, but that you can access using another variable. That means: you can use loops to access them! Basically infinite variables! They let you **duplicate** “clay”.

Basic example, extending the circles:

```javascript
var x0 = 45;
var y0 = 50;

var x1 = 55;
var y1 = 65;

var x2 = 50;
var y2 = 80;

function setup() {
  createCanvas(400, 400);
}
  
function draw() {
  background(0);
  noStroke();

  ellipse(x0, y0, 10);  
  x0 = x0 + 3;
  y0 = y0 + 1;

  ellipse(x1, y1, 10);
  x1 = x1 + 3;
  y1 = y1 + 1;

  ellipse(x2, y2, 10);  
  x2 = x2 + 3;
  y2 = y2 + 1;
}
```

Let’s say we want 100 circles. Well, that’s super annoying! Here the code above with arrays:

```javascript
var x = [];
var y = [];

x[0] = 45;
y[0] = 50;

x[1] = 55;
y[1] = 65;

x[2] = 50;
y[2] = 80

function setup() {
  createCanvas(400, 400);
}
  
function draw() {
  background(0);
  noStroke();

  ellipse(x[0], y[0], 10);  
  x[0] = x[0] + 3;
  y[0] = y[0] + 1;

  ellipse(x[1], y[1], 10);
  x[1] = x[1] + 3;
  y[1] = y[1] + 1;

  ellipse(x[2], y[2], 10);  
  x[2] = x[2] + 3;
  y[2] = y[2] + 1;
}
```

What’s the big deal? Well, the deal is that you can use another variable in place of the [#]:

```javascript
var x = [];
var y = [];

x[0] = 45;
y[0] = 50;

x[1] = 55;
y[1] = 65;

x[2] = 50;
y[2] = 80

function setup() {
  createCanvas(400, 400);
}
  
function draw() {
  background(0);
  noStroke();

  for (var index = 0; index < 3; index = index + 1) {
    ellipse(x[index], y[index], 10);
    x[index] = x[index] + 3;
    y[index] = y[index] + 1;
  }
}
```

That `for` loop "iterates over" every `index` from `0` to `2` of the array. For each of `0`, `1`, and `2`, the loop draws the ellipse at the `x` and `y` coordinate for that index.

And we can do something similar for the creation of the initial data, the initial “clay”:

```javascript
var x = [45, 55, 50];
var y = [50, 65, 80];

// etc.
```

…or…

```javascript
var x = [];
var y = [];

function setup() {
  createCanvas(400, 400);
  for (var index = 0; index < 100; index = index + 1) {
    x[index] = random(10, width-10);
    y[index] = random(10, height-10);
  }
}

function draw() {
  background(0);
  noStroke();

  for (var index = 0; index < 100; index = index + 1) {
    ellipse(x[index], y[index], 10);
    x[index] = x[index] + 3;
    y[index] = y[index] + 1;
  }
}
```

To actually bounce these circles, we once again need to add to our model: a speed in the `x` and `y` directions for each circle. Two new arrays should suffice! (This code also uses a third new array for color.)

```javascript
var x = [];
var y = [];
var xSpeed = [];
var ySpeed = [];
var colors = [];

function setup() {
  createCanvas(400, 400);

  for (var index = 0; index < 100; index = index + 1) {
    x[index] = width / 2;
    y[index] = height / 2;
    xSpeed[index] = random(-5, 5);
    ySpeed[index] = random(-5, 5);
    colors[index] = color(random(255), random(255), random(255))
  }
}

function draw() {
  background(0);
  noStroke();

  for (var index = 0; index < 100; index = index + 1) {
    fill(colors[index]);
    ellipse(x[index], y[index], 10);
    x[index] = x[index] + xSpeed[index];
    y[index] = y[index] + ySpeed[index];

    if (x[index] > width - 5) {
      xSpeed[index] = -xSpeed[index];
    }

    if (y[index] > height - 5) {
      ySpeed[index] = -ySpeed[index];
    }

    if (x[index] < 5) {
      xSpeed[index] = -xSpeed[index];
    }

    if (y[index] < 5) {
      ySpeed[index] = -ySpeed[index];
    }
  }
}
```

**Exercise**: Modify the water drip or square smoke sketches to add additional "drops" or "smoke". Try without an array first. Then use an array to add 20 or more. (Note: Drops may be easier than smoke!)

#### Objects

Finally, to bounce these circles, we need the extra "direction" data. We could just add two more arrays: one for `xSpeed` and another for `ySpeed`. Or, we can bundle together all the properties of each circle — the `x`, `y`, `xSpeed`, and `ySpeed`, into a single object. (Noe that this code uses `xd` in place of `xSpeed`, `yd` in place of `ySpeed`, and merges the four boundary conditions into two!)

```javascript
var circles = [];

function setup() {
  createCanvas(400, 400);
  colorMode(HSB);

  for (var index = 0; index < 100; index = index + 1) {
    // new "circle" object, with x, y, xd and yd properties:
    circles[index] = {
      x: width / 2,
      y: height / 2,
      xd: random(-2, 2),
      yd: random(-2, 2),
      c: color(random(360), 60, 100)
    }
  }
}

function draw() {
  background(0);
  noStroke();

  for (var index = 0; index < 100; index = index + 1) {
    // get circle object
    var circle = circles[index];

    // draw it
    fill(circle.c);
    ellipse(circle.x, circle.y, 10);

    // move it according to direction
    circle.x = circle.x + circle.xd;
    circle.y = circle.y + circle.yd;

    // check boundaries and update directions
    if (circle.x > width || circle.x < 0) {
      circle.xd = -circle.xd;
    }
    if (circle.y > height || circle.y < 0) {
      circle.yd = -circle.yd;
    }
  }
}
```

Note what "event" triggers the bouncing. What if we do [something else](https://alpha.editor.p5js.org/jd/sketches/H1StgvZwG) in that `if` too?

**Exercise**: Incorporate arrays or objects into your visual musical instrument.

Here's the code we wrote together in class while working on this topic: [`circles-array.js`](https://gist.github.com/zamfi/6d0cf997c2585c6639e4517941af90a7) and [`circles-objects.js`](https://gist.github.com/zamfi/0698d29ad7ea0e1d53babfcc79bce672).

[Homework for Week 5](hw/week5.md)

### Week 6: Wednesday, February 21, 2018

In class:
- Critique & playtest of your visual musical instrument.

[Homework for Week 6](hw/week6.md)

### Week 7: Wednesday, February 28, 2018

Today, Krystof led a discussion of how to write a program from scratch. Here are my notes on a similar session that may be useful for you.

#### From Idea to Code

Designing and implementing from scratch, using the data/render/simulate/user input breakdown, a sketch of moderate complexity.

In class, we started building Pong together. We began by decomposing the game into components, and listing each component under the heading of Data Model, Rendering, Simulation, and User Input:

|     Data Model     |     Rendering       |     Simulation     |      User Input       |
|--------------------|---------------------|--------------------|-----------------------|
| puck: `x`, `y`, `xSpeed`, `ySpeed` | puck | move puck, bounce puck |                  |
| paddles: `x`, `y`  | paddles             | move paddles       |       arrow keys      |
| scores: `player1`, `player2` | scores    | check for scoring  |                       |
| defined playspace  | midline             |                    |                       |

Then we started writing code, picking off the easiest / lowest hanging fruit from our chart above. Good practice is to prioritize the smallest possible thing that you can still show works: in our case, we started by modeling and rendering the puck. Then, simulating the puck. Then, modeling and rendering the paddles. Etc.

We ended up with this code:

```javascript
var puck = {
  x: 200,
  y: 200,
  xSpeed: 3,
  ySpeed: -1,
  r: 15
};
var edgeOffset = 20;

var player1 = {
  x: edgeOffset,
  y: 200,
  ht: 50,
  wd: 10
};

var player2 = {
  x: 400-edgeOffset,
  y: 200,
  ht: 50,
  wd: 10
};


function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(255);
  
  // draw puck
  ellipse(puck.x, puck.y, puck.r);
  
  // bounce puck off top/bottom edges
  if (puck.y < 0 || puck.y > height) {
    puck.ySpeed = -puck.ySpeed;
  }
  
  // move puck
  puck.x += puck.xSpeed;
  puck.y += puck.ySpeed;
  
  // draw paddles
  rect(player1.x, player1.y, player1.wd, player1.ht);
  rect(player2.x, player2.y, player2.wd, player2.ht);
  
}

function keyPressed() {
  // move paddles
  if (key == 'Q') {
    player1.y -= 3;
  }
  
  if (key == 'A') {
    player1.y += 3;
  }
}
```

In the homework, you'll extend this code to add scoring!

[Homework for Week 7](hw/week7.md)

### Week 10: Wednesday, March 28, 2018

#### Quiz Review

Make sure you get a review of the quiz before next week!

#### Servomotors!

With the DC motors, we used "fake analog" via PWM to modulate the speed of the motor. But PWM can also be used as an interpreted signal, rather than to fake a voltage. 

Servomotors, a special kind of motor that designed for easy angular positioning, have a microcontroller inside them that read a PWM signal and convert that into a desired rotation.

Using one of your two servos, **add** this circuit to your breadboard:

![Servo signal on pin 5, using 6V battery pack for power](img/servo-circuit.png)

Then, create a new sketch with this code, and upload it using Arduino:

```c
/* Sweep
 by BARRAGAN <http://barraganstudio.com>
 This example code is in the public domain.

 modified 8 Nov 2013
 by Scott Fitzgerald
 http://www.arduino.cc/en/Tutorial/Sweep
*/

#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position

void setup() {
  myservo.attach(5);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  for (pos = 45; pos <= 135; pos += 1) { // goes from 45 degrees to 135 degrees
    // in steps of 1 degree
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
  for (pos = 135; pos >= 45; pos -= 1) { // goes from 135 degrees to 45 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
}
```

Notice that the code above only uses the angle range of 45-135°. Not all servos have the same range, and this is a good starting point. Experiment with your servo and see if you can increase the range in the code. **Watch out for your servo exceeding one end of its range and getting hot** -- if this happens, unplug your servo from the 6V power supply, shrink your range, and try again. If your servo stays pegged for too long, it may burn out!

The code above just "sweeps" your servo, but usually you'll want some kind of control. Consider this code instead:

```c
/*
 Controlling a servo position using a potentiometer (variable resistor)
 by Michal Rinott <http://people.interaction-ivrea.it/m.rinott>

 modified on 8 Nov 2013
 by Scott Fitzgerald
 http://www.arduino.cc/en/Tutorial/Knob
*/

#include <Servo.h>

Servo myservo;  // create servo object to control a servo

int potpin = 0;  // analog pin used to connect the potentiometer
int val;    // variable to read the value from the analog pin

void setup() {
  myservo.attach(5);  // attaches the servo on pin 9 to the servo object
  Serial.begin(9600)
}

void loop() {
  val = analogRead(potpin);            // reads the value of the potentiometer (value between 0 and 1023)
  val = map(val, 0, 1023, 45, 135);    // scale it to use it with the servo (value between 0 and 180)
  myservo.write(val);                  // sets the servo position according to the scaled value
  Serial.print("Angle: "); Serial.println(val);
  delay(15);                           // waits for the servo to get there
}
```

This code uses your potentiometer as an input angle; what happens when you rotate your potentimeter? Change the angle endpoints 
to match what you discovered your true endpoints to be in the previous exercise.

**Exercise**: Attach your second servo to a new pin, and make it rotate in the opposite direction from your first servo.

**Challenge**: Build a [mechanism](https://teachmetomake.files.wordpress.com/2010/02/machinations-mechanisms.pdf) powered by your two servos using found materials.