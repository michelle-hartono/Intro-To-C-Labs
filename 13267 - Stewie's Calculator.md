# 13267 - Stewie's Calculator

## Brief
Invent a calculator which will only be able to take in 2 numbers and an operator in a specific order and then will output the answer with 2 decimal places.

The operators the calculator will have are addition (+), subtraction(-), division(/), and multiplication(*).

## Input
The input will consist of 2 numbers, which may contain decimals, and an operator in the following order:

I1 Op I2

(there will be spaces between each character)

## Output
Output the result of the equation with two decimal spaces and a trailing newline character

If the equation cannot be calculated, print "Error" with a trailing newline character

## Solution
```c=
#include<stdio.h>

int main(){
    double M, N, O;
    char c;
    scanf("%lf %c %lf", &M, &c, &N);
    if(c == '/' && N == 0) printf("Error\n");
    else{
        if(c == '+') O = M + N;
        else if(c == '*') O = M * N;
        else if(c == '/') O = M / N;
        else if(c == '-') O = M - N;
        printf("%.2lf\n", O);
    }
    return 0;
}
```