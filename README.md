# Intro_to_AI_Project - Rubik's cube - 2*2*2

 # SOLVING THE RUBIK’S CUBE: Optimized pathfinding and search Algorithms

       This project covered how to solve the Rubik's cubes using A*, Bidirectional BFS, and Breadth First Search.

       In order to solve or determine the shortest path between two states in a 2x2x2 Rubik's Cube, our code implements two algorithms. We 
       have employed A*, Bidirectional BFS, and Breadth-First-Search (BFS).Here is an example of how to use the code.

# Breadth-First-Search Function - shortest_path
       Shortest_path(start, end) is one function. We supply the initial and final states for resolving our Rubik's Cube in this function. 
       This function begins in the start state and moves through the subsequent states using the BFS algorithm until it reaches the end 
       state. The path/moves that lead to the final state are finally returned as a list.

# A* - Function - a_star
      The (a_star)function's A* algorithm determines the shortest route between the Rubik's Cube's start and goal states. Based on the sum 
      of the actual cost (g_score) and the expected cost to the objective (Manhattan distance), it explores states using a priority queue 
      (open_set). The method reconstructs the best path by updating states and going back through the came_from dictionary. The most 
      effective move sequence to solve the cube is guaranteed by this method.

# Bidirectional BFS- Function - shortest_path_optimized((start, end)
      The shortest_path_optimized function determines the shortest path between a Rubik's Cube's start and end states using bidirectional  
      BFS. In order to determine whether the current condition in one direction matches the other or has been visited, it simultaneously 
      investigates from both ways. The pathways from both directions are joined once a common state has been identified, with the inverse 
      ofeach move applied and the path from the end state reversed. A list of moves from the start state to the end state is the resultant  
      merged path.   

# Optimization:
      Bidirectional BFS simultaneously explores the search space from the start and end states to optimize the Rubik's Cube solving process.
      Compared to classical BFS, this lowers the overall number of states investigated. The method use distinct parent dictionaries and 
      queues for each direction. The forward and backward tracks are combined to rebuild the path where the searches intersect. 
      Bidirectional BFS solves the cube more quickly than BFS and A* thanks to this method's huge reduction in time complexity. Faster 
      convergence is made possible by the bidirectional approach's reduction of the search space. Fewer steps are required to get at the 
      solution when they meet in the middle. The Rubik's Cube and other huge state spaces benefit greatly from this optimization.

      

      
       
       
