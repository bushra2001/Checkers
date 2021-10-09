# Checkers
![checkers_interface](https://user-images.githubusercontent.com/61081924/136661906-69155ae5-f495-405c-9f94-adb0dc463dff.png)

## GAME:
### The board:
is consisted of 8 * 8 rows and columns. 

### The piece: 
each player has 12 playing pieces, computer’s piece starts with  c, 
while player’s piece start with b. Each piece can move only towards the enemy’s 
side diagonally, one step at a time, except the cases where a jump (capture) or 
more can be made.

### Kings: 
when a piece gets to the enemy side of the board it gets promoted to a 
king state, which allows it to move backwards to the players own side as well as 
the enemy’s side.

### Jumps (captures):
a jump is possible only over the enemy pieces, when there is a possibility to jump the jump must be taken, if there is more than one possibility 
the player can choose between them. After performing a jump the player must 
perform additional jumps if possible with the same pond.

### Game Over: 
a player wins if the other player runs out of pieces (ponds and kings) or has no valid moves.

### Type of Search Implemented:
Adversarial search algorithms are used in checkers . These algorithms are similar to graph search except that we plan under the assumption that our opponent 
will maximize his own advantage.
In this checker game we implemented following :
    • Minimax Algorithm
    • Alpha-Beta Pruning
    • Heuristic Function



## The Minimax algorithm:
### Parameters:
    • Board: the current board state (including virtual changes made during 
      calculations.
    • Color: the current player’s color depending on the depth (changes with 
      every depth).
    • Alpha: the maximum value stored from the previous depth.
    • Beta: the minimum value stored from the previous depth.
    • Depth: the current depth of the backtracking.

### The Algorithm:
The Minimax function is called to check the best move possible for a given depth; it checks all ponds/kings that have available moves starting at a random 
location (so we wouldnot get the same selection on identical board states).
Minimax is a recursive algorithm which is used to choose an optimal move for a  player assuming that the other player is also playing optimally . There are two    players involved in a game, called MIN and MAX. The player MAX tries to get the  highest possible score and MIN tries to get the lowest possible score, i.e., MIN      and MAX try to act opposite of each other.
    1.  The initial state is the first layer that defines that the board is blank 
       it’s MAX’s turn to play.
    2.  Successor function lists all the possible successor moves. It is defined for all 
           the layers in the tree.
    3.  Terminal State is the last layer of the tree that shows the final state,
        i.e whether the player MAX wins, loses, or ties with the opponent.

![alt text](https://blog-c7ff.kxcdn.com/blog/wp-content/uploads/2017/03/Minimax-3.jpg)
       
To summarize,
Minimax Decision = MAX{MIN{3,5,10},MIN{2,2}}
= MAX{3,2}
= 3

## Heuristic Function: 
A heuristic is a function that estimates how close a state is to a goal. 
The heuristic function takes a state and returns an estimate of its distance (path cost) from a goal state. A heuristic is admissible if it never overestimates the cost of reaching a goal from any node i.e., h(n) <= actual cost of reaching the closest 
goal from n, for any node n, and h(goal) = 0. According to this definition, even the null heuristic (which returns 0 for any node) is admissible so it is not as 
restrictive as it sounds. The only thing required for a heuristic to be admissible is that it never returns a value greater than the actual path cost to the nearest goal for any node.

## ALPHA-BETA PRUNING:
When a human plays the computer (or the computer plays itself), each computer player has 2 possible methods of alpha-beta search. The first is to search down 
to a specified depth. We consider depths of 4 or 5 to be beginner level, depths of 6 to 8 to be intermediate, and depths of 9 or 10 to be advanced. The second 
method is to allow the computer to search for a specified time limit. We consider this to be the better method, since depending on the state of the game and 
number of legal moves in each position, choosing a specific depth can lead to moves of very varying durations. At times, low depth cutoffs are really unnecessary, especially in situations when there are multiple forced moves in a row. When searching for a specified time limit, the computer starts off with an alpha-beta search of depth 4, and then uses iterative deepening, increasing the depth by 1 for each search. If the time limit runs out mid-search, the search to 
the current depth is halted, and the move given by the previous search is used. In almost all cases, the search to each depth takes more time than the searches toall previous (smaller) depths combined, so at most one depth (and often none) is lost due to the extra time used for previous searches done by iterative deepening. Also, if after a search to a given depth, more than half of the time limit has expired, the best move based on that depth is returned without starting the next level of search, since it is highly unlikely that the new search would have time to complete anyway. We find that giving the computer 30 seconds per move leads to a challenging game, although that sometimes needs to be increased in certain end game situations for the computer to correctly force pieces out of corners.

![checkers_1](https://user-images.githubusercontent.com/61081924/136661918-daf53ae3-e2c7-4a7c-a203-5c93cc4746d4.png)
