# Bot saves princess 1 and 2

## Bot saves princess 1

Princess Peach is trapped in one of the four corners of a square grid. You are in the center of the grid and can move one step at a time in any of the four directions. Can you rescue the princess?

### Input format

The first line contains an odd integer N (3 <= N < 100) denoting the size of the grid. This is followed by an NxN grid. Each cell is denoted by '-' (ascii value: 45). The bot position is denoted by 'm' and the princess position is denoted by 'p'.

Grid is indexed using Matrix Convention

### Output format

Print out the moves you will take to rescue the princess in one go. The moves must be separated by '\n', a newline. The valid moves are LEFT or RIGHT or UP or DOWN.

### Sample input
```
3
---
-m-
p--
```

### Sample output
```
DOWN
LEFT
```

## Solution
My solution was developed using python 3. It uses Manhattan distance to calculate how many steps in each diretion the bot has to walk over. It follows below:

```python
#!/usr/bin/python
def displayPathtoPrincess(n,grid):
    points = {}
    
    for i in range(n):
        for j in range(n):
            if( grid[i][j] != '-' ):
                points[ grid[i][j] ] = (i, j)
    
    ## Manhattan distance with directions
    distX = ( points['m'][0] - points['p'][0] )
    distY = ( points['m'][1] - points['p'][1] )
    
    for i in range(abs(distX)):
        if( distX < 0 ):
            print("DOWN")
        else:
            print("UP")
    
    for i in range(abs(distY)):
        if( distY < 0 ):
            print("RIGHT")
        else:
            print("LEFT")
    
    
    
m = int(input())
grid = [] 
for i in range(0, m): 
        grid.append(input().strip())

        
displayPathtoPrincess(m,grid)

``` 



## Bot saves princess 2

In this version of "Bot saves princess", Princess Peach and bot's position are randomly set. Can you save the princess?

### Task

Complete the function nextMove which takes in 4 parameters - an integer N, integers r and c indicating the row & column position of the bot and the character array grid - and outputs the next move the bot makes to rescue the princess.

### Input Format

The first line of the input is N (<100), the size of the board (NxN). The second line of the input contains two space separated integers, which is the position of the bot.

Grid is indexed using Matrix Convention

The position of the princess is indicated by the character 'p' and the position of the bot is indicated by the character 'm' and each cell is denoted by '-' (ascii value: 45).

### Output Format

Output only the next move you take to rescue the princess. Valid moves are LEFT, RIGHT, UP or DOWN

### Sample Input
```
5
2 3
-----
-----
p--m-
-----
-----
```

### Sample Output
```
LEFT
```

### Resultant State
```
-----
-----
p-m--
-----
-----
```

### Solution
It follows the same idea as Bot saves princess 1 problem: it calculates Manhattan distance between bot's current position and princess position in every updated state.

```
def nextMove(n,r,c,grid):
    for i in range(n):
        for j in range(n):
            if( grid[i][j] == 'p' ):
                pPos = (i, j)
                
    distX = r - pPos[0]
    distY = c - pPos[1]
    
    if( distX < 0 ):
        return "DOWN"
    elif( distX > 0 ):
        return "UP"
    
    if( distY < 0 ):
        return "RIGHT"
    elif( distY > 0 ):
        return "LEFT"
    



n = int(input())
r,c = [int(i) for i in input().strip().split()]
grid = []
for i in range(0, n):
    grid.append(input())

print(nextMove(n,r,c,grid))
```


