# Rhythm

## Step 1

Place an 'on shake' input block. Attach a 'while' loop block.

```blocks
input.onGesture(Gesture.Shake, () => {
    while (true) {

    }
})
```

## Step 2

We're going to make a variable called 'game' to allow the @boardname@ to check if the loop should continue. Go to the Variables tab, click Make a Variable, and type 'game'.

## Step 3

Place a block in between the input and loop blocks. This block should be the 'set item to 0'block. Set the variable to 'game' and change the number to '1'. Go to the Logic tab and attach a '0 = 0' block. Attach a 'game' variable block to the left side. Change the number on the right side to '1'.

```blocks
let game = 0input.onGesture(Gesture.Shake, () => {    game = 1    while (game == 1) {            }}) 

let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
    	
    }
})
```

## Step 4

We're going to create another variable. Name this one 'random'. Place an 'set item to 0' block in the while loop, change the variable to 'random' and add a block from the Math tab. This should be the 'pick random 0 to 4' block. Attach it to the 'set item to 0' block and change 4 to 1.

```block
let random = 0
let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
        random = Math.random(2)
    }
})
```

## Step 5

Add an 'if, then, else' block from the Logic tab below the 'set random to pick random 0 to 1' set of blocks. Add a '0 = 0' block to the 'if' condition. Place the 'random' variable block on the left side. Add a 'show leds' block in the 'then' section. Draw an 'A'. Add another 'show leds' block in the 'else' section and draw a 'B'.

```block
let random = 0
let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
        }
    }
})
```

## Step 6

Add a 'pause (ms)' block from the Basic tab below each 'show leds' block. Set the number to 500. Place an 'if, then, else' block under each 'pause (ms)' block. Add an 'and' block to the 'if' condition of each block.

```blocks
let random = 0
let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(500)
            if (false && false) {
            	
            } else {
            	
            }
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(500)
            if (false && false) {
            	
            } else {
            	
            }
        }
    }
})

```

## Step 7

Add a 'not' block from the Logic tab to the right space of each 'and' block. Place a 'button A is pressed' blocks in each space. On the block on top, change the right block to 'B' and on the lower block, change the left block to 'B'.

```blocks
let random = 0
let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
            	
            } else {
            	
            }
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
            	
            } else {
            	
            }
        }
    }
})
```

## Step 8

Create another variable named 'score'. Place a 'change item by 1' block from the Variables tab into the 'then' condition of each 'if, then, else' block. Change the variable to 'score'.

```blocks
let score = 0
let random = 0
let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
                score += 1
            } else {
            	
            }
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
                score += 1
            } else {
            	
            }
        }
    }
})
```

## Step 9

Place a 'show icon' block from the Basic tab in each 'else' condition. Change the icon to the cross. Attach a 'set item to 0' block under each of the 'show icon' blocks and change 'item' to 'game'. The purpose of this is to let the @boardname@ know that the game is over and stop the 'while' loop.

```blocks
let item = 0
let score = 0
let random = 0
let game = 0
input.onGesture(Gesture.Shake, () => {
    game = 1
    while (game == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game = 0
            }
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game = 0
            }
        }
    }
})
```

## Step 10

Add a 'show number' block from the Basic tab below the 'while' loop. Place a 'score' variable block in the number space. Place a 'set item to 0' block and change 'item' to 'score'.

```blocks
let score = 0
let random = 0
let game2 = 0
input.onGesture(Gesture.Shake, () => {
    game2 = 1
    while (game2 == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(500)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        }
    }
    basic.showNumber(0)
})
```

## How it should work

You have finished coding! When downloaded to your @boardname@, you can shake it to begin the game. Hold down the A button when you see 'A' come up. Hold it down until you see it change to B. Start holding the B button until it changes to the A button again. This will repeat until you don't hold the correct button or hold the wrong button. An 'X' will come up, signalling that the game is over. Your score is shown at the end.

## Challenges!

1. How can you make the required input switch faster?
2. How can you use the features of the @boardname@ to create more inputs?
3. How can you modify the code such that the radio functions can be used to play with a friend?

Solution to challenge 1:

```blocks
let score = 0
let random = 0
let game2 = 0
input.onGesture(Gesture.Shake, () => {
    game2 = 1
    while (game2 == 1) {
        random = Math.random(2)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(300)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(300)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        }
    }
    basic.showNumber(0)
})
```

Notice how the 'pause (ms)' blocks have had their inputs changed from 500 to 300.

Solution to challenge 2:

```blocks
let score = 0
let random = 0
let game2 = 0
input.onGesture(Gesture.Shake, () => {
    game2 = 1
    while (game2 == 1) {
        random = Math.random(4)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(300)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else if (random == 1) {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(300)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else if (random == 2) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
                `)
            if (input.acceleration(Dimension.X) < -200) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else {
            basic.showLeds(`
                . . # . .
                . . . # .
                # # # # #
                . . . # .
                . . # . .
                `)
            if (input.acceleration(Dimension.X) > 200) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        }
    }
    basic.showNumber(0)
})
```

Notice that the accelerometer of the @boardname@ has been utilized. When you see a left arrow, you would tilt the @boardname@ left and when you see a right arrow, you would tilt it right.

Solution to challenge 3:

```blocks
let score = 0
let random = 0
let game2 = 0
let win = 0
radio.onDataPacketReceived( ({ receivedNumber: win }) =>  {
    if (win == 1) {
        game2 = 0
        basic.showIcon(IconNames.Yes)
        basic.showNumber(score)
        score = 0
    }
})
input.onGesture(Gesture.Shake, () => {
    game2 = 1
    while (game2 == 1) {
        random = Math.random(4)
        if (random == 0) {
            basic.showLeds(`
                . . # . .
                . # . # .
                # # # # #
                # . . . #
                # . . . #
                `)
            basic.pause(300)
            if (input.buttonIsPressed(Button.A) && !(input.buttonIsPressed(Button.B))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else if (random == 1) {
            basic.showLeds(`
                # # # # .
                # . . . #
                # # # # .
                # . . . #
                # # # # .
                `)
            basic.pause(300)
            if (input.buttonIsPressed(Button.B) && !(input.buttonIsPressed(Button.A))) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else if (random == 2) {
            basic.showLeds(`
                . . # . .
                . # . . .
                # # # # #
                . # . . .
                . . # . .
                `)
            if (input.acceleration(Dimension.X) < -200) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        } else {
            basic.showLeds(`
                . . # . .
                . . . # .
                # # # # #
                . . . # .
                . . # . .
                `)
            if (input.acceleration(Dimension.X) > 200) {
                score += 1
            } else {
                basic.showIcon(IconNames.No)
                game2 = 0
            }
        }
    }
    win = 1
    radio.sendNumber(win)
    basic.showNumber(0)
})
radio.setGroup(1)
```

Notice the addition of two sets of blocks. This solution works as long as you and your friend shake the @boardname@ at the same time to start the game at the same time. To learn how the radio blocks work, go to Reference > Radio.
