# 13292 - Nappa's Alphabet 2

## Brief
Similar to Pascal's Triangle, but print alphabets instead of numbers.

## Input
N

N will only be in range of the total number of alphabets.

## Output
Lowercase alphabet pyramid

Detail will show in sample output

Remember to put "\n" in every line

## Solution
```c=

#include <stdio.h>

int main(){
   char letter = 'a';
   int n;
   int temp = 1;
   scanf("%d", &n);
    for (int i = 1; i <= n; i++) {
        for(int k=1;k<=n-i;k++) printf(" ");
        for(int j = 0; j <= (temp / 2); j++) printf("%c", letter++);
        letter = letter - 2;
        for (int j = 0; j < (temp / 2); j++) printf("%c", letter--);
        temp = temp + 2;
        letter = 'a';
        printf("\n");
    }
}

 //the number of letters will be less than 26
```