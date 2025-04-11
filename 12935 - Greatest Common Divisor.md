# 12935 - Greatest Common Divisor

## Brief
Given two integers, calculate their greatest common divisor.

## Input
The input contains two integers between 2 and 10000.

## Output
Output the greatest common divisor of the input pair, follow by a newline.

## Solution
```c=

#include<stdio.h>
int main() {
	int a,b;
	scanf("%d %d",&a,&b);
	for(int i=(a < b ? a : b);i>=1;i--)
		if(a % i == 0 && b % i == 0) {
			printf("%d\n",i);
			break;
		}
	return 0;
}
```