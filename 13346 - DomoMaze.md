# 13346 - DomoMaze

## Brief
This DomoMaze can be described as a two-dimensional array. With width W and length L, Domo is at the position (0, 0) in the beginning, and Wilson is at the position (W-1, L-1).

 

Each time Domo moves, he can choose one of three ways below:

1. from (i, k) to (i+1, k)
2. from (i, k) to (i, k+1)
3. from (i, k) to (i+1, k+1)

 

Also, there are some portals in the maze. If you step into a certain position (i, k) where has a portal, you will be immediately teleported to the position (i-2, k-2), and the portal you used will disappear. 

It is guaranteed that the position (i-2, k-2) is in the DomoMaze, and the portal will not appear at (W-1, L-1).

 

Given the size of DomoMaze and the position of all portals, please find out how many ways Domo can find Wilson.

## Input
The first line contains two integers W (1 ≤ W ≤ 15) and L (1 ≤ L ≤ 15) - the width and the length of DomoMaze

For the next W lines, each line has L numbers either 1 or 0 - 0 for empty, and 1 for the portal.

 

The variable range of each test case is different.

For test cases 1 ~ 4, there is no portal in the DomoMaze.
For test case 5, there is one portal in the DomoMaze.
For test case 6, there are two portals in the DomoMaze.

## Output
The output only contains a number and a newline character - the number of ways Domo can reach where Wilson is.

 

It's guaranteed that the answer will not be greater than $2^{31}-1$.

## Solution
```c=

#include <stdio.h>

int dp[20][20][4];

int x[2] = {-1, -1};
int y[2] = {-1, -1};
int idx;

int main() {
    int w, h;
    scanf("%d %d", &w, &h);
    getchar();
    
    for (int i = 1; i <= w; i++) {
        for (int k = 1; k <= h; k++)
            if (getchar() == '1') {
                x[idx] = i;
                y[idx] = k;
                idx++;
            }
                 
        getchar();
    }
   
    dp[0][0][3] = 1;
    
    for (int bit = 3; bit >= 0; bit--) {
        for (int i = 1; i <= w; i++)
            for (int k = 1; k <= h; k++) {
                int sum = dp[i-1][k][bit] + dp[i][k-1][bit] + dp[i-1][k-1][bit];
                
                int not_tp = 1;
                
                if (x[0] == i && y[0] == k && (bit % 2)) {
                    not_tp = 0;
                    dp[i][k][bit] = 0;
                    dp[i-2][k-2][bit-1] += sum;
                }
                
                if (x[1] == i && y[1] == k && bit >= 2) {
                    not_tp = 0;
                    dp[i][k][bit] = 0;
                    dp[i-2][k-2][bit-2] += sum;
                }
                
                if (not_tp)
                    dp[i][k][bit] += dp[i-1][k][bit] + dp[i][k-1][bit] + dp[i-1][k-1][bit];
            }
    }
    
    printf("%d\n", dp[w][h][0] + dp[w][h][1] + dp[w][h][2] + dp[w][h][3]);
}
```