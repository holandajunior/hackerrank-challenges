#Bot saves princess

Princess Peach is trapped in one of the four corners of a square grid. You are in the center of the grid and can move one step at a time in any of the four directions. Can you rescue the princess?

###Input format

The first line contains an odd integer N (3 <= N < 100) denoting the size of the grid. This is followed by an NxN grid. Each cell is denoted by '-' (ascii value: 45). The bot position is denoted by 'm' and the princess position is denoted by 'p'.

Grid is indexed using Matrix Convention

###Output format

Print out the moves you will take to rescue the princess in one go. The moves must be separated by '\n', a newline. The valid moves are LEFT or RIGHT or UP or DOWN.

###Sample input
```
3
---
-m-
p--
```

###Sample output
```
DOWN
LEFT
```

My solutions follows below:

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
