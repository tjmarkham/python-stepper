# python-stepper

Python Stepper Driver for Raspberry Pi + Easy Driver (or similar stepper motor driver).

Supplies a "Stepper" class with a "step" method that can be used to control a stepper motor's number of steps, speed, direction, and enable status. 

## Instantiation

To create an instance of a "Stepper," simply supply an array of the motor's step, direction, and enable pins. In the example below, the step pin is "22," the direction pin is "17," and the enable pin is "23."

```python
from Stepper import Stepper
testStepper = Stepper([22, 17, 23])
```

When the "Stepper" is instantiated, the Raspberry Pi GPIO pins are configured and the stepper "enable" pin is set to high, keeping the stepper in a lower-power mode (i.e. "off").

## Using the "Step" Method

The "step" method *requires* two arguments:
- **Steps** (the number of steps the stepper will take)
- **Direction** (the direction the stepper will move)

and has two *optional* arguments:
- **Speed** (defines the denominator in the waitTime equation: waitTime = 0.000001/speed. As "speed" is increased, the waitTime between steps is lowered)
- **StayOn** (defines whether or not stepper should stay "on" or not. If stepper will need to receive a new step command immediately, this should be set to "True." Otherwise, it should remain at "False.")

Example (3200 steps to the right):

```python
testStepper.step(3200, "right"); #steps, dir, speed, stayOn
```
