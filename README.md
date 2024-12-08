# Elevator Simulation
## Purpose
Elevator Simulation is a command-line simulation of a simple elevator system built in Python. It models an elevator moving between floors with realistic delays, making it a great learning tool for understanding sequential processes and state management in programming.
## Code
```
# Elevator Simulation

import random
import time


class Elevator:
    
    def __init__(self):
        print('Executing Elevator init()')
        self.MIN_FLOOR = 1
        self.MAX_FLOOR = 13
        self.CURRENT_FLOOR = self.MIN_FLOOR

    def run(self):
        while True:
            DestinationFloor = random.randint(self.MIN_FLOOR, self.MAX_FLOOR)
            if DestinationFloor != self.CURRENT_FLOOR:
                break
        self.GoToFloor(DestinationFloor)

    def GoToFloor(self, theFloor):
        print('Destination Floor = [%d]' % theFloor)
        if theFloor > self.CURRENT_FLOOR:
            print(f'Going Up  Starting Floor is [{self.CURRENT_FLOOR}]')
        else:
            print(f'Going Down  Starting Floor is [{self.CURRENT_FLOOR}]')


        time.sleep(1)
        while theFloor > self.CURRENT_FLOOR:
            self.GoUp()
        while theFloor < self.CURRENT_FLOOR:
            self.GoDown()

    def GoUp(self):
        self.CURRENT_FLOOR += 1
        print('\tGoing Up   Current Floor is [%d]' % self.CURRENT_FLOOR)
        time.sleep(.5)
        
    def GoDown(self):
        self.CURRENT_FLOOR -= 1
        print('\tGoing Down   Current Floor is [%d]' % self.CURRENT_FLOOR)
        time.sleep(.5)


def main():

    myElevator = Elevator()

    runTimes = int(input('How many times would you like to run? '))

    for i in range(runTimes):
        myElevator.run()

main()
```
