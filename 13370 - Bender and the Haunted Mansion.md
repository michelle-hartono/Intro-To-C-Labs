# 13370 - Bender and the Haunted Mansion

## Brief
Convert all the given digits to a decimal number.
## Input
integer M which represents the number's base 

a string of exactly 8 integers
## Output
The value of the 8 decimal in base 10 form followed by a newline

## Solution
```c=
#include <stdio.h>
#include <stdlib.h>

long long power(int base, int pow){
    long long num = 1;
    for(int i = 0; i < pow; i++) num *= base;
    return num;
}

int main(){
    int max_bit;
    char num[8];
    scanf("%d", &max_bit);
    for(int i = 0; i < 8; i++) scanf(" %c", &num[i]);

    long long temp = 0;

    for(int i = 0; i < 8; i++){
        switch(num[i]){
            case '0':
                temp += power(max_bit, 7-i) * 0;
                break;
            case '1':
                temp += power(max_bit, 7-i) * 1;
                break;
            case '2':
                temp += power(max_bit, 7-i) * 2;
                break;
            case '3':
                temp += power(max_bit, 7-i) * 3;
                break;
            case '4':
                temp += power(max_bit, 7-i) * 4;
                break;
            case '5':
                temp += power(max_bit, 7-i) * 5;
                break;
            case '6':
                temp += power(max_bit, 7-i) * 6;
                break;
            case '7':
                temp += power(max_bit, 7-i) * 7;
                break;
            case '8':
                temp += power(max_bit, 7-i) * 8;
                break;
            case '9':
                temp += power(max_bit, 7-i) * 9;
                break;
            case 'A':
                temp += power(max_bit, 7-i) * 10;
                break;
            case 'B':
                temp += power(max_bit, 7-i) * 11;
                break;
            case 'C':
                temp += power(max_bit, 7-i) * 12;
                break;
            case 'D':
                temp += power(max_bit, 7-i) * 13;
                break;
            case 'E':
                temp += power(max_bit, 7-i) * 14;
                break;
            case 'F':
                temp += power(max_bit, 7-i) * 15;
                break;
        }
    }

    printf("%lld\n", temp);

    return 0;
}
```