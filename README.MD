# Programming the Farming Drone(Report)

## Introduction

In a nutshell, The Farmer Was Replaced is a simulation game based on programming, developed and published by Timon Herzog. This is a very unusual game that merges farming with coding; players will have to automate a farm using a drone that can be customized. Players will instruct their drone to execute all the basic agricultural tasks, like planting crops, watering, fertilizing, and harvesting, by writing scripts in some simplified language, similar to Python.

The ultimate objective of the game is to carry out the farming operations in an efficient manner. While going through it, the players get advanced technologies and challenges that gradually get more and more complex, requiring them to solve strategic problems and develop more refined coding skills. Improvement and resources in building up a farm are continuously managed to ensure efficiency and sustainability. The Farmer Was Replaced is a great combination of creativity and logic with learning that will hook an enthusiast in both programming and simulation games.

# Table of Contents
- [Code Snippets and Explanation](#code-snippets-and-explanation)
- [Challenges and Learnings](#challenges-and-learnings)
- [References](#references)

# Code-Snippets-and-Explanation

## Step 1:Farming on 1 tile

**Code:**
```python
harvest()
do_a_flip()
```

**Explanation:**
Since the game is similar to python the code is run line by line, We start of with basic command ; the above command is used to harvest, which is used to collect the hay.
The second command is similarly does a flip.

**Demo:**
Video Demo:
https://mega.nz/file/2twHDa6S#RAB50n_PWZeSq52oS2cADJPyQlsOZu5HAwJcDaeokOc
**Notes**
- Using the code above I was able to get enough hay to unlock While loop.

## Step 2: Farming on 1 tile
**Code:**
```python
while True:
if can_harvest():
harvest()
```

**Explanation:**
After Unlocking while loop we are arble to use loop for efficiency where we put the harvest command under the while loop which executes the harvest command over and over again.

**Demo:**
Video Demo:
https://mega.nz/file/6lZX3aBK#KVHojE9-O8Pi-0ZZ5h-C3-Rl5bZGkOdk3U6iIR-yg4Q
**Notes**
- With enough hay we are able to unlock speed.
- When Speed is unlocked it causes problem with the while loop therefore you are no longer able tp harvest any more.

## Step 3: Farming on 1 tile
**Code:**
```python
while True:
    if can_harvest():
        harvest()
    else:
        do_a_flip()
```

**Explanation:**
In order to fix the issue we introduce conditional statements; under while loop we add if can_harvest() followed by the code above.

**Demo:**
Video Demo:
https://mega.nz/file/2thQRJTA#rZHfNlpffTzaxmAmarCK9_IIwonABft5VpWyampfAS4
**Notes**
- Using the code above I was able to get enough hay to unlock the tile
- These features were unlocked too: expand along with new plant

## Step 4: Farming on 3 tiles
**Code:**
```python
while True:
    if can_harvest():
        harvest()
        move(North)
```

**Explanation:**
We can now work on multiple field tasks and move the drone towards north(If you move north which is the topmost tile you are just looping back around) using if statement.

**Demo:**
Video Demo:
https://mega.nz/file/nxwGgARQ#K2vaxSntnYIBQcOl3F7ynpd80MR2rBZ5IkMM5UQCxrg
**Notes**
- After enigh hay we are able to increase the yield of the grass(We are able to get 2 hays instead of 1)
- Able to unlock sensors which helps us to analyze our surrounding and certain states of the Drone.

## Step 5: Farming on 1 tile
**Code:**
```python
while True:
    plant(Entitled.Bush)
    if can_harvest():
        harvest()
        move(North)
    else:
        move(North)
```
**Explanation:**
Next we are able to plant one of these bushes with the plant entities.
By using the else statement we use move(North) which help us to harvest one rows of hays and another row of wood.
 
**Demo:**
Video Demo:
https://mega.nz/file/3tJQmS6B#R1dpfTei4vNS0O-1BejSZ1RXbAgV4d2tInhw9Qr9brg
**Notes**
- After enough hay and wood, we are able to unlock the following : operators, debug, expand ugrade(3*3 tile) along with for loop

## Step 6: Farming on 3x3 tile
**Code:**
```python
while True:
    for i in range(get_world_size()):
        move(North)
        if can_harvest():
            harvest()
            if num_items(Items.Hay) < 300:
                plant(Entities.Grass)
            else:
                plant(Entities.Bush)
    move(East)
```

**Explanation:**
After unlocking For Loop and Expanding the tile to 3 by 3 tile we want to run a loop that allows the drone to check all the fields and then loop back to the first field.

**Demo:**
Video Demo:
https://mega.nz/file/3pwjmLjJ#qmXX4GHY-4UqYPwuHrGVRuNTcCeDulkT-X7PzdnqiQo
**Notes**
- It is able to collect all of the hays going through all the rows, after reaching x mark it goes to planting bush and vice versa.
- Next unlockable we are able to unlock is carrot.

## Step 7: Farming on 3x3 tile
**Code:**
```python
while True:
    for i in range(get_world_size()):
        move(North)
        if can_harvest():
            harvest()
            if num_items(Items.Hay) < 300:
                plant(Entities.Grass)
            elif num_items(Items.Wood) < 400:
                plant(Entities.Bush)
            else:
                if num_items(Items.Carrot_Seed) == 0:
                    trade(Items.Carrot_Seed)
                if get_ground_type() == Grounds.Turf:
                    till()
                plant(Entities.Carrots)
    move(East)
```

**Explanation:**
After three crops and every time we want to plant some carrots we also need to purchase seeds. We modify the else statment into elif  to add another statement below for the carrot.
**Demo:**
Video Demo:
https://mega.nz/file/aox0CDxA#D-tRBT_HxSX2hxK17csVkHb-vAV7ewps8eKglkdejgE
**Notes**
- Able to unlock : variables, watering

## Step 8: Farming on 3x3 tile
**Code:**
```python
while True:
    for i in range(get_world_size()):
        move(North)
        if can_harvest():
            #Harvest
            harvest()
            #Water Tank
            if num_items(Items.Water_Tank) < 100:
                trade(Items.Empty_Tank)
            #Watering
            if get_water() < 0.75:
                use_item(Items.Water_Tank)
            #Hay and Bush
            if num_items(Items.Hay) < 300:
                plant(Entities.Grass)
            #Bush
            elif num_items(Items.Wood) < 400:
                plant(Entities.Bush)
            #Carrot
            else:
                if num_items(Items.Carrot_Seed) == 0:
                    trade(Items.Carrot_Seed)
                if get_ground_type() == Grounds.Turf:
                    till()
                plant(Entities.Carrots)
    move(East)
```

**Explanation:**
We add an if statment to purchase water tank(water tank < 100 ) then we want to trade item empty tank. We  
**Demo:**
Video Demo:
https://mega.nz/file/aoowxCYB#g7bFAFnaQPPo7VZ4aK3ny85TGt4GVqyP8oh_BI5hKbc
**Notes**
- Able to unlock : Trees

## Step 9: Farming on 3x3 tile
**Code:**
```python
#Variable
Hay = 300
Wood = 400
WaterTank = 100
Carrot = 300
while True:
    for i in range(get_world_size()):
        move(North)
        x = get_pos_x()
		y = get_pos_y()
        if can_harvest():
            #Hay & Grass
			if num_items(Items.Hay) < Hay:
				if get_ground_type() == Grounds.Soil:
					till()
				plant(Entities.Grass)
			#Wood
			elif num_items(Items.Wood) < Wood:
				if (x % 2 == 0 and y % 2 == 1) or (x % 2 == 1 and y % 2 == 0):
					plant(Entities.Tree)
				else:
					if get_ground_type() == Grounds.Soil:
						till()
					plant(Entities.Bush)
			#Carrot
			elif num_items(Items.Carrot) < Carrot:
				if num_items(Items.Carrot_Seed) == 0:
					trade(Items.Carrot_Seed)
				if get_ground_type() == Grounds.Turf:
					till()
				plant(Entities.Carrots)
    move(East)
```

**Explanation:**
We modify the code to prioitize the crop production. Making the drop to harvest much faster
**Demo:**
Video Demo:
https://mega.nz/file/34wwjYpT#L1ZZr7IaWx0GLTFdXwGcpvxkJOD5Jed99t5NhB3kdQw
**Notes**
- Able to farm certain number of items, after collecting certain item it farms hay again.
-Able to expand the tile into 4x4 tile.

## Step 10: Farming on 4x4 tile
**Code:**
```python
#Variables
Hay = 600
WaterTank = 200
Wood = 600
Carrot = 300

#Main
while True:
	for i in range(get_world_size()):
		move(North)
		x = get_pos_x()
		y = get_pos_y()
		if can_harvest():
			#Harvest
			harvest()
			#Watering
			Watering()
			#Planting
			Planting()
			
	move(East)

def Watering():
	#Water Tank
			if num_items(Items.Water_Tank) < WaterTank:
				trade(Items.Empty_Tank)
			#Watering 
			if get_water() < 0.75:
				use_item(Items.Water_Tank)

def Planting():
	#Hay & Grass
			if num_items(Items.Hay) < Hay:
				if get_ground_type() == Grounds.Soil:
					till()
				plant(Entities.Grass)
			#Wood
			elif num_items(Items.Wood) < Wood:
				if (x % 2 == 0 and y % 2 == 1) or (x % 2 == 1 and y % 2 == 0):
					plant(Entities.Tree)
				else:
					if get_ground_type() == Grounds.Soil:
						till()
					plant(Entities.Bush)
			#Carrot
			elif num_items(Items.Carrot) < Carrot:
				if num_items(Items.Carrot_Seed) == 0:
					trade(Items.Carrot_Seed)
				if get_ground_type() == Grounds.Turf:
					till()
				plant(Entities.Carrots)
```

**Explanation:**
We introduce variable to our main function.
**Demo:**
Video Demo:
![](./step1_video.mp4)
**Notes**
- Unlocked function

## Step 11: Farming on 4x4 tile
**Code:**
```python
while True:
if can_harvest():
harvest()
```

**Explanation:**
Introduced trees to tile(Trees can be planted next to each other but they dont yield fast). In order for the tree to yield fast we plat it in a checkerboard pattern.

**Demo:**
Video Demo:
https://mega.nz/file/S9BmACJY#YKEZx1_HO4aMp8nUEHbpSmzS3fC0lop1Af8ymuJm03k
**Notes**
- We use checkerboard pattern in the main loop which consists of a number dividable by two for y not dividable for x and vice versa.

## Step 10: Farming on 4x4 tile
**Code:**
```python
while True:
if can_harvest():
harvest()
```

**Explanation:**
We create function for watering and plantation for code organization
**Demo:**
Video Demo:
https://mega.nz/file/O1QkBLjL#XdrOZZss1z4rglsGTasNTPYOFzmKEfwhrf0gIcAUQuc
**Notes**
- No changes
 
# Challenges and Learnings
## Challenges
In The Farmer Was Replaced, The challenges I faced are:
Optimized Crop Layouts: All crops have different planting rules. For instance, trees cannot be planted next to each other.So, space efficiency often needs to juggle with crop requirements with lots of planning and code tweaking.
Pathfinding and Resource Management As you progress higher in skills, I found out that resource management is actually the key to success. At one time, a drone will be able to scan and harvest a tile only once. Because of this, you must make sure some efficient paths are being followed in order to maximize yield.
Advanced Timing and Conditions: Most crops are at different times for water and harvest, and you need to program the drone to manage them in concert, using conditions such as soil quality and plant health. It will be even more intensive when you unlock more and more types of plants, with the need to juggle several routines for different crops.
Unlocked Various Commands: We need to make choices between when to invest in upgrades and when to save resources, as usually upgrades mean some costs that hit the efficiency of our farm in the short run.
## Learnings
While playing The Farmer Was Replaced, I learned a few key programming methods and algorithms:
Pathfinding: To make the drone move efficiently across each tile, I used a zigzag traversal to cover all necessary spots without revisiting.
Conditional Logic: I set conditions for specific crops, like spacing trees properly to ensure they grew without interference.
## References
List any resources, articles, or libraries you used or referenced while working on this project.
1. https://youtu.be/p9B7MQ_42p8?si=csXP7sBWOB94wJaI
2. https://youtu.be/gmJ357XAAdE?si=RPZHvF71jDYVYmVZhttps://youtu.be/gmJ357XAAdE?si=RPZHvF71jDYVYmVZ
