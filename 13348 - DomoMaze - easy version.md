# 13348 - DomoMaze - easy version

## Brief
Domo is a brilliant dog. By the way, his grandfather is also a brilliant dog, and he has built a giant maze in the forest years ago, which is called "DomoMaze".

 

One day, Domo loses his ball called Wilson in this maze. He wants to take Wilson back, and your task is to find out how many ways Domo can reach the position where Wilson is.

 

This DomoMaze can be described as a two-dimensional array. With width W and length L, Domo is at the position (0, 0) in the beginning, and Wilson is at the position (W-1, L-1).

 

Each time Domo moves, he can choose one of three ways below:

1. from (i, k) to (i+1, k)
2. from (i, k) to (i, k+1)
3. from (i, k) to (i+1, k+1)

 

Also, there are some barricades in the maze. You can't enter the barricades on the map.

It is guaranteed that the barricade will not appear at (0, 0) and (W-1, L-1).

 

Given the size of DomoMaze and the position of all barricades, please find out how many ways Domo can find Wilson.

## Input
The first line contains two integers W (1 ≤ W ≤ 15) and L (1 ≤ L ≤ 15) - the width and the length of DomoMaze

For the next W lines, each line has L numbers either 1 or 0 - 0 for empty, and 1 for the barricade.
## Output
The output only contains a number and a newline character - the number of ways Domo can reach where Wilson is.

 

It's guaranteed that the answer will not be greater than 231-1.
## Solution
```c=
#include <stdio.h>

int w, h;
char _DomoMaze[20][20];
int cal[20][20];

int main()
{
    scanf("%d %d", &w, &h);
    
    for (int i = 1; i <= w; i++)
        for (int k = 1; k <= h; k++)
            scanf(" %c", &_DomoMaze[i][k]);
    
    for (int i = 0; i <= w; i++) cal[i][0] = 0;
    for (int i = 0; i <= h; i++) cal[0][i] = 0;
    
    cal[0][0] = 1;
    
    for (int i = 1; i <= w; i++)
        for (int k = 1; k <= h; k++)
        {
            if (_DomoMaze[i][k] == '1') cal[i][k] = 0;
            else cal[i][k] = cal[i-1][k] + cal[i][k-1] + cal[i-1][k-1];
        }
    
    printf("%d\n", cal[w][h]);
}
```