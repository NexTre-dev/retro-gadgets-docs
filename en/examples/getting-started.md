# Introduction to your Retro Desk
Retro Gadgets takes place in, well... on a Retro Desk!  
The Retro Desk has **2 modes**: MultiTool Mode and Building Mode.

## Building Mode
<p align="center">
	<img src="../assets/examples/getting-started/building-mode.png" width="1000px">
</p>

## Interactable Objects

| Object Name          | Description                                                                                                                       |
| :------------------- | :-------------------------------------------------------------------------------------------------------------------------------- |
| 1. Your Gadget       | Your gadget is the main attraction of your desk. It's what you have to be building, testing and playing around with in this game. |
| 2. Mat               | This is your building area, feel free to fiddle around with your gadget here!                                                     |
| 3. Boards Drawer     | Here you can find all the boards (basic shapes) that you can use to build your gadget.                                            |
| 4. Component Drawers | Here you can find 3 drawers, each containing different types of components.                                                       |
| 5. Soldering Iron    | You can use the soldering iron to solder your gadget's boards together.                                                           |
| 6. Airbrush          | Feeling a bit creative, perhaps fancy? (🍷) You can use the airbrush to paint your gadget however you want.                        |
| 7. Tweezers          | You can use the tweezers to place or reposition stickers on your gadget.                                                          |
| 8. MultiTool Handle  | Your primary tool, which is used to program functionality into your device. We'll get into this later!                            |
| 9. Gadget Archive    | You can put your finished gadgets here. Didn't finish it? No problem! Work on something else and return to it later.              |
| 10. Lamp             | This is your lamp, you can drag it to the middle, to the left, and turn it on and off.                                            |
| 11. Sticker Trash    | Drag your sticker here and it'll be deleted.                                                                                      |

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
<img src="../assets/examples/getting-started/board-cover.png" width="135">

Now, let's flip the board over by clicking on the arrow icon near the gadget handle. Open the drawer labelled "Misc", and find a small CPU chip, then place it on the back-side of the board. Flip it back over.  
<img src="../assets/examples/getting-started/board-cpuchip.png" height="180">

Now, let's add a light. Open the drawer labelled "Output", find a LED light, and place it anywhere on the board.

You can now put the cover back by dragging it back down onto the board.

## Programming your gadget
Now that you've built your gadget, it's time to program it!
Let's start by opening MultiTool: drag the handle to the right.

You will most likely see your gadget in the following way:  
<img src="../assets/examples/getting-started/gadget-multitool.png" width="300">

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