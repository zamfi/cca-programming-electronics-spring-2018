### Homework 4 (due Monday, February 12, 2018)

This homework has three parts; first, extend the oscillator keyboard we looked at in class. Second, share your solutions with someone else from class and ask them to to provide feedback on your work. Third, watch two tutorials by Daniel Shiffman about objects and arrays.

#### The Visual Musical Instrument mini-project

This week and next, you'll work on creating a visual musical instrument. Some of this work will be assigned, but most will come from you. 

Your only brief for the project is: "make a visual musical instrument". Think outside the box. Don't just draw a piano and play notes from keystrokes. That's a great starting point, but the goal is to do something different. 

How can you make use of keyboard **and** mouse input? How can you use color to influence musical perception? What exactly *is* a musical instrument, anyway? 

These are the questions I want you to consider as you work on this project. Think of a few possible answers before diving in; don't just run with the first idea that comes to mind.

##### Extending the Oscillator Keyboard

First, we'll start with some programming exercises to extend the oscillator code we examined at the end of class. Here's the initial code:

```javascript
var freqA = 174;
var freqS = 196;
var freqD = 220;
var freqF = 246;

var oscA, oscS, oscD, oscF;

var playing = false;

function setup() {
  backgroundColor = color(255, 0, 255);
  textAlign(CENTER);
  
  oscA = new p5.Oscillator();
  oscA.setType('triangle');
  oscA.freq(freqA);
  oscA.amp(0);
  oscA.start();
  
  oscS = new p5.Oscillator();
  oscS.setType('triangle');
  oscS.freq(freqS);
  oscS.amp(0);
  oscS.start();
  
  oscD = new p5.Oscillator();
  oscD.setType('triangle');
  oscD.freq(freqD);
  oscD.amp(0);
  oscD.start();
  
  oscF = new p5.Oscillator();
  oscF.setType('triangle');
  oscF.freq(freqF);
  oscF.amp(0);
  oscF.start();
}

function draw() {
  if (playing) {
    background(0, 255, 255);
  } else {
    background(255, 0, 255);
  }
  text('click here,\nthen press A/S/D/F\n keys to play', width / 2, 40);
}

function keyPressed() {
  print("got key press for ", key);
  var osc;
  if (key == 'A') {
    osc = oscA;
  } else if (key == 'S') {
    osc = oscS;
  } else if (key == 'D') {
    osc = oscD;
  } else if (key == 'F') {
    osc = oscF;
  }
  if (osc) {
    osc.amp(0.5, 0.1);
    playing = true;
  }
}

function keyReleased() {
  print("got key release for ", key);
  var osc;
  if (key == 'A') {
    osc = oscA;
  } else if (key == 'S') {
    osc = oscS;
  } else if (key == 'D') {
    osc = oscD;
  } else if (key == 'F') {
    osc = oscF;
  }
  if (osc) {
    osc.amp(0, 0.5);
    playing = false;
  }
}
```

-  **Assignment**: `visual-feedback.js` Add some per-key visual feedback. One approach is to create a new variable for each key that tracks whether that particular key is pressed, and then use that variable in the `draw` function to highlight different parts of the canvas.
   
   In the current code, there's a single "playing" variable that's set to `true` when any key is pressed, and set to `false` when any key is released. Instead, try creating a `playing` variable for each key, e.g., `playingA`, `playingS`, etc. -- declare these up top with `var playingA, playingS, playingD, playingF;`. In your `keyPressed` function's `if`-`else if` sequence, when checking for each key, set the corresponding `playingA = true`, `playingS = true`, etc; then, in `keyReleased`, set the appropriate variables to `false`.
   
   Now that your four `playingA`, etc., variables are being set to `true` and `false` by `keyPressed` and `keyReleased` respectively, you can use those four variables in `if` statements inside your `draw` function to give visual feedback. Here's one example:
   
   ```javascript
   function draw() {
     background(255);
     fill(120);
     if (playingA) {
       rect(0, 0, width/4, height);
     }
   }
   ```
   
   The code above draws a gray rectangle if (and only if) the `playingA` variable has been set to `true` by the `keyPressed` function -- so it indicates whether the `A` key is pressed.
   
   One option for this assignment is to extend the above approach to all four keys. But you are welcome to give visual feedback in other ways too!

-  **Assignment**: `mouse-input.js` Incorporate mouse input into your sketch in some way. You could use it to control pitch, for example, by changing the frequency of one or more of the oscillators.

-  **Assginment**: `musical-instrument.js` Do something new, interesting, and different. Articulate what you chose in a comment at the top of this sketch.

-  **Optional Challenge**: Use the `millis` or `seconds` function to create a visual metronome to help you keep time while playing your instrument.

-  **Optional Challenge**: Implement a volume control, perhaps using keys or mouse input.

-  **Optional Challenge**: Octave shifts in music correspond to a doubling of frequency. Add an input that shifts the octave of your instrument up or down.

#### Tutorials (due before class on Wednesday)

Watch the following tutorial videos by Daniel Shiffman.
- 2.3: [JavaScript Objects](https://www.youtube.com/watch?v=-e5h4IGKZRY&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=8)
- 7.1: [What is an Array?](https://www.youtube.com/watch?v=VIQoUghHSxU&index=23&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA)
- 7.2: [Arrays and Loops](https://www.youtube.com/watch?v=RXWO3mFuW-I&list=PLRqwX-V7Uu6Zy51Q-x9tMWIv9cueOFTFA&index=24)


You should be able to answer the following questions:

1. What is an object?
2. How do you access a property of an object?
3. What is the index of the first item in an array?
4. What syntax can you use to get the third item in an array?
5. How do you use a variable nad a loop to get every item in an array?