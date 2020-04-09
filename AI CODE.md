# sandeep,sameera
Maze solving is the act of finding a route through the maze from the start to finish. Some maze solving methods are designed to be used inside the maze by a traveller with no prior knowledge of the maze, whereas others are designed to be used by a person or computer program that can see the whole maze at once. The mathematician Leonhard Euler was one of the first to analyse plane mazes mathematically, and in doing so made the first significant contributions to the branch of mathematics known as topology. Mazes containing no loops are known as "standard", or "perfect" mazes, and are equivalent to a tree in a graph theory. Many maze solving algorithms are closely related to graph theory. If one pulled and stretched out the paths in the maze in the proper way, the result could be made to resemble a tree.

public int[][] generateMaze() { int[][] maze = new int[height][width]; // Initialize for (int i = 0; i < height; i++) for (int j = 0; j < width; j++) maze[i][j] = 1;

 Random rand = new Random();
 // r for row、c for column
 // Generate random r
 int r = rand.nextInt(height);
 while (r % 2 == 0) {
     r = rand.nextInt(height);
 }
 // Generate random c
 int c = rand.nextInt(width);
 while (c % 2 == 0) {
     c = rand.nextInt(width);
 }
 // Starting cell
 maze[r][c] = 0;

 //　Allocate the maze with recursive method
 recursion(r, c);

 return maze;
}

public void recursion(int r, int c) { // 4 random directions int[] randDirs = generateRandomDirections(); // Examine each direction for (int i = 0; i < randDirs.length; i++) {

     switch(randDirs[i]){
     case 1: // Up
         //　Whether 2 cells up is out or not
         if (r - 2 <= 0)
             continue;
         if (maze[r - 2][c] != 0) {
             maze[r-2][c] = 0;
             maze[r-1][c] = 0;
             recursion(r - 2, c);
         }
         break;
     case 2: // Right
         // Whether 2 cells to the right is out or not
         if (c + 2 >= width - 1)
             continue;
         if (maze[r][c + 2] != 0) {
             maze[r][c + 2] = 0;
             maze[r][c + 1] = 0;
             recursion(r, c + 2);
         }
         break;
     case 3: // Down
         // Whether 2 cells down is out or not
         if (r + 2 >= height - 1)
             continue;
         if (maze[r + 2][c] != 0) {
             maze[r+2][c] = 0;
             maze[r+1][c] = 0;
             recursion(r + 2, c);
         }
         break;
     case 4: // Left
         // Whether 2 cells to the left is out or not
         if (c - 2 <= 0)
             continue;
         if (maze[r][c - 2] != 0) {
             maze[r][c - 2] = 0;
             maze[r][c - 1] = 0;
             recursion(r, c - 2);
         }
         break;
     }
 }
}
