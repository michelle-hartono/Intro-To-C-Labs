# 13266 - Nappa's Alphabet

## Brief
Similar to Pascal's Triangle. However, this problem uses alphabets.

## Input
N

N will only be in range of the total number of alphabets.

## Output
Uppercase alphabet pyramid

Detail will show in sample output

Remember to put "\n" in every line

## Solution
```c=

#include <stdio.h>

int main(){
   char letter = 'A';
   int n;
   int temp = 1;
   scanf("%d", &n);
    for (int i = 1; i <= n; i++) {
        for(int k=1;k<=n-i;k++) printf(" ");
        for(int j = 0; j <= (temp / 2); j++) printf("%c", letter++);
        letter = letter - 2;
        for (int j = 0; j < (temp / 2); j++) printf("%c", letter--);
        temp = temp + 2;
        letter = 'A';
        printf("\n");
    }
}

 //the number of letters will not be more than 26

```