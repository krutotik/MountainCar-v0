# "MountainCar-v0" Reinforcement learning

## Problem description

The main goal of this report is to implement an algorithm which will help an agent to reach the required target in the given environment, and study how different parameters of the algorithm will affect agent's ability to learn. In this report the environment for which an agent will be trained is **"MountainCar-v0"** from OpenAI Gym library. To train an agent for this environment **Q-learning approach** was chosen. "MountainCar-v0" environment will be described below.

## Environment

On OpenAI website the description of this environment looks like this:

> A car is on a one-dimensional track, positioned between two “mountains”. The goal is to drive up the mountain on the right; however, the car’s engine is not strong enough to scale the mountain in a single pass. Therefore, the only way to succeed is to drive back and forth to build up momentum.

There are two dimensions for possible states:

    Num    Observation               Min            Max
    0      Car Position              -1.2           0.6
    1      Car Velocity              -0.07          0.07


The agent can choose one of the following actions:

    Num    Action
    0      Accelerate to the Left
    1      Don't accelerate
    2      Accelerate to the Right
                
Possible rewards agent can recieve for his actions look like this:

    Reward of 0 is awarded if the agent reached the flag (position = 0.5) on top of the mountain
    Reward of -1 is awarded if the position of the agent is less than 0.5

This means that, unless the can figure out a way to ascend the mountain in less than 200 moves, it will always achieve a total reward of -200 units.

From the environment description, this is the starting points for our agent:

    The position of the car is assigned a uniform random value in [-0.6 , -0.4]
    The velocity of the car is always assigned to 0
        
There are two main conditions for ending an episode:

    The car position is more than 0.5
    Episode length is greater than 200

## Algorithm
To train an agent in this environment Q-learning algorithm was chosen. This algorithm looks like this:

![Q-learning](https://github.com/krutotik/MountainCar-v0/blob/master/Pictures/Q-learning%20alg.png?raw=true "name_1")

this is how formula for updating q-table looks like:

![formula](https://github.com/krutotik/MountainCar-v0/blob/master/Pictures/678cb558a9d59c33ef4810c9618baf34a9577686.svg "name_2")

More on Q-learning algorithm: https://towardsdatascience.com/a-beginners-guide-to-q-learning-c3e2a30a653c

The main problem with this particular environment is that it has a continuous state space (Car Position from -1.2 to 0.6 and Car Velocity from -0.07 to 0.07). One approach to deal with it is to use Deep Reinforcement Learning algorithms, but an alternative approach is to simply discretize the state space and train an agent using Q-learning algorithm, as previously planned before. Here, the discretization was performed using 0.1 step for first element (Position) from state vector and 0.01 step for the second element (Velocity), but those values can be changed if needed. 

Another important thing for this environment is that the only way to impove final reward for an agent is to find a way to climb the hill. This can be problematic if the algorithm used for training has limited state exploration alibility. 

## Evaluation
See https://github.com/krutotik/MountainCar-v0/blob/master/Q_learning_report.ipynb
