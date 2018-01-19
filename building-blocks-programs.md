## Building Blocks of Programs

In today's class, we explored the five building blocks of code: **actions** and **recipes** (aka **functions**, aka **commands**), remembering (aka **variables**), making decisions (aka **`if`**), and repetition (aka **`while`**, a repeated `if`). We moved a red dot around a grid; turns out, that red dot is named **Rudy**.

A program consists of a list of commands; each command is run in sequence, but `if` and `while` can modify that sequence locally.

### Functions, aka Actions & Recipes

Functions are the most fundamental building block: telling the Red Dot to do something.

There are six functions that Rudy can perform: `up`, `down`, `left`, `right`, `getColor`, and `setColor`.

A list of function "calls" (i.e., telling Rudy to execute functions) looks like this:
```
down
down
down
right
right
right
up
right
right
```

You can create your own action with a "function definition", aka a **recipe**. A recipe is just a recipe: it tells Rudy *how* to do something, but doesn't tell Rudy *to* do it -- until you actually *run* the function.

```
function downThreeTimes {
  down
  down
  down
}
```

This `downThreeTimes` function instructs Rudy to go `down` three times. Then you can tell Rudy to run the recipe the same way you run any other function:

```
right
downThreeTimes
right
right
```

When Rudy gets to the `downThreeTimes` function, it'll look up the function definition -- the *how* to `downThreeTimes` -- and start running that code. So the code above is equivalent to:

```
right
down
down
down
right
right
```

Making your own function is a useful way to repeat a block of code several times without rewriting it; well-created and well-named function can also make your program spectacularly more understandable.


### Variables & Remembering

Remembering is a key part of what computers do well. When you want to remember something, tell Rudy to assign it to a variable. For example:

```
down
down
var firstColorSeen = getColor
down
down
setColor(firstColorSeen)
down
```

The `var` instruction is special: it allocates (aka *reserves*) memory for some data. But what data? Whatever comes after the `=` assignment operator. 

In the snippet of code above, Rudy runs `getColor`, which inspects Rudy's current square for a color, and then saves it for later use in a variable called `firstColorSeen`. In memory, there's a little table like this:


| Name            | Data          |
| --------------- | ------------- |
| firstColorSeen  | "blue"        |


 The `setColor` action then recalls that color -- that is, it gets it back from memory -- and uses it to paint (`setColor`) the square Rudy has since moved to. You can tell the `setColor` function what specific color to paint either directly (e.g., "blue" or "red") or indirectly via a variable as above.

### Making Decisions With `if` Statements

`if` statements let you control the flow of your program so that it doesn't just sequentially run every action you have. The typical `if` statement might look something like this:

```
if (getColor == "blue") {
  up
} else {
  down
}
```

This program tells Rudy to check if the color of the square Rudy is currently on is blue, and if it is, Rudy should go `up`, but if it isn't, Rudy should go `down`. Make sure to use curly braces `{}` to indicate what's part of the if and what isn't -- you can have as many functions as you want as part of the `if`!

The `else` part is entirely optional.

Here another example:

```
right
right
if (getColor == "blue") {
  up
}
if (getColor == "red") {
  down
}
left
left
```

And another:

```
right
right
if (getColor == "green") {
  up
  up
  up
} else {
  down
  down
  down
}
```

Can you figure out what these two examples do?

### Repetition With `while` Loops

`while` is just like `if`, except that the condition gets checked again, and the associated actions get repeated again, if the condition is true again.

For example:

```
while (getColor != "red") {
  down
}
```

The program above:

1. Checks if `getColor` isn't `"red"`, and
2. If true (that the color isn't red), it goes `down`. 
3. Checks again: `getColor` isn't `"red"`. 
4. If true, goes `down` again. 
5. Then checks again, etc. 
6. When it checks the condition and finds that it is finally false (because `getColor` **IS** `red"`), the program is done -- it continues from after the `while` and doesn't run `down` any more times.

By combining a `while` with some memory, you can keep track of the number of times something has happened, and thus repeat something a given number of times. For example:

```
var steps = 0
while (steps < 8) {
  down
  steps = steps + 1
}
```

Each time through the loop, Rudy moves down **and** updates its memory by remembering that it has moved one additional step.

Convince yourself that `down` runs exactly 8 times in the code above!

Whew. That's all we did today! If you're stuck on anything, ask a fellow student or email [me](mailto:jzamfirescupereira@cca.edu) for help!
