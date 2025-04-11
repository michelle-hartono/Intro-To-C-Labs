# 13337 - Karpet Sierpinski
## Brief
The Sierpinski Carpet is a self-similar pattern with 8 non-overlapping copies of itself. 

It starts with a white square divided into 9 smaller subsquares, which interior square is filled with black (Depth = 1).

To obtain a carpet at Depth = 2, do the same procedure recursively to the remaining 8 subsquares.
## Input
Input contains single integer n, the Depth of the carpet (1 <= n <= 8).

## Output
Please output the Sierpiński carpet of side length 3n and use '.' to represent white, '#' to represent black.
## Solution
```c=
#include <stdio.h>

int check(int x, int y, int len) {
	if(len == 0) return 0;
	if(x >= len && x < len * 2 && y >= len && y < len * 2) return 1;
	return check(x % len, y % len, len / 3);
}

int main(){ 
	int n; scanf("%d", &n);
	int len = 1;
	for(int i = 0; i < n; i++) len *= 3;
	for(int i = 0; i < len; i++) {
		for(int j = 0; j < len; j++) printf("%c", check(i, j, len / 3) ? '#': '.');
		printf("\n");
	}
	return 0;
}
```
