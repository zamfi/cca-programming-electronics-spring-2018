## Building Blocks of Programs

In today's class, we explored the five building blocks of code: actions and recipes, remembering, making decisions (`if`), and repetition (`repeat if`).

A program consists of a list of actions and recipes; each action is run in sequence, but `if` and `repeat if` can modify the sequence locally.

### Actions & Recipes

Actions are the most fundamental building block: telling the Red Dot to do something.

There are six actions that the red dot can perform: `up`, `down`, `left`, `right`, `getColor`, and `setColor`.

A list of actions looks like this:
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

You can create your own action with a **Recipe**:

```
recipe downThreeTimes
| down
| down
| down
```

This recipe instructs the dot to go `down` three times. Then you can tell the dot to run the recipe the same way you run any other actions:

```
right
downThreeTimes
right
right
```

Making a recipe is a useful way to repeat a block of actions several times without rewriting it; well-created and well-named recipes can also make your program more understandable.


### Remembering

Remembering is a key part of what computers do well. When you want to remember something, tell the red dot to save it. For example:

```
down
down
save getColor as firstColorSeen
down
down
setColor remember firstColorSeen
down
```

The `save` instruction is special: above, it runs `getColor`, which inspects the red dot's current square for a color, and then remembers it for later use. The `setColor` action then `remember`s that color -- that is, it gets it back from memory -- and uses it to paint (`setColor`) the square the red dot has since moved to. 

Note: writing `remember` is optional; the second to last line above could also be written as `setColor firstColorSeen`.

### Making Decisions

`if` statements let you control the flow of your program so that it doesn't just sequentially run every action you have. The typical `if` statement might look something like this:

```
if getColor is blue
| up
else
| down
```

This program tells the red dot to check if the current color is blue, and if it is to go `up`, but if it wasn't, go `down`. You can embed `if` statements in your program; just make sure to make it clear with a `line` what's part of the if and what isn't -- you can have as many actions as you want as part of the `if`.

The `else` part is optional.

Here another example:

```
right
right
if getColor is blue
| up
if getColor is red
| down
left
left
```

And another:

```
right
right
if getColor is green
| up
| up
| up
else
| down
| down
| down
```

Can you figure out what these two examples do?

### Repetition

`repeat if` is just like `if`, except that the condition gets checked again and the associated actions get repeated if the condition is true.

For example:

```
repeat if getColor isn't red
| down
```

The program above checks if `getColor isn't red`, and if true (that the `color isn't red`), it goes `down`. Then it checks again: `getColor isn't red`. If true, goes `down` again. Then checks again, etc. When the condition is finally false (because `getColor is red`), the program continues from after the `repeat if` -- it doesn't run `down` any more times.

By combining a `repeat if` with some memory, you can keep track of the number of times something has happened, and thus easily repeat something a given number of times. For example:

```
save 0 as steps
repeat if steps < 8
| down
| save steps + 1 as steps
```

Each time through the loop, the red dot moves down **and** updates its memory by remembering that it has moved one additional step.

Convince yourself that `down` runs exactly 8 times in the code above!

Whew. That's all we did today! If you're stuck on anything, ask a fellow student or email [me](mailto:jzamfirescupereira@cca.edu) for help!
