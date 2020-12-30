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

#### Reaction over a Bunsen burner (gas burner)

The reaction mixture in an Erlenmeyer flask (conical flask) is on top of an iron tripod,
with the Bunsen burner below. There is a thermometer inside the flask to measure the
solution temperature. The range of acceptable temperature is listed in a note next to the
experiment.
##### Input

* 2 specific chemicals.

* An Elrenmeyer (conical) flask

* Thermometer

##### UI

* There is a gas control knob and an igniter button which must be pressed after the knob is
  is set above 0 to light the flame, showing a spark and a sound effect. If the igniter 
  button is pushed while the gas knob is set to 0, the spark effect is played. 
  While the flame is lit, setting the knob to 0 immediately extinguishes the flame.
  Any other setting controls the size and heat of the flame without delay.

##### Suggested mechanism

This mechanism is somewhat realistic, and the introduction of heat transfer and heat loss
introduces a delay in the heating process and forces the player to be careful (or, gives
some excuse to the infiltrator why the task failed).

* The flame has an output heat that depends on the size (linear, equal steps)

* The flask has a constant heat capacity, which relates its energy to its temperature. The
  flame output directly increases the energy of the flask (continously in time).

* The solutioun has a constant heat capacity, which relates its energy to its temperature.

* The temperature of the solution is directly displayed by the thermometer.

* Heat loss of the solution: the solution loses its energy to the environment based on how much
  its temperature is over the room temperature (25 °C).

* Heat loss of the flask: the flask loses its energy to the environment based on how much
  its temperature is over the room temperature (25 °C).

* Heat transfer between the flask and the solution: depending on the temperature difference
  between the two, some ammount of energy is transfered to the solution.

## Experiments

#### Gas chromatograph

##### Requirements

* The gas pressure maintenance task must be turned on and within the accepted range
  for the entire time between starting the heat-up and the experiment finishing.
  
* One compatible item must be inserted. If an item is not allowed for this machine, it
  cannot be inserted. The item can be taken out again unless the expirement is currently running.
  
* The machine must be started as detailed below.

##### Starting the machine

The following three actions are required to start the machine. They can be performed
in any order.

* Turn on gas flow by rotating the gas valve. The gas pressure set by the maintenance task
  is displayed directly here in a gauge with the acceptable ranges overlapped

* The GC-capillary is located in a chamber with electric heating elements. A knob directly adjusts
  the heat transfered to the chamber, and the chamber loses some of its heat to the environment
  (see the *Reaction over a Bunsen burner* task for details). The temperature is displayed by
  a Nixie-tube display. The temperature has to be within a predefined range.

* Set the detector voltage properly.
  Voltage control knob controls the detector voltage between 0V and 20V relatively smoothly
  (0.2 V steps), but there are no direct markings related to voltage at the knob.
  The currently set voltage is displayed in a 3-digit Nixie-tube display.
  The voltage knob is set to 0 at the start of the game.
  The needed value must be set exactly and can be read from a table accessible in the machine
  GUI that lists all possible ingredient mixtures and their needed voltages. This table
  contains the following values (will change):

|Mixture            |Voltage|
|-------------------|------:|
|Potato essence     |6.0V   |



##### Running the experiment

If all requirements are completed, a green light lights up, if any requirement is
missing an appropriate visual clue is given to the player, as one of the four red
lights lights up: Temperature error, pressure error, voltage error or missing sample
error.

If the green light is on, the player can start the experiment by pulling down a lever that
lowers a syrenge, and when pulling up the lever, the syrenge sucks in the solution,
then rotates and injects the solution into the capillary chamber.

The process needs to run for 60 seconds during which all settings must remain
in an acceptable state, including the gas pressure maintenance task.  If one of
them moves out of range, the machine immediately stops the process but its
progress is saved and upon reconfiguring and restarting the machine picks up
from where it stopped (i.e. the chromatogram is already partly printed).  All
players can always interact with the controls of the machine.  The machine
keeps running if the player leaves it and the settings are also kept until
someone else changes them.

Once the process successfully finishes, the input item is consumed and a
chromatogram printed on paper (a long graph with peaks on it) is
returned in the output slot.  This item is unique for every different input item.


## Maintenance Tasks

Maintenance tasks differ from regular tasks in that they are always running
and only act as prerequisites for other tasks. They constantly emit a value
that can change over time or upon manual interaction. That value must lie within
an acceptable range for tasks that are dependent on it to work.

#### Gas valve

Controls the gas pressure.

* There is a main valve that completely cuts the gas pressure in the off position. It
  is set to "off" at the start of the game.

* There is a regulator valve that can be turned from low to high pressure state. It is
  at the lowest pressure setting at the start of the game.

##### Suggested mechanism

* Output pressure: numerically, the input pressure is a number, and the setting of the
  regulator valve is also a number. The output pressure is the sum of the two numbers,
  however, when displaying it to the player, both input and output pressures should be
  displayed in a logarithmic scale.

* Input pressure: the fluctuation in the input pressure is implemented using a target 
  input pressure value. Everytime the output pressure moves towards the target value,
  preferably first stars moving slowly, then the speed increases, and as it gets closer
  to the target value, it slows down again. Whenever the input pressure gets to close
  enough to the target pressure, a new, random target pressure is selected, and the
  input pressure starts to slowly move in that direction.

* Input pressure possible range: the input pressure fluctuations should be wide enough
  that no one regulator setting sould make the output pressure in the acceptable range
  for all possible input pressures.

#### Electricity

_TBD_
