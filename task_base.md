# Task Base

This document details what mechanics should be available for tasks. No actual
tasks are specified here but a basic system that all tasks should fit in and
will be based on.


### Task result types

##### Normal task

Is either Completed or not completed.

##### Resulting in an item

When the task is successfully finished, it results in an item that can be
picked up by a player. The number of times the item is produced can be limited.

##### Resulting in information

Completing a task reveals information, like something that helps or enables
another task.

##### Resulting in task

Completing this task assigns a new task automatically. Similar to Among Us's
chained tasks.

##### Utility / converter type of task

The task controls a certain output based on an input and a setting. The output
might be required by other tasks to be able to performed. The output being
outside an expected range can lead to dependent tasks failing / unable to run
or instant or delayed defeat (see Maintenance tasks).

*Ex.:* a gas valve. The input is an input pressure that is slowly changing in
time with random direction changes. The setting in a task is a pressure valve
that is also set to a value by the player. The output pressure is a function of
the input pressure and the setting, and a time variable that delays the effect
of changing the valve. If the output is outside the "acceptable" range, a
dependent task can't be initiated and if initiated, it fails.

##### Maintenance task

Similar to the utility / converter task, there is / are randomly changing
inputs in time that interact with the settings fiddled in the task. When the
output moves outside the expected range, that can result in instant victory for
the impostors (i.e. reactor meltdown), emergency door lockdowns, lights turning
off, etc. There could be a "yellow" zone in the output before hitting the
failure condition to warn the players on time. 

The function of a task like this is to force the players constantly check on
this task while the impostors can screw with the settings to sabotage.

##### Win condition

Completing a task constitutes a win condition for a team, ending the game.


### Preconditions of tasks

##### Item

The task can only be started if the player starting it has a specific item on
it. By starting the task, the item is lost, and if the task is not finished /
failed, the item can't be retrieved.

##### Utility

The task requires the output of an utility type task to be in the accepted
range. If the output of that utility gets out of the range, the task fails.

##### Task dependencies

One or multiple other tasks must be completed or have an acceptable output
value for a task to be started.


### Timing of tasks

##### Timeless tasks

The tasks are available from the beginning to the end of the game.

##### Timed tasks

The task is only available based on a preconfigured time, such as a specific
round (in a round based game like the document collection) or within a set time
window.


### Task distribution

##### Shared tasks

A task is available to all players, everyone can help complete it and all
players share the same goal

##### Personal tasks

Only a specific player can do a task. To be precise, this does not exclude
multiple players getting assigned the same task at the same location.
