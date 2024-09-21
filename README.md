# Self Driving Vehicle
This project focuses on making a model of Self Driving Vehicle using Tabular Reinforcement Learning Techniques.

# Description
Make a Reinforcement Learning (RL) Model which can drive a car without any external assistance (i.e. Learning from its own experience).

![197708045-e1dd4e4a-4097-4d9c-8ec4-397d69fdbee3](https://user-images.githubusercontent.com/109021179/201350919-1c9ce660-c809-4e15-b322-20ddd7eeb0bc.gif)




# Graphs


![sdv rew](https://user-images.githubusercontent.com/109021179/232239415-f060ae46-ee6d-4ac2-8842-d66d9c2322cb.png)
![sdv running](https://user-images.githubusercontent.com/109021179/232239446-ce27afad-8e67-4da4-9767-ad08545df71b.png)



# Implementation

## Observation Space


We used LiDar observation to measure relative distances of ego vehicle from other vehicles. In this method we don't need separate x,y coordinates and velocities are also not required thus,reducing the state space .Also,this method gives accurate and consistent results.


## State Space
1)16 angles out of which we picked up only 5 to reduce our state space .Took only front and side angles ignoring backward ones.

2)Discretized distances by 0.2 to reduce state space using if statements. <br />
if(d>=0 and d<0.2): <br />
return 0.0 <br />
elif(d>=0.2 and d<0.4):<br />
return 0.2<br />
elif(d>=0.4 and d<=1):<br />
return 0.4


## Action Space

### Discrete Meta Actions

The full corresponding action space is defined in ACTIONS_ALL

ACTIONS_ALL = { <br />
0: 'LANE_LEFT',<br />
1: 'IDLE',<br />
2: 'LANE_RIGHT',<br />
3: 'FASTER',<br />
4: 'SLOWER' <br />
} <br />
Out of the 5 available actions we trained our agent using 3 actions(LANE LEFT,IDLE,LANE RIGHT).We are planning to further extend the project using all 5 actions(i.e we will also invlove the role of velocities).

## Method Used

Q learning <br />
It is an off policy learning method of action values Q(s,a) in which we allow both behaviour and target policies to improve greedily.It is a model free method.

## Environment

env =gym.make('highway-v0')
## Reward
"collision_reward": -25    
"right_lane_reward": 0
                                
"high_speed_reward": 1
                                       
 "lane_change_reward": 0.6   
 "reward_speed_range":[20, 35]
 

# Dependencies
* pip
* gym
* matplotlib
# Installation
* Clone this repository
* Navigate to the cloned repository
* Run command $ pip install -e ./
