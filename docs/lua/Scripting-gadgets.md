<!-- 
TODO:
- [ ] Add a section on how to make the led blink
- [ ] Go in-depth with a couple of component examples
-->

# Scripting your first gadget
> Please note that this is not a Lua tutorial.  
> You can view the [Lua Manual](http://www.lua.org/pil/contents.html) here, or check out the basics on [Learn X in Y minutes, Where X=Lua](https://learnxinyminutes.com/docs/lua/).

Creating a gadget may seem like a daunting task at first, so let's build something simple... a gadget that flashes a light on and off!

## Your first gadget
Let's start by taking a large square board from the boards drawer and placing it on the gadget mat.

After you're done, pull the cover off of your gadget by holding on this handle and pulling it up:  
<img src="./../../.github/screenshots/board-cover.png" width="135">

Now, let's flip the board over by clicking on the arrow icon near the gadget handle. Open the drawer labelled "Misc", and find a small CPU chip, then place it on the back-side of the board. Flip it back over.  
<img src="./../../.github/screenshots/board-cpuchip.png" height="180">

Now, let's add a light. Open the drawer labelled "Output", find a LED light, and place it anywhere on the board.

You can now put the cover back by dragging it back down onto the board.

## Programming your gadget
Now that you've built your gadget, it's time to program it!
Let's start by opening MultiTool: drag the handle to the right.

You will most likely see your gadget in the following way:
<img src="./../../.github/screenshots/gadget-multitool.png" width="300">

Let's open the CPU's Lua script by clicking on "Assets", then double-clicking on "CPU0.lua".

You will see the following:
```lua
-- Retro Gadgets

-- update function is repeated every time tick
function update()

end
```

Let's make that LED light up, shall we?  
You can see and access your gadget's components by typing in `gdt.`. From there, select your LED component.  
If you selected a single LED, you will see the `State` property, if you didn't, go back and select a single one.  
You can set the `State` property to true in order to light it up:
```lua
-- Retro Gadgets
gdt.Led0.State = true

-- update function is repeated every time tick
function update()

end
```

Turn on your gadget by clicking on the power button, and you should see the LED light up!