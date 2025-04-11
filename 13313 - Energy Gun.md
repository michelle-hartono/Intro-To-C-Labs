# 13313 - Energy Gun

## Brief
Input an integer into the gun every second for M seconds. Afterwards, each input integer will remain inside the energy gun for N - 1 seconds and it will be outputted during the Nth second.

## Input
The first line will contain 2 integers, N and M.

1<= N, M <= 50

N is the delay of the weapon.

M is the amount of seconds Samus will input integers.

The next line will contain M integers, the integers Samus will input into the code

## Output
The output of the weapon followed by a newline character after M seconds.

If the gun makes no output, the output value will be 0.

## Solution
```c=
#include <stdio.h>

int main(){
    int N, Buff, in;
    int buffer[51];
    scanf("%d %d", &Buff, &in);
    for(int i = 0; i < Buff; i++) buffer[i] = 0;
    for(int i = 0; i < in; i++){
        scanf("%d", &N);
        for(int j = Buff - 1; j >= 1; j--)
            buffer[j] = buffer[j-1];
        buffer[0] = N;
        printf("%d\n", buffer[Buff - 1]);
    }
    return 0;
}
```