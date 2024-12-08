# Intro_to_AI_Project -  Solving the Rubik's cube: Optimized pathfinding and search Algorithms

       This project covered how to solve the Rubik's cubes using A*, Bidirectional BFS, and Breadth First Search.

       In order to solve or determine the shortest path between two states in a 2x2x2 Rubik's Cube, our code implements two algorithms. We 
       have employed A*, Bidirectional BFS, and Breadth-First-Search (BFS).Here is an example of how to use the code.

# 2x2 Rubik's Cube State Representation and Permutation Logic

       The 2x2 Rubik's Cube's state representation and permutation logic are integral to understanding its structure and movements.The cube
       is made up of 24 stickers, each of which represents a cubie (small cube portion) on the puzzle. A tuple of integers between 0 and 23 
       is used to map the locations of these cubies. Variables that represent the cubies' locations with relation to the cube's faces are 
       used to label them. Variables such as flu = 0, luf = 1, and so on, for instance, correlate to the locations of particular cubies 
       according to their relationship to the cube's front (red), left (green), up (white), right (blue), rear (orange), and down (yellow)
       faces. The cube's status can be precisely and methodically tracked with this tuple-based representation.

      The positions of the cubies change in accordance with a permutation as the cube moves, for example, by rotating its front, left, or 
      upper faces. These permutations serve as the foundation for the cube's movement logic, where each permutation denotes a shift in the 
      cubies' locations. For instance, a permutation records the movement of a certain set of cubies to new locations on the cube when the 
      front face is rotated clockwise. Similarly, a distinct permutation results by rotating faces counterclockwise. The cubies are returned 
      to their original places when a move is reversed using the perm_inverse function, which computes the inverse of the current 
      permutation. By applying a permutation to the cube's present state, the perm_apply function essentially does a move. Through a variety 
      of transformations, these functions enable the simulation and manipulation of the cube's state.

      By producing a condensed string representation of a permutation, the perm_string function makes it easier to display or log cube 
      states for examination. The logic allows the basic faces to be rotated both clockwise and counterclockwise, offering a full range of 
      moves for experimenting with various cube combinations. The tuple-based state representation and the manipulation of these 
      permutations allow for effective tracking, simulation, and 2x2 Rubik's Cube solution. For the implementation of algorithms designed to
      solve the cube, including sophisticated methods like pattern databases and reinforcement learning for optimization, this structure is 
      crucial.
      
#  Algorithms : 
#  Breadth-First-Search Function - shortest_path
        The shortest_path function finds the shortest set of moves needed to solve a 2x2 Rubik's Cube from a given start_state to a 
        goal_state by implementing the Breadth-First Search (BFS) algorithm.

       In order to keep track of the states the algorithm has investigated, the function first initializes a dictionary named visited. The 
       present state, its parent state, and the move (or twist) that brought it about are all stored in each entry. In order to store the  
       states that have not yet been investigated, the algorithm first adds the start_state to the BFS queue.The BFS removes states from the 
       queue one at a time as it moves forward. It applies the cube's quarter twists to each state to produce every conceivable following 
       state. The motion that resulted in the new state being added to the queue and marked as visited is done if it hasn't been visited 
       yet. The end_state is achieved or every potential state has been investigated before this procedure ends.

       The function constructs the series of actions that resulted in the solution by going backwards from the end_state to the start_state
       after locating the goal state. This is accomplished by attaching each step to the path and following the parent states that are kept 
       in the visited dictionary. The sequence of moves from the start state to the objective state is then provided by reversing the path.

       The method returns None, signifying that there is no solution, if it finishes the search without achieving the objective. Since no 
       moves arerequired to solve the puzzle, the method returns an empty path if the start_state and end_state are the same.

# A* - Function - a_star
     The A* algorithm is implemented by the a_star function, which determines the shortest set of movements needed to solve the Rubik's Cube
     from a given start state to a destination state. An efficient search for the answer is ensured by the well-informed search algorithm 
     A*, which estimates the cost to attain the goal using a heuristic in addition to the real cost (g_score).

     In order to record states and their corresponding f_score (the sum of the real cost g_score and the heuristic value) and g_score, the 
     function first initializes a priority queue (open_set). The Manhattan distance heuristic is employed here to measure the distance 
     between the present state and the objective by counting the number of pieces that are misplaced in comparison to the solved state. The 
     initial state is first appended to the open_set with a f_score equal to the total of its heuristic and g_score.To make sure the 
     algorithm gives priority to states that seem closer to the objective, the search iteratively explores the state with the lowest f_score 
     from the queue. The function determines whether each state corresponds to the desired state. If so, it goes back via the came_from 
     dictionary, which contains the parent state and the move that brought it about, to recreate the route to the destination. After that,
     the path is given back in the proper sequence, from beginning to end.Because the A* algorithm cleverly mixes the heuristic and the 
     actual cost to guide the search, it ensures that it will identify the most efficient way to the goal, if one exists. The function 
     returns None if no solution is discovered.

     

# Bidirectional BFS- Function - shortest_path_optimized((start, end)
      The shortest_path_optimized function uses Bidirectional BFS to find the shortest path between the start and end states of a 2x2 
      Rubik's Cube, optimizing the search process by exploring from both directions simultaneously. This bidirectional approach reduces the
      search space significantly compared to traditional BFS, as it can meet in the middle rather than searching the entire space from one 
      direction.

       The function first determines whether the start and finish states are identical; if so, it returns an empty path since no moves are 
       required. It initializes two queues, start_queue for the forward search and end_queue for the backward search, as well as 
       dictionaries for tracking the distance between the start and end states (start_dist and end_dist), the parent states (start_parent 
       and end_parent), and the visited states (visited_start and visited_end).

       The path from the start state to the meeting point and subsequently from the meeting point to the end state is reconstructed 
       throughout the merging process by going back via the parent states. The right move sequence is returned by applying the inverse of 
       each step to the backward path.Following the reconstruction of the pathways, the function merges the forward and backward paths and 
       yields the entire set of moves required to solve the puzzle. The function returns None in the event that no solution is discovered. 
       Because it halved the search space, this bidirectional search approach offers significant efficiency benefits over classic BFS, 
       particularly  in large or difficult puzzles.

# Efficiency Comparison: Bidirectional BFS vs. BFS and A* Search
      Bidirectional BFS significantly optimizes the Rubik's Cube solving process by simultaneously exploring the search space from both the 
      start and goal states, reducing the overall number of states investigated. This method uses two distinct queues and parent 
      dictionaries, one for each direction, and merges the forward and backward paths when they meet. 
      
      Compared to traditional BFS, which explores every possible state from the start until the goal is found, Bidirectional BFS 
      drastically reduces the search space, leadingto faster convergence and fewer states explored. In tests, normal BFS took 45.93 seconds 
      to solve, while A* search, guided by a  heuristic, reduced the time to 18.77 seconds. Bidirectional BFS, however, solved the Rubik's 
      Cube in just 0.42 seconds by halving the search space and quickly finding the solution when the searches met in the middle. 
      
      This makes Bidirectional BFS the most efficient method for solving the Rubik's Cube, offering a significant reduction in time 
      complexity and demonstrating its effectiveness in largestate spaces. The optimization becomes more apparent with complex puzzles or 
      larger state spaces, where traditional methods struggle with time efficiency. Its ability to converge faster and reduce unnecessary 
      exploration makes it ideal for real-time problem-solving scenarios. The reduction in the number of states explored also leads to less 
      computational overhead and faster decision-making. As a result, Bidirectional BFS provides a considerable advantage in terms of both 
      performance and resource utilization. This approach can  be extended to other similar large state-space problems, further proving its
      versatility and efficiency.
      

      
       
       
