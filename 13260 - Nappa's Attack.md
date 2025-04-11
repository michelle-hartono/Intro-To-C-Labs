# 13260 - Nappa's Attack

## Brief
Pascal's triangle, in algebra, a triangular arrangement of numbers that gives the coefficients in the expansion of any binomial expression, such as (x + y)n. ... Then the triangle can be filled out from the top by adding together the two numbers just above to the left and right of each position in the triangle.
![](https://i.imgur.com/SwtLXQQ.png)

## Input
The input will contain a single integer N, the strongest soldier at the center.

0<N<1000000

## Output
The output will require you to print the entire traingle pattern with the strongest soldier at the center having the N power level.

There need not be space between numbers but there should be a new line at the end of every line.

## Solution
```c=

#include <stdio.h>

int main(){
   int n;
   scanf("%d",&n);
   for(int i=1;i<=n;i++){
     for(int j=1;j<=n-i;j++) printf(" ");
     for(int j=1;j<=i;j++) printf("%d",j);
     for(int j=i-1;j>=1;j--) printf("%d",j);
     printf("\n");
   }
   return 0;
}
```