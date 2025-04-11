# 13253 - Frieza!!

## Brief
The program in Trunks watch requires 2 variables:

1) F: The volume of Frieze and

2) S: The amount of slices Trunks plans to do

so F/S is the volume of each chunk of Frieza.

You need to write the program that helps Trunks with his calculations. The result of each calculation must also be rounded off to 2 decimal places.

## Input
The input will contain 2 integers F and S.

## Output
Print the results of the calculation rounded off to 2 decimal places, otherwise print "Error".

No newline is needed.

## Solution
```c=

#include<stdio.h>

int main(){
    double A, B, C;
    scanf("%lf %lf", &A, &B);
    if(!B) printf("Error");
    else{
        C = A / B;
        printf("%.2lf", C);
    }
    return 0;
}
```