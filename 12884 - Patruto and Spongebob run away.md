# 12884 - Patruto and Spongebob run away

## Brief
Consider Patrick is on a 2n x 2n grid. And he is at the upper-left cell (1,1) in the begining. When he starts to move, he will go right continuously until the next cell he will move to is out of bounds or has been visited before. Then he will go down with the same pattern(stops when the next cell is out of bounds or has been visited). Similarly he goes left and goes up with the same pattern. And continue to keep going right, going down, going left, going up, going right, going down… until he can’t move anymore.

What you have to do is to offer a map. And there must be a 2n x 2n grid on the map and all the cells in the grid are noted the order Patrick should visit. In this way Patrick can move like a ninja by following your map(don’t worry about Patrick’s counting ability).

The following image shows the example of  n = 3(so the grid is 6 x 6).
![](https://i.imgur.com/mHMvvDa.png)

## Input
The first line contains one integer n (1 ≤ n ≤ 250) – the size of the grid which Patrick moves on.

## Output
Output a 2n x 2n grid which is the map Patrick will follow.

## Solution
```c=

#include<stdio.h>
#define maxn 505
int main() {
	int n;
	scanf("%d",&n);

	int delta_i[] = {0,1,0,-1}, delta_j[] = {1,0,-1,0};
	int ans[maxn][maxn];
	int pos_i = 1, pos_j = 1, cnt = 1;
	for(int len=2*n-1;len>=1;len-=2) {
		for(int type=0;type<4;type++)
			for(int step=0;step<len;step++) {
				ans[pos_i][pos_j] = cnt;
				pos_i += delta_i[type], pos_j += delta_j[type];
				cnt++;
			}
		pos_i++, pos_j++;
	}

	for(int i=1;i<=2*n;i++) {
		for(int j=1;j<=2*n;j++) {
			if(j != 1)	printf(" ");
			printf("%d",ans[i][j]);
		}
		printf("\n");
	}
	return 0;
}
```