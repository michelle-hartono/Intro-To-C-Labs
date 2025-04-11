# 13394 - Spider-verse

## Brief
Find all the different movies in the selection.

## Input
An integer Q which represents the number of movies in a selection. (1 <= Q <= 10000 100000)

Q lines of 10 character string which consist of character '1', '0', and 'x'

note: there can only be at most one 'x' in each string

## Output
The number of different movies in the selection followed by a newline

## Solution
```c=
#include <stdio.h>

int power(int base, int pow){
    int num = 1;
    for(int i = 0; i < pow; i++) num *= base;
    return num;
}

int converter(char* str){
    int value = 0;
    for(int i = 0; i < 10; i++){
        switch(str[i]){
            case '0':
                value += power(3, 9-i) * 0;
                break;
            case '1':
                value += power(3, 9-i) * 1;
                break;
            case 'x':
                value += power(3, 9-i) * 2;
                break;
        }
    }
    return value;
}

int main(){
    int count[50000];
    int q;
    scanf("%d", &q);
    for(int i = 0; i < 50000; i++) count[i] = 0;
    for(int i = 0; i < q; i++){
        char str[10];
        scanf("%s", str);
        int num = converter(str);
        count[num] = 1;
    }
    int C = 0;
    for(int i = 0; i < 50000; i++) C += count[i];
    printf("%d\n", C);
    return 0;
}
```