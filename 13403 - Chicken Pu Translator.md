# 13403 - Chicken Pu Translator

## Brief
Chicken Pu did too much 'research' last night and his brain started to get very crazy. He started to speak in numbers and it did not make any sense, but it seems he is trying to tell his friends smth. Being the smart guy that he is, Rib Saw Janna, decided to translate the numbers he is speaking.

Rib noticed that Chicken Pu first says X, the number of strings and then he says a series of 10 binary digits that can be converted to a decimal. Rib also realizes that when he converts the result of these numbers to a character of the alphabet, he would get a sentence. (whitespace is 0, A is 1, B is 2, and so on, the only special character is whitespace and all alphabets are in capital letters)

Now Rib has to help Chicken Pu translate what he is saying because it seems it is very important.

In the case that the result of the 10 digits exceed the alphabet, it must be modded(%), so if the result is 55, the alphabetical value would be 'A'.

## Input
An integer X to determine the number the number strings. (1 < X < 20000)

X number of binary strings consisiting of 10 digits.
## Output
The sentence that Chicken Pu is trying to say. No newline is required

## Solution
```c=
#include<stdio.h>
#include <stdlib.h>

char alphabet[27] = {' ', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 
                    'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q',
                    'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'};

long long power(int base, int pow){
    long long num = 1;
    for(int i = 0; i < pow; i++) num *= base;
    return num;
}

int main(){
    int q;
    char num[11];
    char answer [10000];

    scanf("%d", &q);

    for(int i = 0; i < q; i++){
        for(int i = 0; i < 10; i++) scanf(" %c", &num[i]);

        long long temp = 0;

        for(int i = 0; i < 10; i++){
            switch(num[i]){
                case '0':
                    temp += power(2, 9-i) * 0;
                    break;
                case '1':
                    temp += power(2, 9-i) * 1;
                    break;
            }
        }
        printf("%c", alphabet[temp%27]);
    }
    return 0;
}

```