# Snake-Game-AI
Solving the snake game with a neural network and algorithms.

This project contains all the python code files you need to make the computer consistently win the Snake game. 
For this, I used 3 computer models: 
  1. Linear neural network combined with the Bellman equation;
  2. Pertubated hamiltonian cycle algorithm;
  3. "Normal" hamiltonian cycle.

From top to bottom, the computer takes less and less risk but it also becomes less and less efficient. Below I explain them all in detail:

The neural network was created with Pytorch and uses reinforcement learning (RL). In the input layer, 11 game parameters are passed: the direction of movement (4), the food direction (4) and information about a possible collision next to the snake's head (3). Next, the hidden layer contains 256 neurons and the output layer returns 3 values representing an action: left, right or straight ahead. Some statistics about the model: 

Activation: Rectified Linear Unit (ReLU) > converts negative numbers to zeros and leaves positive numbers the same.
Optimizer: Adam.
Loss: Mean Squared Error (MSE).

Since the snake is always in a different position on the game board, we need to use the Bellman equation so that wherever the snake is, the model can make the correct predictions. Which looks as follows: V(s)=max(R(s,a)+gamma*V(s'))
Het eerste deel (max(R(s,a)) is simpel gezegd de reward van een actie in een bepaalde state. Het tweede deel (gamma*V(s')) geeft de mogelijke toekomstige reward aan want de slang moet natuurlijk ook vooruit kijken. Daarbij is gamma de discount factor tussen 0 en 1.
