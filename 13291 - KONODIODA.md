# 13291 - KONODIODA

## Brief
Given an image (square matrix) A[N,N], if point P(X,Y) is the center of a star, the following condition will be satisfied:

(1) A[X][j]=255, for all 0<=j<N  (The values in the Xth row are all 255)

(2) A[i][Y]=255, for all 0<=i<N  (The values in the Yth column are all 255)

(3)
A[X+i][Y+i]=255, for all -N<=i<N if 0<=(X+i)<N and 0<=(Y+i)<N

A[X+i][Y-i]=255, for all -N<=i<N if 0<=(X+i)<N and 0<=(Y-i)<N

(The values of two diagonals from the centers are all 255)

For example, a star looks like:
                                                              ![](https://i.imgur.com/i9WFo0u.jpg)

In this problem, given T  square matrices wth size N, you are asked to find out how many stars in each matrix respectively.                                               

## Input
There are three parts of the input:

(1) The number of testcases, T. 1<=T<=1000

(2) The size of the square matrices, N. 1<=N<=2048

(3) T N*N matrices separated by a newline character. 0<=The values in the matrices<=255.

## Output
The number of stars in each matrix.

Note that you need to print "\n" in the end of each answer.

## Solution
```c=

#include<stdio.h>
int test[2049][2049]={0};

int main()
{
    int size ;
    int border;
    int num_que;
    
    scanf("%d", &num_que);
    scanf("%d", &size);
    border = size-1;
    while(num_que--){
        int row[2049]={0};
        int col[2049]={0};
        int diag1[4099]={0};
        int diag2[4099]={0};
        for(int i=0; i<size; i++)
            for(int j=0; j<size; j++)
            {
                scanf("%d", &test[i][j]);
                if(test[i][j]==255)
                {
                    row[i] += 1;
                    col[j] += 1;
                    diag1[i-j+border] += 1;
                    diag2[i+j] += 1;
                }
            }
        unsigned long long int res = 0;
        for(int i=0; i<size; i++)
        {
            for(int j=0; j<size; j++)
            {
                int num_diag1 = (i-j>0)? size-(i-j) : size+(i-j);
                int num_diag2 = (i+j>=size)? 2*size -(i+j+1) : i+j+1;
                if(row[i]==size && col[j]==size && diag1[i-j+border]==num_diag1 && diag2[i+j]==num_diag2)
                {
                    res++;
                }

            }
        }
        printf("%lld\n", res);
    }
    return 0;
}

```