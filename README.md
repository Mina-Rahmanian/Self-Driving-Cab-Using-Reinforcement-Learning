# Self Driving Cab Using Reinforcement Learning methods <br /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (Q-learning and DQN)
<br />

Useful bits of knowledge before start:
+ First of all, please read The Reinforcment Learning book in second edition from this link ["Sutton & Barto" ](https://www.dbooks.org/reinforcement-learning-0262039249/).
+ There is a absolutely Free Resources for Reinforcement Learning [here](https://medium.com/datadriveninvestor/absolutely-free-resources-for-reinforcement-learning-d16a5230cb0f).
+ Also if you want to work with MATLAB you can read this link [RL with MATLAB](https://github.com/MinaR-90/Self-Driving-Cab-Using-Reinforcement-Learning/issues/1) too. 
<br /><br />

## Introduction

In this project, the Self-Driving cab task is studied. The major goal is to demonstrate, in a simplified environment, how can Reinforcement Learning techniques be used to develop an efficient and safe approach for picking up and dropping passengers. An evaluation of two state-of-the-art Reinforcement Learning algorithms, namely, Q-learning and Deep-Q-Network is presented and final results are illustrated. Experimental results show that Q-learning method with higher exploitation results in obtaining better policies. <br /><br />

Reinforcement Learning (RL) is a semi supervised machine learning technique in which an agentinteracts with its environment (Fig.1) and takes appropriate actions to achieve its goal by max-imising the rewards. The  problem that we are interested in tackling is the optimization of aself-driving cab in a simplified environment using RL methods.

<p align="center">
<img width="400" height="200" src="https://user-images.githubusercontent.com/71558720/98610550-d5704480-22bd-11eb-934f-177bfd696f7e.PNG"><br />
<p align="center">
   <em>The agent-environment interaction in RL</em>
</p> <br /> 


The  self-driving cab environment provides a basic real-world transportation problem envi-ronment with a single cab that acts as the agent, a passenger that needs to be picked up from his pick up location and dropped at his drop-off location.  The taxi may or may not be at the pick up location at the initial stage. Therefore, essentially the taxi needs to move towards the passenger, pick them up, travel towards the drop-off location and then drop them off. These setof actions constitute the total action space  available  to  the  agent. Additionally there are alsocertain obstructions in the environment which the agent needs to avoid. The environment frameof self-driving cab is shown in(Fig.   2). The goal is to explore and compare how different RL algorithms apply to the self-driving cab problem.<br />


<p align="center">
   <img width="150" height="200" hspace="20" alt="intial state" src="https://user-images.githubusercontent.com/71558720/98610588-e8831480-22bd-11eb-94d0-3aa8d0743978.PNG">
      <em>(a) Initial State</em>
   <img width="150" height="200" hspace="20" alt="pichup" src="https://user-images.githubusercontent.com/71558720/98610577-e15c0680-22bd-11eb-9498-dab344439b39.PNG"> 
      <em>(b) Pickup State</em>
   <img width="150" height="200" hspace="20"  alt="drop off" src="https://user-images.githubusercontent.com/71558720/98610583-e751e780-22bd-11eb-8f2c-5f0edda5e339.PNG">
      <em>(c) Drop-off State</em>
</p> <br />


 Self-driving cabis well-structured and only has a limited number of states,  actions, and rewards; therefore, wethought this was an appropriate environment to develop in. The Smartcab’s problem is to pickup the passenger at one location and drop them off in another. Here are a few things that wewould like our Smartcab to take care of:
 
 + Drop off the passenger to the location.
 + Save passenger’s time by taking minimum time possible to drop off.
 + Take care of passenger’s safety and traffic rules. <br />

The RL determines how good each step is in the process of learning and assigns weights toevery step. Specifically, we studied and implemented two RL algorithms for self-driving cab: Q-learning and Deep Q-networks (DQN). We explored each algorithm, tuned the hyperparameters,and compared their performances on the simulation. The performance of agents trained usingthese different algorithms and the rewards obtained are evaluated and compared for analysis. Theresult showed that DQN gives the best average reward. <br /><br />



## Experimental Setup

Here, we used OpenAI Gym, which is a toolkit for developing and comparing RL algorithms. Thereare four possible locations for pick up and drop off, these are the ones marked by R,G,B and Y. For a particular iteration, the pickup spot will be highlighted by blue, while the drop off spot willbe highlighted by purple. Therefore, from the initial state as shown in the image, the taxi needs to pick the passenger up from B and drop them off at location Y. When the passenger is not inthe taxi, the colour of the taxi is denoted as yellow, if the passenger has been picked up by thetaxi, its colour changes to green. And finally, once the taxi drops the passenger off, it’s colourchanges back to yellow.  The straight lines (like |) denote obstructions through which the agentcannot pass as a wall. The possible actions the agent can take are: "North - South - West - East- Pickup - Drop-off".
<br />

Some following functions used: 
```diff
+ env.render: renders one frame of environment (helpful in visualization)
+ env.step: advances the environment by one timestep
+ env.reset: resets the environment and returns a random initial state.
```
<br />


Certain parameter restrictions:
```diff
+ Number of iterations for each algorithm :1000
+ Measurable quantities:
- Epochs :time step for the agent to reach the final state from the initial state.
- Penalties :We have selected to count the number of times the agent takes an incorrectstep.
+ Hyperparameters:
- Alpha (α) :learning rate.
- Gamma (γ) :discount factor.
- Epsilon (ϵ) :balance factor between exploration and exploitation.
```
<br /><br />



## Solutions


<p align="center">
<img width="700" height="400" alt="figq dqn" src="https://user-images.githubusercontent.com/71558720/98610586-e7ea7e00-22bd-11eb-9e06-a6dff21d4591.PNG"><br />
<p align="center">
   <em>Schematic representation of Q-learning and DQN methods</em>
</p> <br />


### Q-learning:

<p align="center">
<img width="560" height="300" alt="Qlearning" src="https://user-images.githubusercontent.com/71558720/98615180-fe95d280-22c7-11eb-9c6c-d1630eb611ec.PNG"> <br />
</p> <br />


### Deep Q-networks(DQN):

<p align="center">
<img width="550" height="370" alt="dqn" src="https://user-images.githubusercontent.com/71558720/98610593-e91bab00-22bd-11eb-812d-8f6017accdb6.PNG"> <br />
</p> <br /><br />

## Results and Analysis

The agent is trained in 1000 iterations or episodes using the each of two algorithms describedabove. A single iteration in the experiment consists of certain epochs, which is the number oftime-steps the agent took to reach the final state from the initial state, and a penalty count (thepenalty count is the number of times the agent incurred a reward =−10). The observations ofaveraging over 1000 iterations are recorded in a table, and individual algorithm performances areshown in Fig.4. The algorithms are tested with a collection of hyperparameter values as shownin Table 1.<br />
First, the Q-Learning method is applied; learning parameters are varied to study how agentsbehave in different situations. The experimentation produced distinguishable  results  for α=0.3,γ= 0.85. The exploiting (ϵ= 0.9) results in learned values which helps the agent convergefaster and steadily as compared to exploring (ϵ= 0.1) and balanced/greedy (ϵ= 0.5) approaches.Among these cases, exploitation not only has had the lowest amount of average penalties, butit also had  the lowest amount of time step. As shown in the left part of Fig.4, Q-learningperformance in better as we increase the exploitation. A sharp descend in the average epoch andpenalty value in the bottom left plot illustrate this issue.<br /><br />
The original algorithm [here](https://arxiv.org/pdf/1312.5602.pdf) was configured for Atari 2600 games and received successive frames(static images) of the game as input and used a CNN for the Q-network. Here, the algorithmis modified to take as input a one-hot vector representing one of 500 possible states of the taxienvironment. Since the input is a 1D vector, linear feed-forward layers are used instead of convo-lutional layers. The implementation contains 1 hidden layer of 150 neurons as well as a Dropoutlayer. As we can see its performance in (Fig.4). It should be noted that, because of CNN, testingDQN for high iterations is a very time consuming process hence we have selected 1000 iterationfor all algorithm. <br />
At first look, it was not expected that the DQN agent did not perform the bestin the taxi environment. This can be due to the fact that the taxi environment is a hierarchicalRL  problem  unlike  Atari  2600  games. The DQN also takes a longer time per episode due to Experience Replay and Gradient Descent. Despite all these explanations, it is more efficient andfaster than Q-learning explore case. This issue is also easily seen in (Fig.  5 left) where the averageepoch of all utilized methods are compared. The right plot shows the distribution of number ofsteps needed for obtaining a best result in each algorithms. It can be seen that it takes 6000time-steps for Q-learning with exploration to obtain a good policy which shows this method hasthe worst performance among the tested methods. <br />


<p align="center">
<img width="440" height="320"  alt="q-greedy" src="https://user-images.githubusercontent.com/71558720/98610571-def9ac80-22bd-11eb-8b7d-b637b85b47cd.PNG">
<img width="440" height="320"  alt="q-explore" src="https://user-images.githubusercontent.com/71558720/98610568-def9ac80-22bd-11eb-923a-00d4f7a1fbe4.PNG">
<img width="440" height="320"  alt="q-exploit" src="https://user-images.githubusercontent.com/71558720/98610567-de611600-22bd-11eb-8c2e-4a456f9fa2cd.PNG">
<img width="440" height="320"  alt="DQL" src="https://user-images.githubusercontent.com/71558720/98610592-e8831480-22bd-11eb-81fc-ed5f6017e5d8.PNG">
<br /> 
<p align="center">
   <em> Figure 4: Performance Graphs:  Iterations vs (red color: Penalties – blue color:Time step/Epochs)</em>
</p> <br /><br />


| Algorithm           | ϵ   | α  | γ | Average Epochs  | Average Penalties  |
| --------------------|:---:|:---:|:---:|:---:|:---:|
| Q-learning Greedy   |  0.5   |    0.3 |  0.85   |  67.978 | 11.173  |
| Q-learning Exploit  | 0.9  | 0.3  |   0.85 | 47.838  | 2.522  |
| Q-learning Explore  | 0.1  |   0.3 |  0.85 |  276.79 |  78.878 |
| Deep Q-learning     |   0.3  | 0.3  | 0.85  |  123.949 | 12.435  |  
<br />
<em>Table 1: Results observed for algorithms in different values of hyperparameters</em> <br /><br />

***
<p align="center">
<img width="460" height="370"  alt="comp" src="https://user-images.githubusercontent.com/71558720/98610590-e8831480-22bd-11eb-8130-ce73dad1989b.PNG">
<img width="460" height="370"  alt="comp2" src="https://user-images.githubusercontent.com/71558720/98610591-e8831480-22bd-11eb-8649-ec8cdf850ed4.PNG">

<br /> 
<p align="center">
   <em> Figure  5: Comparing  algorithms;  average  steps  required  (left)  and  distribution  of  number  of  stepsneeded (right)</em>
</p> <br /><br />



## ** Mina R **
