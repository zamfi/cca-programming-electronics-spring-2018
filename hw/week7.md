### Homework 7 (due Tuesday, March 6, 2018)

In this homework, you'll extend some Pong code and learn about Arduino.

#### Pong

We started writing pong in class, and ended up with [this code](https://github.com/cantor10000/cca-programming-electronics-spring-2018/blob/master/class_code/pong_wednesday.js). I've made some changes to this code to simplify a few things:

```javascript
var puck = {
  x: 200,
  y: 200,
  xSpeed: 1,
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
  ellipse(puck.x, puck.y, puck.r*2);
  
  // move puck
  if (puck.y < puck.r || puck.y > height - puck.r) {
    puck.ySpeed = -puck.ySpeed;
  }
  
  puck.x += puck.xSpeed;
  puck.y += puck.ySpeed;
  
  // draw paddles
  rect(player1.x, player1.y, player1.wd, player1.ht);
  rect(player2.x-player2.wd, player2.y, player2.wd, player2.ht);
  
  // paddle movement
  if (player1.paddleDown && ! player1.paddleUp) {
    player1.y += 3;
  }
  if (player1.paddleUp && ! player1.paddleDown) {
    player1.y -= 3;
  } 

  if (player2.paddleDown && ! player2.paddleUp) {
    player2.y += 3;
  }
  if (player2.paddleUp && ! player2.paddleDown) {
    player2.y -= 3;
  }
  
  // don't let paddles outside of the play area
  player1.y = constrain(player1.y, 0, height-player1.ht-1);
  player2.y = constrain(player2.y, 0, height-player2.ht-1);
  
  // bounce puck on paddles -- player 1 -- based on x-coordinate
  if (puck.x - puck.r < player1.x + player1.wd) {
    // check if puck is within paddle height...
    if (puck.y > player1.y && puck.y < player1.y + player1.ht) {
      puck.xSpeed = abs(puck.xSpeed);
    } else {
      // ???
    }
  }
  
  // bounce puck on paddles -- player 2 -- based on x-coordinate
  if (puck.x + puck.r > player2.x - player2.wd) {
    // check if puck is within paddle height...
    if (puck.y > player2.y && puck.y < player2.y + player2.ht) {
      puck.xSpeed = -abs(puck.xSpeed);
    } else {
      // ???
    }
  }
}

// keyboard input
function keyPressed() {
  print(key);
  if (key == 'A') {
    player1.paddleDown = true;
  } else if (key == 'Q') {
    player1.paddleUp = true;
  }
  
  if (keyCode == DOWN_ARROW) {
    player2.paddleDown = true;
  } else if (keyCode == UP_ARROW) {
    player2.paddleUp = true;
  }
}

function keyReleased() {
  if (key == 'A') {
    player1.paddleDown = false;
  } else if (key == 'Q') {
    player1.paddleUp = false;
  }
  
  if (keyCode == DOWN_ARROW) {
    player2.paddleDown = false;
  } else if (keyCode == UP_ARROW) {
    player2.paddleUp = false;
  }
}
```

**Assignment**: `pong.js`: Modify the code above to add player scores! Think about what you'll need to add in the **data**, **render**, **simulate**, and **user input** categories. What new variables do you need, or what objects need new properties? How do you draw the scores on the board? How do you trigger conditions to increase the scores? (And, what happens to the gameplay when someone scores -- perhaps another round?) Hint: there is already a trigger condition in the code, questionably marked, that might be useful for you.

**Challenge**: Add sound effects for the paddle hits and wall bounces!

#### Preparing for Arduino (due before class on Wednesday)

On Wednesday, **bring a project box** to take home (and bring back to class) all your electronic components for the next few weeks. This can be a regular (closeable) cardboard box, or a special box you may find on Amazon or elsewhere.

In class, You'll receive an [AdaFruit Feather 32u4 Bluefruit LE board](https://learn.adafruit.com/adafruit-feather-32u4-bluefruit-le/setup) in class next week. Prepare your computer to use this board by following these instructions: [part 1](https://learn.adafruit.com/adafruit-feather-32u4-bluefruit-le/setup) and [part 2](https://learn.adafruit.com/adafruit-feather-32u4-bluefruit-le/using-with-arduino-ide) -- **make sure you do both parts!**

Also read these sections from Chapter 1 of the All About Circuits textbook:

1. [Electric Circuits](https://www.allaboutcircuits.com/textbook/direct-current/chpt-1/electric-circuits/)
2. [Voltage and Current](https://www.allaboutcircuits.com/textbook/direct-current/chpt-1/voltage-current/)
3. [Resistance](https://www.allaboutcircuits.com/textbook/direct-current/chpt-1/resistance/)
4. [Voltage and Current in a Practical Circuit](https://www.allaboutcircuits.com/textbook/direct-current/chpt-1/voltage-current-practical-circuit/) (Note: this is different from section 2 above!)