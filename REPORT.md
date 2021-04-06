# Report
This document contains my report for the Udacity `Continuous control` project. It includes the project goal, environment, learning algorithm, results and ideas for future work

## The Goal
The goal of the agent is to maintain its position at the target location for as many time steps as possible
The task is episodic, and in order to solve the environment, the agent must get an average score of +30 over 100 consecutive episodes.

## The Environment

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

## The Learning Algorithm
The agent is trained with the off-policy method called *Deep Deterministic Policy Gradient*.
> Deep Deterministic Policy Gradient (DDPG) is an algorithm which concurrently learns a Q-function and a policy. It uses off-policy data and the Bellman equation to learn the Q-function, and uses the Q-function to learn the policy.

The algorithm is further described in [Continuous control with deep reinforcement learning](https://arxiv.org/abs/1509.02971).

### Model architecture

**Actor Neural Network**
The architecture includes:
- _Input size_ of **33**
- _Output size_ of **4**
- 2 fully connected hidden layers

*Critic Neural Network*
The architecture includes:
- _Input size_ of **4**
- _Output size_ of **1**
- 2 fully connected hidden layers



### Hyper parameters
|                                            |                                          |
| :----------------------------------------- | :--------------------------------------- |
| <p align="left">BUFFER_SIZE</p>            | <p align="left">1e5</p>                  |
| <p align="left">BATCH_SIZE</p>             | <p align="left">128</p>                  |
| <p align="left">GAMMA</p>                  | <p align="left">0.99</p>                 |
| <p align="left">TAU</p>                    | <p align="left">1e-3</p>                 |
| <p align="left">LR_ACTOR</p>               | <p align="left">1e-3</p>                 |
| <p align="left">LR_CRITIC</p>              | <p align="left">1e-3</p>                 |
| <p align="left">WEIGHT_DECAY</p>           | <p align="left">0</p>                    |

## Results

I was able to achieve the goal in less than 200 episodes

```angular2html
Episode 100	Average Score: 1.23
Episode 114	Average Score: 30.27
Environment solved in 114 episodes!	Average Score: 30.27
```
![alt text](./score_chart.jpg)

## Ideas for Future Work

- Try using D4PG, A3C, A2C, TRPO, PPO to improve performance
- Modify the model to solve the task in fewer episodes