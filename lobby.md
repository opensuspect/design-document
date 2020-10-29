# Lobby

The lobby is where all players gather when joining a server.


## Requirements

* Provide a space for everyone to see their fellow participants.
* Selection and preview of character customization.
* The decision for the map happens here.


## Design

The lobby shall be located inside of a moving train.
This means, the map decision will be handled in the form of selecting
a destination for the train.

Deciding a map will be by popular vote. There will be an option
however to let only the game host choose the map.

### Features

* A map/vote box or similar for choosing the map.
* Wardrobe or similar for choosing character customization/disguises.


### Starting a game

The process of starting a game will work as follows:

* The train comes to a stop inside of a train station
* All players are animated as leaving the train
* The special roles are revealed:
    * For all traitors an overlay is shown so that they are aware
      of their role and who hteir teammates are.
    * Normal players don't see any overlay. They don't know who
      the traitors are.
* Players get teleported into the map.
