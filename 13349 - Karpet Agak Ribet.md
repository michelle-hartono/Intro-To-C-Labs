# 13349 - Karpet Agak Ribet

## Brief
The construction is decribed as follow.

For a Carpet that has depth 1, consists of 1x1 square colored black.

For depth 2, it has side length 4, its 4 corners are made up of depth 1 Carpet with a 2x2 center square.

For depth 3, it has side length 10, its 4 corners are made up of depth 2 Carpet with a 4x4 center square.

For carpet with depth of n, its 4 corners are made up of depth (n-1) carpet, without the opposite diagonal of each corner and a 2n-1 center square.

## Input
Input contains only one line with single integer n (1 <= n < 12).

## Output
Output the carpet with depth n and use ' ' (space) to represent white, '*' to represent black.
Remember to add a newline character at the end of line.

## Solution
```c=
#include <stdio.h>
int array [3100][3100];
void karpetRibet(int x, int y, int n, int dir){
    if(n==0)return;
    int h = n/2;

    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            array[x+i][y+j]=1;
        }
    }
    if(dir!=4)karpetRibet(x-h,y-h,h,1);
    if(dir!=3)karpetRibet(x-h,y+n,h,2);
    if(dir!=2)karpetRibet(x+n,y-h,h,3);
    if(dir!=1)karpetRibet(x+n,y+n,h,4);
}
 
int main()
{
    int n;
    scanf("%d",&n);
    n--;
    int d=1<<n;             // 2 to the power of n
    int span=(d-1)*2+d;     // span of carpet

    for(int i=0;i<span;i++){
        for(int j=0;j<span;j++){
            array[i][j]=0;
        }
    }
    
    karpetRibet(d-1,d-1,d,0);
    
    for(int i=0;i<span;i++){
        for(int j=0;j<span;j++){
            if(array[i][j]==1) printf("*");
            else printf(" ");
        }
        printf("\n");
    }
    return 0;
}
```