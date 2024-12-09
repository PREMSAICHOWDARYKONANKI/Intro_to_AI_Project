# Introduction to AI Project: Optimized Pathfinding and Search Algorithms for Solving the Rubik's Cube

 # Abstract:
       This repository explores solving the 2x2 Rubik's Cube using three advanced search algorithms: Breadth-First Search (BFS), A*, and
       Bidirectional BFS. BFS guarantees the shortest solution by exhaustively exploring all states but is computationally expensive. A* 
       improves efficiency by incorporating a heuristic, namely the Manhattan distance, which estimates the number of misplaced pieces 
       relative to the solved state. Bidirectional BFS optimizes the search process by performing simultaneous searches from both the start
       and goal states, significantly reducing the search space and computational time. Through evaluation, Bidirectional BFS proves to be 
       the most efficient algorithm in terms of time, memory usage, and scalability. This approach is ideal for real-time applications and 
       solving large state-space problems. The project underscores the significance of choosing the right algorithm for solving complex 
       computational challenges.

 # Introduction:
       This project focuses on solving the 2x2 Rubik’s Cube by implementing three different search algorithms—Breadth-First Search (BFS), 
       A*, and Bidirectional BFS. These algorithms are evaluated for their efficiency in finding the shortest path to the solved state of 
       the cube. BFS is a reliable approach that guarantees the shortest solution but comes with a high computational cost due to its 
       exhaustive search nature. The A* algorithm introduces a heuristic to guide the search, improving efficiency by prioritizing states
       closer to the goal. The Bidirectional BFS method, which simultaneously searches from both the start and end states, drastically 
       reduces the search space and runtime. The project aims to compare these algorithms based on their computational efficiency and 
       scalability, ultimately highlighting the optimal choice for solving large-scale puzzles and real-time applications.

   # Software and Tools:
   
       The project is implemented in Python 3.9.0, chosen for its simplicity and robust support for algorithmic tasks. Key libraries               include queuefor managing breadth-first search (BFS) and collections for efficient state tracking and data management. These 
       libraries ensure optimal performance and smooth execution of the algorithms. Python’s versatility makes it ideal for solving the 2x2
       Rubik's Cube efficiently.             
                
# 2x2 Rubik's Cube State Representation and Permutation Logic

       The cube's state is represented as a tuple of integers (0–23), where each value denotes a cubie's position. Movements, such as 
       rotating the front, left, or upper faces, are defined by permutations that track cubie displacements. The key functions include:

              perm_apply: Simulates a move by applying a permutation to the current state.
              perm_inverse: Reverses a move by computing the inverse of a permutation.
              perm_string: Provides a concise string representation for debugging cube states.
       This permutation-based logic ensures accurate tracking and manipulation of the cube's state during the solving process.
      
#  Implemeneted Algorithms: 

   # Breadth-First-Search Function - shortest_path
        The shortest_path function finds the shortest set of moves needed to solve a 2x2 Rubik's Cube from a given start_state to a 
        goal_state by implementing the Breadth-First Search (BFS) algorithm.

       In order to keep track of the states the algorithm has investigated, the function first initializes a dictionary named visited. The 
       present state, its parent state, and the move (or twist) that brought it about are all stored in each entry. In order to store the  
       states that have not yet been investigated, the algorithm first adds the start_state to the BFS queue.The BFS removes states from 
       the queue one at a time as it moves forward. It applies the cube's quarter twists to each state to produce every conceivable 
       following  state. The motion that resulted in the new state being added to the queue and marked as visited is done if it hasn't been 
       visited yet. The end_state is achieved or every potential state has been investigated before this procedure ends.

       The function constructs the series of actions that resulted in the solution by going backwards from the end_state to the start_state
       after locating the goal state. This is accomplished by attaching each step to the path and following the parent states that are kept 
       in the visited dictionary. The sequence of moves from the start state to the objective state is then provided by reversing the path.

       The method returns None, signifying that there is no solution, if it finishes the search without achieving the objective. Since no 
       moves arerequired to solve the puzzle, the method returns an empty path if the start_state and end_state are the same.

   # A* - Function - a_star
       The A* algorithm is implemented by the a_star function, which determines the shortest set of movements needed to solve the Rubik's 
       Cube from a given start state to a destination state. An efficient search for the answer is ensured by the well-informed search 
       algorithm A*, which estimates the cost to attain the goal using a heuristic in addition to the real cost (g_score).

       In order to record states and their corresponding f_score (the sum of the real cost g_score and the heuristic value) and g_score, 
       the function first initializes a priority queue (open_set). The Manhattan distance heuristic is employed here to measure the 
       distance between the present state and the objective by counting the number of pieces that are misplaced in comparison to the solved 
       state. The initial state is first appended to the open_set with a f_score equal to the total of its heuristic and g_score.To make 
       sure the algorithm gives priority to states that seem closer to the objective, the search iteratively explores the state with the 
       lowest  f_score from the queue. 
     
       The function determines whether each state corresponds to the desired state. If so, it goes back via the came_from  dictionary, 
       which contains the parent state and the move that brought it about, to recreate the route to the destination. After that,the path is 
       given back in the proper sequence, from beginning to end.Because the A* algorithm cleverly mixes the heuristic and the  actual cost 
       to guide the search, it ensures that it will identify the most efficient way to the goal, if one  exists. The function returns None 
       if no solution is discovered.

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
       The implemented algorithms—Breadth-First Search (BFS), A*, and Bidirectional BFS—were evaluated for their efficiency in solving the
       2x2 Rubik's Cube. Among these, BFS is the simplest approach, guaranteeing the shortest path by exhaustively exploring all possible
       states from the starting configuration to the goal. However, this thoroughness comes at a significant computational cost, as BFS 
       does not incorporate any optimization techniques to prioritize promising states, resulting in a prolonged runtime of 45.93 seconds 
       in our tests.

       A* improves upon BFS by incorporating a heuristic function, specifically the Manhattan distance, which estimates the number of 
       misplaced cubies relative to the solved state. By combining this heuristic with the actual cost of moves (g_score), A* intelligently
       prioritizes states closer to the solution. This approach significantly reduces the search space, achieving a faster runtime of 18.77
       seconds. Despiteits improvements, A* still requires substantial computational resources, especially as the heuristic can only  
       partially prune the state space.

       Bidirectional BFS emerges as the most efficient algorithm, leveraging a simultaneous search from both the start and goal states. By 
       meeting in the middle, this approach effectively halves the search space and drastically reduces the number of states explored. In 
       our evaluation, Bidirectional BFS solved the Rubik's Cube in just 0.42 seconds, demonstrating its ability to converge quickly and 
       efficiently. This method's dual-front search minimizes unnecessary exploration, significantly reducing both runtime and memory usage.

       In summary, Bidirectional BFS stands out as the optimal choice for solving the 2x2 Rubik's Cube due to its remarkable efficiency and 
       scalability. Its ability to drastically cut down computational time while maintaining precision highlights its superiority over BFS
       and A*.This efficiency is particularly beneficial for real-time applications and large state-space problems, showcasing its 
       versatility and effectiveness in practical scenarios.

# Analysis and Insights:
        Breadth-First Search (BFS):
              1. BFS explores all possible states from the start to the goal, making it reliable for finding the shortest path.
              2. However, it is computationally expensive for larger puzzles because it does not prioritize more promising states.
        A* :
              1. The inclusion of a heuristic (Manhattan distance) improves efficiency by guiding the search toward the goal state.
              2. It balances exploration and exploitation, reducing unnecessary state evaluations.
              3. While faster than BFS, it still processes many states due to the heuristic's limitations in tightly pruning the search 
              space.
              
       Bidirectional BFS:
              1. By performing simultaneous searches from the start and goal states, this algorithm minimizes the number of states explored.
              2. The meeting of the two search fronts allows it to converge rapidly, cutting the search time drastically.
              3. Its efficiency becomes particularly evident in larger state spaces or problems with symmetric structures.
              
# Key Findings:
       1. Time Efficiency: Bidirectional BFS outperforms the other methods, solving the cube almost instantly. This makes it ideal for real-
       time applications where speed is critical.
       2. Computational Overhead: The reduction in the number of states explored directly translates to lower memory and processing 
       requirements, giving Bidirectional BFS a clear advantage in terms of resource utilization.
       3. Scalability: While BFS and A* can struggle with larger or more complex puzzles, Bidirectional BFS scales efficiently, making it a 
       versatile choice for various problem domains.
       
# Significance of the Project:
       This project demonstrates how advanced search algorithms can be applied to solve combinatorial puzzles efficiently. The findings are 
       broadly applicable in fields like:

       1. Robotics: Enhancing pathfinding and manipulation tasks.
       2. Artificial Intelligence: Real-time decision-making in dynamic environments.
       3. Optimization Problems: Solving complex problems with large state spaces.
       4. By comparing BFS, A*, and Bidirectional BFS, this project highlights the importance of choosing the right algorithm for solving 
          computational challenges.
              
# Conclusion:
       Bidirectional BFS emerges as the most efficient algorithm for solving the 2x2 Rubik's Cube. It combines the strengths of BFS and A* 
       while eliminating their limitations through a symmetrical search approach. This method's ability to optimize search space 
       exploration demonstrates its superiority in solving large state-space problems effectively. By halving the search space, 
       Bidirectional BFS significantly reduces both computational time and memory usage. This makes it an ideal solution for real-time 
       problem-solving applications and complex puzzles.

# Additional Resources:
       This repository contains the final project for solving the 2x2 Rubik's Cube using various search algorithms. It includes the   
       following files:
       1. Slides: "Intro to AI - Final Project Rubik's Cube.pptx" (raw file) – A detailed presentation explaining the project's methodology 
       and results.
       2 Video Demonstration: "solving the Rubik's Cube using search algorithm.mp4" (raw file) – A visual demonstration of the Rubik's Cube
       being solved using the search algorithms.
       3. Source Code Files:
              1. rubikscu.py: Defines the 2x2 Rubik's Cube state representation and movement logic.
              2. solver.py: Implements the BFS, A*, and Bidirectional BFS algorithms for solving the cube.

# References
       1. Introduction to Minimal Thinking Technique using an Extremely Fast Implementation of a Rubik’s Cube Solver - Prakhar Gupta
       Director of Science, FAIPS, DPS Society, New Delhi, India
       2.Finding Optimal Solutions to Rubik’s Cube Using Pattern Databases -Richard E. Korf, Computer Science Department , University of 
       California, Los Angeles ,Los Angeles, Ca. 90095, korf@cs.ucla.edu 


      
       
       
