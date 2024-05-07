# final_exam_ai
Final Exam of Artificial Intelligence


# Question 1
You have a partially observable version of the 8-puzzle problem from class. You cannot see two tiles. Here is the observation:

Instead of fully observable states, you must work with belief states (the set of all possible states given the current observation).

Draw the belief state for the board shown above. What states does it contain?
Perform the prediction step: Draw the predicted belief state after the transition: move the center-bottom tile up into the center of the board.
Perform the update step: Assume that you observe that the center tile is now the tile "8". Draw the updated belief state with this new observation.

## Answer
A) The belieft sate is {3, 8} or {8, 3}, two possibilities for the unobservable state space

[7 2 4]

[5 x 6]

[3 8 1]

or

[7 2 4]

[5 x 6]

[8 3 1]

B) 

Move the center-bottom tile up into the center of the board:

[ 7 2 4 ]

[ 5 8 6 ]

[ 3 x 1 ]

or

[ 7 2 4 ]

[ 5 3 6 ]

[ 8 x 1 ]




C)

[ 7 2 4 ]

[ 5 8 6 ]

[ 3 x 1 ]


# Question 2
You wonder how studying hard for AI affects your chances of getting a great job in the field of AI after you graduate. Here is a Bayesian network that models the problem with 5 random variables.

How do you interpret the probability P(S) = 0.80? What does it mean?
Are the variables S and E independent?  Are the variables conditionally independent? Explain why or why not.
If you want a great job, what conditional probabilities would you consider to make a maximum a posteriori (MAP) decision? You don't need to calculate the actual probability values but go ahead if you can.
How many entries does the joint probability table P(S, E, L, G, J) have? Explain your answer.
You are interested in the probability of the event (S = False, E = True, L = False, G = True, J = True). Derive the equation and calculate the probability.


## Answer 2

A) The probability of the student studying hard is 80%. This means that regardless of any other variables/factors the student has a 80% chance of studying hard




B) 

Check for independence:

P(S and E) = P(S) * P(E) = 0.8 * 0.10 = 0.08

P ( S n E) = 0.80 * 0.10 = 0.08

Variables S and E are independent as the joint probability is the product of their individual prob


Check for conditionally independence:

Conditional dependence between S and E given G implies that the relationship between S and E is influenced by the value of G. When G is known, information about S provides insights into E, and conversely, information about E sheds light on S. This indicates an interdependence between S and E conditioned on G, so they are not conditionally independent.

 

C)

We want to maximize the function P(J|S,E,L,G) = P(J|L,G). P(L|S) and P(G|S,E) need to be looked at as well to obtain L and G

Thus, The goal would be to determine the likelihood of L and G given S and E so we would want to pick the values of this that maximize P(J|L,G)




D)

S, E, L, G, J have 2 states each

entires = 2^5 = 32

 

E)

P(J=True∣L=False,G=True) = 0.50

P(G=True∣E=True,S=False) = 0.70

P(E=True) = 0.10

P(S=False) = 1 - 0.8 = 0.20

P(L=False | S = False) = 0.40




P(S = False, E = True, L = False, G = True, J = True)

=P(J=True∣L=False,G=True) × P(G=True∣E=True,S=False) × P(E=True) × P(S=False) × P(L=False | S = False)

= 0.50 * 0.70 * 0.10 * 0.20 * 0.40 = 0.0028 = 0.28%


 
# Question 3
You have the following game tree for a simple 2-ply war game: your player has two options (go left or right), and then your opponent decides on a response. Note that hiding is not an option for the opponent when you choose to go left. States are numbered in the diagram. The game is zero-sum, where you want to maximize your score while the opponent seeks to minimize it.

Would a rational opponent ever choose to surrender? Why? Why not?
You want to solve this problem using Minimax search. What are the three minimax values (MV1, MV2, and MV3)?
What are the played actions if both players play optimally?
If you think your opponent plays randomly, how would you decide on your action? What action would you choose? 


## Answer 3

A) In a zero-sum game, the rational opponent would not choose to surrender because the opponent wants to minimize your score while maximize theirs. If they surrender, they would give you a score of 10, which is maximal value you can achieve, but they want to minimize this so they would choose the action that minimizes your score as much as possible.




B) 

MV2

min(0,10,2) = 0

MV3

min(-5,5,10,3) = -5

MV1

max(0, -5) = 0




C) 

You would choose to go left and your opponent chooses to run (giving you a score of 0)




D) I would calculate the expected value of going left vs going right.

Going left = 0 * .33 + 2 * .33 + 10 * .33 = 3.96

Going right = -5 * .25 + 5 * .25 + 3 * .25 + 10 * .25 = 3.25

Since the expected value for going left is greater than going right, I would go left to achieve a higher expected score.


# Question 4
You work on Tesla's self-driving car team and are tasked with training a neural network with 0-1 loss to decide if a detected traffic sign is a stop sign. You have collected video footage of traffic signs from cars and labeled 150,000 videos as "stop signs" or "not a stop sign." Here are some detected signs from the videos.

image.png

 

About 1/10 of all traffic signs in the data are stop signs. You used 80% of the data for training and 20% for testing. On the test set, you classify  27,000 signs correctly.

What is the accuracy of your classifier in percent?
A weak baseline would be a classifier that always predicts the most frequent class in the data. What would be the accuracy of such a baseline classifier?
Is your classifier good, given the baseline?
Your classifier can make two types of mistakes: saying there is a stop sign when there is none or saying there is no stop sign when there is one. The classifier assigns the same loss of 1 to each mistake. Would a rational agent agree with this way of accounting for classification mistakes? Why? Why not?

## Answer 4
a) 150,000 * .20 = 30,000 for testing. 27,000 / 30,000 = 0.9 = 90%

b) We can calculate the proportion of "not a stop sign", so 1/10 of all traffic signs are stop signs then 9/10 are "not a stop sign"

baseline classifier accuracy= 9/10 = .9 or 90%

c) Based on results a and b having the same accuracy of 90%, they are the same, meaning that our classifier is not performing better than the baselinea

d) A rational agent would need agree with this because misclassification of the two groups don't have the same consequences. Misclassifying a stop sign as a non-stop sign could be more dangerous for a vehicle if it doesn't stop, but misclassifying a non-stop sign doesn't have a critical consequence as the vehicle would just stop unnecessarily. The rational agent would then consider the misclassification differently by assigning a different loss value to each mistake.

# Quesiton 5
Describe what algorithm worked best for your Connect-4 assignment. Why do you think it performs better than the other algorithms?

## Answer 5

In my Connect-4 project, I implemented several algorithms: Minimax Search, Simple Move Ordering Strategy, HeuristicMinimaxAgentWithCutoff, and Random Agent.

While Minimax Search outperformed the Random Agent, with a 50% chance of winning, my HeuristicMinimaxAgentWithCutoff showed even better results compared to Minimax Search alone.

The success of the HeuristicMinimaxAgentWithCutoff can be attributed to its integration of alpha-beta pruning and a specified cutoff depth, enhancing the efficiency of the algorithm. Unlike basic Minimax, which evaluates game states solely based on win/loss/draw outcomes, the heuristic function in the HeuristicMinimaxAgentWithCutoff offers a more nuanced assessment. It considers various aspects of the game state that contribute to its progress and strategy, such as the arrangement of pieces, positional advantages, and potential future moves. This comprehensive evaluation allows the agent to make more informed decisions, ultimately leading to a higher winning rate.
