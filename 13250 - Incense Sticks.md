# 13250 - Incense Sticks.md

## Brief

![](https://i.imgur.com/bb6rSQr.png)

The incense sticks consist of three lines :

The first line includes four whitespaces and three pairs of (\|/).

The second line includes a pair of brackets(()), a pair of quotation marks ("), and 5 underscores (_).

The third line includes 4 whitespaces, two pairs of  brackets(()), and two pairs of carets(^).

Remember to put a new line character in the end of each line.
 ## Solution
```c=

#include <stdio.h>

int main() {
    printf(" \\|/ \\|/ \\|/ \n");
    printf("(\"_____\")\n");
    printf("( ^ ^)( ^ ^)\n");
    return 0;
}
```