### @activities true
### @explicitHints true

# ERPS STEM WEEK :: Motorised Buggy - Line Follower

## Introduction
### Introduction Step @unplugged
Moving our buggy ourselves is great, but what if the buggy could 'drive' itself?    
  
Well with this challenge, we can explore one one way that this could work!  
  
**Q. Why would we want a self-driving vehicle?**  
**Q. What could the dangers be of a self-driving vehicle?**
  
In this tutorial, we're going to code our micro:bit to make our buggy follw a line on the road, all by itself!

![Motorised Buggy](https://raw.githubusercontent.com/niaxotim/erps-buggy-line-follower/master/assets/buggy.png)

## Putting our buggy together!
### Assembling the pieces @unplugged
Before we start, make sure your buggy has been assembled. There are lots of sensors we *can* connect, but for now, just make
sure that the tyres are on the wheels, and that the wheels are connected to the motors.  
  
You'll also need a *line following sensor* - this goes underneath your buggy. Make sure it's the right way around!
  
Oh, and don't forget some AA batteries too!

![Buggy Key Features](https://raw.githubusercontent.com/niaxotim/erps-buggy-line-follower/master/assets/features.png)


## Using our new sensor
### Step 1
For this challenge, we're using the *line following sensor*. But how does it work? Looks closely at the sensor - there are 2 of them on the board.  

One of the sensors reads a value for the *left* of the buggy, and the other for the *right*. Each of these sensors 
gives a value on how *reflective* the surface is that it can see - a value between 0 and 1023. The more reflective, the higher the value!  


### Step 2
We need to track 3 things - the value of the *left* sensor, the value of the *right* sensor, and the *difference* between them.  
  
To do that, let's create 3 variables called 'leftSensor', 'rightSensor', and 'sensorDifference'.  
  
Then inside our ``||basic:forever||`` block, let's drag the blocks to set each variable.
  
#### ~ tutorialhint
```blocks
let leftSensor = 0
let rightSensor = 0
let sensorDifference = 0
basic.forever(function () {
    leftSensor = 0
    rightSensor = 0
    sensorDifference = 0
})

```

### Step 3
Now we need to actually set our variables to be the values that our sensors are reading.  

Drag a ``||Kitronik_Move_Motor.Left line following sensor value||`` block to replace the '0' for setting our leftSensor variable.  
  
Do the same for our 'rightSensor' variable, making sure to change the sensor value to 'Right'.  

#### ~ tutorialhint
```blocks
let sensorDifference = 0
basic.forever(function () {
    leftSensor = Kitronik_Move_Motor.readSensor(Kitronik_Move_Motor.LfSensor.Left)
    rightSensor = Kitronik_Move_Motor.readSensor(Kitronik_Move_Motor.LfSensor.Right)
    sensorDifference = 0
})
```

### Step 4
Now we need to work out the difference between our two sensors. But why are we doing this?  
  
Well, if both sensors are giving us the *same* value, then we know that both sensors are looking at the same thing.  

But if they are different, then the sensors are telling us that they aren't seing the same thing, and we should adjust where we are.  

We can work out the *difference* between our two sensors using a simple 'subtract'. But we don't care about negative numbers,
so we can use a special ``||math.absolute of||`` block. Drag one of these in to our setter for 'sensorDifference'.

#### ~ tutorialhint
```blocks
basic.forever(function () {
    leftSensor = Kitronik_Move_Motor.readSensor(Kitronik_Move_Motor.LfSensor.Left)
    rightSensor = Kitronik_Move_Motor.readSensor(Kitronik_Move_Motor.LfSensor.Right)
    sensorDifference = Math.abs(0)
})
```

### Step 5
Now let's perform our calculation. Drag a ``||math.0 - 0||`` block in to replace the '0' in our 'absolute' statement.  

Then replace the right-hand-side with the 'leftSensor' variable, and the right-hand-side with the 'rightSensor' variable.

```blocks
basic.forever(function () {
    leftSensor = Kitronik_Move_Motor.readSensor(Kitronik_Move_Motor.LfSensor.Left)
    rightSensor = Kitronik_Move_Motor.readSensor(Kitronik_Move_Motor.LfSensor.Right)
    sensorDifference = Math.abs(leftSensor - rightSensor)
})
```

### Motorised Buggy - Line Following Tutorial Complete @unplugged
Great work! You've just coded your first functions for your buggy! Now you're really motoring ;). 

![Great job](https://raw.githubusercontent.com/niaxotim/erps-buggy-basic-movement/master/assets/great_job.png)
