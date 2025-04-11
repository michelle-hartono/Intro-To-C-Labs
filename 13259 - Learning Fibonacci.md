# 13259 - Learning Fibonacci

## Brief
The Fibonacci sequence are the numbers in the following integer sequence:

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...

In mathematical terms, the sequence Fn of Fibonacci numbers is defined by the first two numbers in the Fibonacci sequence (0 and 1) and each subsequent number is the sum of the previous two.

## Input
The input will contain a single integer N

0<N<10000

## Output
You must print the first N numbers from the Fibonacci sequence. There must be a space after every number. There must also be a new line at the end.

## Solution
```c=

#include <stdio.h>

int main()
{
   int bef=0, next=1, after,i;
   int n;
   scanf("%d",&n);
   printf("%d %d ", bef,next);
  for(i=3;i<=n;i++){
     after=bef+next;
     printf("%d ",after);
     bef=next;
     next=after;
   }
   printf("\n");
}
```