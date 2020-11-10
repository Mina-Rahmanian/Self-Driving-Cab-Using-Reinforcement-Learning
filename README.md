# Self Driving Cab Using Reinforcement Learning methods (Q-learning and DQN)
<br /><br />

Useful bits of knowledge before start:
+ First of all, please read The Reinforcment Learning book in second edition from this link ["Sutton & Barto" ](https://www.dbooks.org/reinforcement-learning-0262039249/).
+ There is a absolutely Free Resources for Reinforcement Learning [here](https://medium.com/datadriveninvestor/absolutely-free-resources-for-reinforcement-learning-d16a5230cb0f).
+ Also if you want to work with MATLAB you can read this link [RL with MATLAB](https://github.com/MinaR-90/Self-Driving-Cab-Using-Reinforcement-Learning/issues/1) too. 
<br />

## Introduction
<br />
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

The RL determines how good each step is in the process of learning and assigns weights toevery step. Specifically, we studied and implemented two RL algorithms for self-driving cab: Q-learning and Deep Q-networks (DQN). We explored each algorithm, tuned the hyperparameters,and compared their performances on the simulation. The performance of agents trained usingthese different algorithms and the rewards obtained are evaluated and compared for analysis. Theresult showed that DQN gives the best average reward. <br />


## Experimental Setup
<br />

Here, we used OpenAI Gym, which is a toolkit for developing and comparing RL algorithms. Thereare four possible locations for pick up and drop off, these are the ones marked by R,G,B and Y. For a particular iteration, the pickup spot will be highlighted by blue, while the drop off spot willbe highlighted by purple. Therefore, from the initial state as shown in the image, the taxi needs to pick the passenger up from B and drop them off at location Y. When the passenger is not inthe taxi, the colour of the taxi is denoted as yellow, if the passenger has been picked up by thetaxi, its colour changes to green. And finally, once the taxi drops the passenger off, it’s colourchanges back to yellow.  The straight lines (like |) denote obstructions through which the agentcannot pass as a wall. The possible actions the agent can take are: "North - South - West - East- Pickup - Drop-off".
<br />

Some following functions used: 
+ ![#f03c15](evvvvv)


































