# Sensors: Touch and sound

```package
core
radio
microphone
```

```template
basic.forever(function () {
    
})
```

```blocks
basic.forever(function () {
    
})
```
## Step 0 @showDialog
Hello! Today we'll learn to make the Micro:bit react to touch and sound.  
    
## Step 1 @showDialog
### Touch and sound
The gold logo on the front of the Micro:bit can tell the Micro:bit if it's been touched, and also can tell the difference between long and short touches. To learn more about these capabilities, watch this [video](https://youtu.be/spFD3SxxxHQ).
  
A sound sensor measures sound level and can tell the difference between loud and soft sounds.

## Step 2 @showDialog
### Sound sensor
In earlier lessons, we used sensors in two different ways:
- With the accelerometer, we used blocks that start a program when the Micro:bit is in a certain position.
- With light and temperature sensors, we used round value blocks to determine the exact sensor values and display them on the screen.
      
The sound sensor uses both of these methods.
  
A block to start the program when a sound is detected:
```block
input.onSound(DetectedSound.Loud, function () {
})
```
Using a value block to display the sound level on screen:
```block
basic.showNumber(input.soundLevel())
```
## Step 3 @showHint
### Measuring sound
A ``||input.sound level||`` block returns a number between 0 and 255. The louder the sound, the higher the number.

Assemble this code and download it to the Micro:bit. We'll conduct a little experiment afterwards.
```blocks
basic.forever(function () {
    basic.showNumber(input.soundLevel())
})
```
## Step 3.5 @showDialog
### Measuring sound
Now when our Micro:bit displays the sound level, let's check what the sensor values correspond to:
- no sound
- a soft whisper
- finger snaps
- hand claps  
  
Memorize or make a note of these results. We'll need them later.

## Step 4 @showHint
### Soft and loud
Humans can discern between loud and soft sounds, but computers only understand numbers. Let's tell our Micro:bit what we humans consider to be "loud"!  
We can set thresholds for loud and soft sounds using the ``||input.set sound threshold||`` blocks. Each sound below the soft sound threshold will be considered "soft" by the program and every sound that exceeds the loud sound threshold will be considered "loud"
```hint
Use the values that we saw earlier:
A whisper is a soft sound
A clap is a loud sound
```
```blocks
input.setSoundThreshold(SoundThreshold.Quiet, 70)
input.setSoundThreshold(SoundThreshold.Loud, 200)
```
## Step 5 @showHint
### Vocal training
Assemble the code as shown. The ``||input.on loud sound||`` block executes the program when the sound level exceeds the loud sound threshold.  
 The ``||input.on soft sound||`` block executes the program when the sound level is below the soft sound threshold.  
Download your program to the Micro:bit. Now, the device will show when the sound level is too high or too low. How long can you sing a note before the device triggers?
```blocks
input.onSound(DetectedSound.Loud, function () {
    basic.showIcon(IconNames.Square)
    basic.clearScreen()
})
input.onSound(DetectedSound.Quiet, function () {
    basic.showIcon(IconNames.SmallSquare)
    basic.clearScreen()
})
input.setSoundThreshold(SoundThreshold.Quiet, 70)
input.setSoundThreshold(SoundThreshold.Loud, 200)

```

## Step 6
### Repeater
Let's check your knowledge! Create a program to respond to a sound with a sound.

## Step 7 @showHint
### Touch sensor
To use the touch sensor you'll need an ``||input.on logo pressed||`` block. This block works just the same as ``||input.on button pressed||`` blocks, but can also start different programs when the logo is released, touched or held down. Can you see it inside the ``||input.input||`` category?

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    
})
```
## Step 8 @showHint
### Morse transmitter 
In this example, the touch logo is used to make a sound that lasts until the logo is released. By alternating between short and long presses, you can encode messages with Morse code dots and dashes!
```blocks
input.onLogoEvent(TouchButtonEvent.Released, function () {
    music.stopAllSounds()
})
input.onLogoEvent(TouchButtonEvent.Touched, function () {
    music.ringTone(262)
})
```
## Step 9
### Now it's your turn!
Let's use both sensors simultaneously! Create a program that measures and displays the sound level when the logo is pressed.
## Step 10 @showDialog
### Answers: Repeater
One example of such a program:
```blocks
input.onSound(DetectedSound.Loud, function () {
    soundExpression.giggle.play()
})
input.setSoundThreshold(SoundThreshold.Loud, 200)
```

### Answers: Now it's your turn!
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(input.soundLevel())
})
```
## Step 8
You've completed all the challenges! Bravo!
