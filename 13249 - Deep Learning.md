# 13249 - Deep Learning

## Brief
Given a valley with N blocks and each block has a length of L.

Pegura, a rookie vtuber, is wondering how deep the valley is.

Can you donate a superchat to tell her the height H ?

## Input
Two integers N and L (1 <= N, L <= 1000) separated by a blank.

## Output
The height H.

Note that you do not need to print '\n' at the end of the output.

## Solution
```c=

#include<stdio.h>

int main()
{
    int N,L;
    scanf("%d%d", &N, &L);
    printf("%d", N*L);
    return 0;
}
```