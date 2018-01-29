### Homework 2 (first part due Sunday, January 28, 2018)

This homework has two parts; first, explore p5.js by modifying some code and writing some new code from scratch. Second, share your solutions with someone else from class and ask them to to provide feedback on your work!

As a refresher, [**read through the building blocks we covered in class**](../building-blocks-code.md) and make sure it all makes sense. If you have any questions about anything, email [J.D.](mailto:jzamfirescupereira@cca.edu) or [Lei](mailto:lxiang@cca.edu)!

Like last week, publish your programs on the web, and [send me](mailto:jzamfirescupereira@cca.edu) a link. For this class, use GitHub to publish your work by [following this tutorial](http://github.com/zamfi/github-guide); make a new repository for each week's homework, and call this first one `hw2`. Then add or upload your solution to *each puzzle in its own file*, named `puzzle-1.js`, `puzzle-2.js`, *etc.*

#### Tutorials about p5.js

Learn about p5.js. Watch these videos by the wonderful and inimitable Daniel Shiffman. You may find it helpful to code along with Daniel.

- 1.3, Basics: https://www.youtube.com/watch?v=D1ELEeIs0j8
- 1.4, Color: https://www.youtube.com/watch?v=9mucjcrhFcM
- 2.1, Variables: https://www.youtube.com/watch?v=RnS0YNuLfQQ

You can run all the code for this assignment in a rudy p5.js playground; click the "p5.js playground" button at [rudy.zamfi.net](http://rudy.zamfi.net).

#### Analyzing code

Take a look at these three sketches, make sure you understand what's going on, and make the requested changes:

1.  **Lines**.

    ```javascript
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    line(random(width), random(height), random(width), random(height));
    ```

    The code above draws 10 lines, starting at a random point, and ending at a random point. But it's kind of repetitive. **Assignment**: Make a 10-step loop instead, with one instance of `line(random(width), random(height), random(width), random(height));` inside it.
    
    You may find this reminder of loop syntax helpful:

    ```javascript
    var steps = 0;
    while (steps < 8) {
      down();
      steps = steps + 1;
    }
    ```
    
2.  **More Lines**. Similar code:

    ```javascript
    function setup() {
      createCanvas(340, 340);
    }

    function draw() {
      line(random(width), random(height), random(width), random(height));
    }
    ```
    
    This code neither uses a loop nor repeats the `line` function many times -- yet it still draws many lines. Reflect on that for a moment.
    
    **Assignment**:
    
    a.  Modify the code so that the start point of every line is the center of the canvas.
    
    b.  Modify the code so that the end point of every line is in the top-right quadrant of the canvas.
    
    c.  **Challenge**: Modify the code so that the [stroke color](https://p5js.org/reference/#/p5/stroke) of each line depends on its start point's `x` coordinate, or (for extra challenge!) its length. Variables may be helpful!

3.  **Fading circles**. Start with this code that draws pastel-colored circles to the screen:

    ```javascript
    background(255);
    colorMode(HSB);
    noStroke();

    while(true) {
      background(0, 0, 255, 0.1);
      fill(random(360), 255, 255);
      ellipse(random(width), random(height), random(20, 40));
    }
    ```
    
    **Assignment**: Modify this code to limit the color to a particular range; perhaps you enjoy the warm orange/red colors of Autumn? Or the bright greens of Spring? Or the blue-tinged twinkles of sun-dappled snow in Winter? You may find it helpful to read about [HSB](https://learnui.design/blog/the-hsb-color-system-practicioners-primer.html) and learn about [`colorMode`](https://p5js.org/reference/#/p5/colorMode). 
    
    Note, in particular, that the maximum values for hue, saturation, and brightness in HSB mode are 360, 100, and 100, respectively.

    **Challenge**: Instead of drawing ellipses, use the [beginShape](https://p5js.org/reference/#/p5/beginShape) function to draw a shape that's appropriate to your choice of color. Start by running the example on the `beginShape` reference page to understand how the function works and pairs with `vertex` and `endShape`.
    
#### Writing New Code

An exercise for developing facility with writing code to achieve a particular visual end.

1.  **Modern-day Mondrian**. 

    ![Piet Mondrian](https://upload.wikimedia.org/wikipedia/commons/4/47/Piet_Mondriaan_-_03.jpg)

    Piet Mondrian was one of the pioneers of 20th century abstract art; his style is [very recognizable](https://www.google.com/search?q=mondrian&client=safari&rls=en&tbm=isch&tbas=0&source=lnt&sa=X&ved=0ahUKEwjonc6SufTYAhWN0YMKHYtoCJsQpwUIIA&biw=1362&bih=940&dpr=2#imgrc=_). Let's copy him!
    
    **Assignment**: Write code that makes an image in the style of Mondrian by drawing lines and colored rectangles.
    
    **Assignment**: Do something *different*. Pick a particular feature of Mondrian's work, and modify it in your sketch. Offer your own take on Mondrian!
    
    **Super-bonus Challenge**: Write code that draws a **random** image in the style of Mondrian. That is, write a Mondrian-painting program that creates a new image in the style of Mondrian every time it's run.


#### Sharing & Caring (due Wednesday before class)

You'll receive a link from me or Lei for someone else's homework.

- When you receive a link to evaluate, look at each program and try running it. Does it work as you expect? Is it easy to understand the code?

- If it doesn't, file a "bug report"!

  - Click the "Issues" tab at the top of the github page, and create a new issue with the bug you found. Make sure to include the puzzle number and what you think is going on, so the author can fix their code.
