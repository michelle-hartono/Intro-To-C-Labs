# 13263 - Star Diamond

## Brief
Given an integer N.

Print a star diamond composed of symbol * with layer N.
 
Each layer has a certain number of stars (symbol *).
 
The middle layer is supposed to have N stars

The first layer and the last layer should contain only one stars.
 
For Layers above the middle layer,
 
each of them contains k + 2 stars, where k is the number of stars of the layer right above the current layer.

For Layers below the middle layer,
 
each of them contains k - 2 stars, where k is the number of stars of the layer right above the current layer.
 
Remember to put spaces in front of each layer to center every layer and form a diamond!

## Input
There is only one line contains an integer N, represents how many layers to print.

0<N<100000


## Output
Star diamond.

If N is even, print "Stop drawing fake diamonds!"

Remember put "\n" at the end of each line.

## Solution
```c=

#include<stdio.h>

int main()
{
   int r;
   scanf("%d",&r);
   if(r%2==0){
        printf("Stop drawing fake diamonds!\n");
   }
   else{
     r = r/2+1;
     for(int i=1;i<=r;i++){
          for(int j=1;j<=r-i;j++)printf(" ");
          for(int j=1;j<=2*i-1;j++)printf("*");
          printf("\n");
     }
     for(int i=r-1;i>=1;i--){
          for(int j=1;j<=r-i;j++)printf(" ");
          for(int j=1;j<=2*i-1;j++)printf("*");
          printf("\n");
     }
   }
 return 0;
}

/*
the diamond will always have odd number as its height
*/
```