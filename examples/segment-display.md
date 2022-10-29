# Segment Display <!-- omit in toc -->

<img src="https://docs.retrogadgets.game/api/modules/SegmentDisplay.png" width="200" align="right">

Welcome, in this page, you will be learning how to display numbers 0-99 in a two [seven-segment display](../docs/modules/output/SegmentDisplay.md) component
and how we can manipulate those numbers using two [buttons](../docs/modules/input/LedButton.md).

Before we start, I want you to familiarize your self with the environment first [here](./getting-started.md).

## Table of Contents <!-- omit in toc -->
- [Building your gadget](#building-your-gadget)
- [Printing symbols on your components](#printing-symbols-on-your-components)
- [Painting your gadget](#painting-your-gadget)
- [Programming your gadget](#programming-your-gadget)

## Building your gadget
First of all, go to the boards drawer and pick a shape:

<img src="../assets/examples/segment-display/boards-drawer.png" width="200">

Now go to the output drawer and scroll up until you find the displays section.  
Now pick the third one starting from above and put that anywhere on your device, make sure you have enough space for two buttons.

<img src="../assets/examples/segment-display/output-drawer.png">  
<img src="../assets/examples/segment-display/gadget-seven-segment.png" width="200">

After that, go to the input drawer, pick two buttons you like and place that anywhere on your device.  
If you are following exactly what I'm doing then make sure to reposition the [power button](../docs/modules/misc/PowerButton.md) like the one on the first image below.

<img src="../assets/examples/segment-display/gadget-opened.png" width="200">
<img src="../assets/examples/segment-display/gadget-buttons.png" width="200">

Now flip the board and go to the misc drawer, scroll up and you should find the "CPUs" section.  
Pick a CPU and place that on your gadget, this will allow us to [program](#programming-your-gadget) our gadget later.

<img src="../assets/examples/segment-display/gadget-cpu.png" width="400">

Great, now we can decorate our gadget.

## Printing symbols on your components

Note that only certain components can have symbols printed onto them such as [LED buttons](../docs/modules/input/LedButton.md) and [switches](../docs/modules/input/Switch.md).

I'm just going to print a symbol on both buttons by opening the MultiTool and selecting the two buttons we just placed.

You can also edit the description and name of your gadget.

<img src="../assets/examples/segment-display/multitool.png" width="700">

To print a symbol onto each button, first go to the symbol property below the hardware section and click on it.  
You will see a list of symbol names, scroll down and pick the one you like for each button.

<img src="../assets/examples/segment-display/multitool-symbol.png">

I will pick `DownArrow` for the first button and `UpArrow` for the second button.

<img src="../assets/examples/segment-display/multitool-symbol-list.png">

Awesome! Our buttons now have symbols, this will make it easier for people to understand which button does what.

## Painting your gadget

Did you know that we could also paint our gadget to make it look even cooler?  
Let's do that then!

On the bottom-right corner of your workstation, you will see an airbrush.  
Click on it and pick a color you want.

<img src="../assets/examples/segment-display/airbrush.png">

Note that left-clicking on a paint will change the color of your main paint while right-clicking will change the color of your secondary paint.

Left-clicking on a button will change its color while right-clicking will change the color of its symbol as shown in the image below.

<img src="../assets/examples/segment-display/gadget-buttons-painted.png" width="400">

As you can see in the image, my main color is dark gray while my secondary color is white.

I'll paint the segment display dark gray and then paint the whole gadget black.

<img src="../assets/examples/segment-display/gadget-painted.png" width="400">

Beautiful! Now we can get to the fun part!

## Programming your gadget

First of all, go to your MultiTool and click on the "Assets" button.

<img src="../assets/examples/segment-display/multitool-button-assets.png" width="400">

Now double-click on the `CPU0.lua` file and you should see this:

<img src="../assets/examples/segment-display/multitool-code-editor.png" width="400">

Let's define a few component variables first.  
This will help us identify which component we are working with.

```lua
-- components
local segmentDisplay:SegmentDisplay = gdt.SegmentDisplay0
local upBtn:LedButton = gdt.LedButton0
local downBtn:LedButton = gdt.LedButton1
```

Now let's define a table called `segments` that we'll use as reference to display our `num` variable to the [segment display](../docs/modules/output/SegmentDisplay.md).

```lua
-- variables
local segments = {
    -- each value in this table represents the LED to turn on for that specific index
    -- in this segments table we don't need the period so we only put upto a maximum of 7
    [0] = {1,2,3,4,5,6},
    [1] = {2,3},
    [2] = {1,2,4,5,7},
    [3] = {1,2,3,4,7},
    [4] = {2,3,6,7},
    [5] = {1,3,4,6,7},
    [6] = {1,3,4,5,6,7},
    [7] = {1,2,3},
    [8] = {1,2,3,4,5,6,7},
    [9] = {1,2,3,4,6,7}
}

local num:number = 0
```

Awesome! Now let's write a few functions that'll help us display the numbers on the segment display.  

```lua
-- functions

-- display is the component we want to access
-- digit is the digit we want to access the segments of
-- value is the number we want to display
function displayDigit(display:SegmentDisplay, digit:number, value:number)
    -- let's make sure to turn off every LED first
    for segment=1, 8 do
        display.States[digit][segment] = false
    end
    
    -- now let's go through each table in the segments table
    -- and turn the required LEDs on
    for segment=1, #segments[value] do
        display.States[digit][segments[value][segment]] = true
    end
end

-- display is the component we want to access
-- value is the number we want to display
function convertNumber(display:SegmentDisplay, value:number)
    local digit1:number = math.floor(value / 10) % 10
    local digit2:number = value % 10
    displayDigit(display, 1, digit1)
    displayDigit(display, 2, digit2)
end
```

Alright, now let's create a function called `listenInputs`, this will check the states of our buttons and act accordingly.
We'll also clamp `num` and check if it is less than zero because we can't display negative values.

```lua
function listenInputs()
    num = math.max(num, 0) % 100

    if upBtn.ButtonDown then
        num += 1
    end

    if downBtn.ButtonDown then
        num -= 1
    end

    if num < 0 then
        num = 99
    end
    convertNumber(segmentDisplay, num)
end
```

Now we'll also check if we're holding down the buttons so we don't have to continuously press each of them.

First, go to the variables section where you defined `segments` and `num`, and create two new variables called `upHoldT` and `downHoldT`, these will keep track of how long we've been holding a button.

You also have to define `holdTime`, this will determine how long we have to hold before `num` starts changing, you can edit this however you like.

```lua
-- variables
local segments = {
    -- each value in this table represents the LED to turn on for that specific index
    -- in this segments table we don't need the period so we only put upto a maximum of 7
    [0] = {1,2,3,4,5,6},
    [1] = {2,3},
    [2] = {1,2,4,5,7},
    [3] = {1,2,3,4,7},
    [4] = {2,3,6,7},
    [5] = {1,3,4,6,7},
    [6] = {1,3,4,5,6,7},
    [7] = {1,2,3},
    [8] = {1,2,3,4,5,6,7},
    [9] = {1,2,3,4,6,7}
}

local num:number = 0

local upHoldT:number = 0
local downHoldT:number = 0
local holdTime:number = 3
```

Then go back to `listenInputs` and do as following:

```lua
function listenInputs()
    num = math.max(num, 0) % 100

    if upBtn.ButtonDown then
        num += 1
    end

    if downBtn.ButtonDown then
        num -= 1
    end

    if upBtn.ButtonState then
        upHoldT += 0.1
    else
        upHoldT = 0
    end

    if downBtn.ButtonState then
        downHoldT += 0.1
    else
        downHoldT = 0
    end

    if upHoldT >= holdTime then
        num += 1
    end

    if downHoldT >= holdTime then
        num -= 1
    end

    if num < 0 then
        num = 99
    end
    convertNumber(segmentDisplay, num)
end
```

Finally, call `listenInputs` in the `update` function so that it gets called every time tick.

```lua
-- update function is called every time tick
function update()
    listenInputs()
end
```

Congratulations! 🏆🥳 We now have a working counter gadget, and you've learned how to use the segment display!