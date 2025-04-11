# 13297 - Learning Matrix

## Brief
In this problem, given 2 matrix, A[N, M] and B[M, N]. You are asked to calculate C = (A x B)T (the transpoed matrix of A multiplies B).

## Input
There are three parts of the input:

(1)1<=N<=2100

(2)1<=M<=2100

(3)A[N,M] and B[M,N] separated by a newline charcter. -100<=The values in the matrix<=100.

## Output
C = (A x B)T (the transpoed matrix of A multiplies B).

Note that you have to print whitespaces between each elements and a newline character in the end of each rows.

## Solution
```c=

#include<stdio.h>

int mat1[2101][2101];
int mat2[2101][2101];
int mat3[2101][2101]={0};
int main()
{
    int N,M;
    scanf("%d%d",&N, &M);
    for(int i=0; i<N; i++)
        for(int j=0; j<M; j++)
            scanf("%d", &mat1[i][j]);

    for(int i=0; i<M; i++)
        for(int j=0; j<N; j++)
            scanf("%d", &mat2[i][j]);

    for (int i=0; i<N; i++)
        for(int j=0; j<N; j++)
            for(int k=0; k<M; k++)
                mat3[j][i] += mat1[i][k] * mat2[k][j];

    for(int i=0; i<N; i++)
    {
        for(int j=0; j<N-1; j++)
            printf("%d ", mat3[i][j]);
        printf("%d\n", mat3[i][N-1]);
    }

    return 0;
}
```