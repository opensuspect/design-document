# Tasks

This document specifies individual tasks that will be done by the agents
to advance their win condition in the first map. For details on how the tasks are distributed
and interact with each other, see `general_gameplay.md`. 
An overview of the general, abstract requirements of the task system can be
found in `task_base.md`.

_NOTE:_ This list is still work in progress, more tasks will be added in the future.


## Storages

Storage tasks in multiple rooms will be the main way to obtain the basic ingredients
needed for all other tasks. They generally don't consist out of more than clicking
on the right item to pick it up. 

_More items will be added in the future._

### Chemical cabinets

* Nitric Acid

### Equipment cabinets

_TBD_

### Freezer storage

* Mashed Potatoes


## Preparation

Preparation tasks are intermediate steps to prepare items obtained from storage for
other experiments.

#### Mixing

Bring two ingredients and mix them slowly by stirring until the color changes.
If you mix too fast, the temperature rises too high and the liquids boil away.

##### Input

2 specific chemicals.

##### Output

A new mixture in a test tube, dependent on the input items.
The following table contains all recipes that can be mixed together here (will change):

|Item A             |Item B             |Result             |
|-------------------|-------------------|------------------:|
|Mashed Potatoes    |Nitric Acid        |Potato essence     |


## Experiments

#### Gas chromatograph

##### Requirements

* The gas pressure maintenance task must be turned on and within the accepted range
  for the entire time between starting the heat-up and the experiment finishing.
  
* One compatible item must be inserted. If an item is not allowed for this machine, it
  cannot be inserted. The item can be taken out again unless the expirement is currently running.
  
* The machine must be started as detailed below.

##### Starting the machine

The following two actions are required to start the machine. They can be performed
in any order.

* Heat up the capillary chamber slowly and keep it up at a specified temperature range.
  There is a gas control knob and an igniter button which must be pressed after the knob is
  is set above 0 to light the flame, showing a spark and a sound effect. If the igniter 
  button is pushed while the gas knob is set to 0, the spark effect is played. 
  While the flame is lit, setting the knob to 0 immediately extinguishes the flame.
  Any other setting controls the size and heat of the flame without delay.
  The temperature of the chamber is directly controlled by the heat of the flame, but it
  only slowly approaches that value, reaching it after about 5 seconds. 
  A dial displays the chamber temperature and has markings for the accepted range which
  is between 50% and 80% of the dial range. If the gas knob is fully turned up, the dial
  will show maximum temperature (after the delay) and minimum temperature if the flame is off.
  The gas knob is set to 0 at the start of the game.

* Set the detector voltage properly.
  Another knob controls the detector voltage between 0V and 20V with discrete steps of 2V.
  The currently set voltage is displayed in a 2-digit seven-segment display.
  The voltage knob is set to 0V at the start of the game.
  The needed value must be set exactly and can be read from a table accessible in the machine
  GUI that lists all possible ingredient mixtures and their needed voltages. This table
  contains the following values (will change):

|Mixture            |Voltage|
|-------------------|------:|
|Potato essence     |6V     |



##### Running the experiment

A button starts running the experiment if all requirements are completed. If
any requirement is missing an appropriate visual clue is given to the player.
The process needs to run for 60 seconds during which all settings must remain
in an acceptable state, including the gas pressure maintenance task.  If one of
them moves out of range, the machine immediately stops the process but its
progress is saved and upon reconfiguring and restarting the machine picks up
from where it stopped (i.e. the chromatogram is already partly printed).  All
players can always interact with the controls of the machine.  The machine
keeps running if the player leaves it and the settings are also kept until
someone else changes them.

Once the process successfully finishes, the input item is consumed and a
chromatogram printed on paper is returned in the output slot.  This item
is unique for every different input item.


## Maintenance Tasks

Maintenance tasks differ from regular tasks in that they are always running
and only act as prerequisites for other tasks. They constantly emit a value
that can change over time or upon manual interaction. That value must lie within
an acceptable range for tasks that are dependent on it to work.

#### Gas valve

Controls the gas pressure. The output pressure fluctuates randomly over time
and can be manually adjusted to be in an acceptable state. There is also an
on/off switch that completely cuts the gas pressure in the off position. It
is set to "off" at the start of the game.

#### Electricity

_TBD_
