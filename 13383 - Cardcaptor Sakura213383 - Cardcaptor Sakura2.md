# 13383 - Cardcaptor Sakura2

## Brief
The problem is modified from 13361 - Cardcaptor Sakura.

You have to implement two more instructions (1) shiftleft (2) shiftright in this problem.

## Input
Commands separated by a newline character.

Note that:

1 <= the value of each card <= 13

1 <= number of cards on each table <= 10000

## Output
Status of each table.

## Solution
```c=
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
int *cards[10];

void Free(void);
void Clear(void)
{
    Free();
    for(int i=0; i<10; i++)
        cards[i] = NULL;
    
}
void Free(void)
{
    for(int i=0; i<10; i++)
    {
        if(cards[i]!=NULL)
            free(cards[i]);
    }
    
}
void Print(void)
{
    for(int i=0; i<10; i++)
    {
        if(cards[i]==NULL)
            printf("%d: No card\n", i);
        else
        {
            printf("%d: ", i);
            for(int j=1; j<cards[i][0]; j++)
                printf("%d ",cards[i][j]);
            printf("%d\n", cards[i][cards[i][0]]);
        }
    }
}
void All(int num, int len)
{
    for(int i=0; i<10; i++)
    {
        cards[i] = (int*)malloc(sizeof(int) * (len+1));
        cards[i][0] = len;
        for(int l=1; l<=len; l++)
            cards[i][l] = num;
    }
}
void Place(int cards_idx, int len)
{
    if(cards[cards_idx]!=NULL)
        free(cards[cards_idx]);
    cards[cards_idx] = (int*)malloc(sizeof(int) * (len+1));
    cards[cards_idx][0] = len;
    for(int i=1; i<=len; i++)
        scanf("%d", &cards[cards_idx][i]);
}
void Swap(int cards_a, int cards_b)
{
    int *tmp;
    tmp = cards[cards_a];
    cards[cards_a] = cards[cards_b];
    cards[cards_b] = tmp;
}
int main(int argc, const char * argv[]) {
    Clear();
    char cmd[15];
    scanf("%s", cmd);
    while(strcmp(cmd, "exit") !=0 )
    {
        if(strcmp(cmd, "all") == 0)
        {
            Free();
            int num, len;
            scanf("%d %d", &num, &len);
            All(num, len);
        }
        else if(strcmp(cmd, "clear") == 0)
        {
            Clear();
        }
        else if(strcmp(cmd, "place") == 0)
        {
            int cards_idx, len;
            scanf("%d %d", &cards_idx, &len);
            Place(cards_idx, len);
        }
        else if(strcmp(cmd, "swap") == 0)
        {
            int cards_a, cards_b;
            scanf("%d %d", &cards_a, &cards_b);
            Swap(cards_a, cards_b);
        }
        else if(strcmp(cmd, "print") == 0)
        {
            Print();
        }
        else if(strcmp(cmd, "shiftleft") == 0)
        {
            int *cards_tmp[10];
            for(int i = 0; i<10; i++)
                cards_tmp[i] = cards[i];
            for(int i = 0; i<9; i++)
            {
                cards[i] = cards_tmp[i+1];
            }
            cards[9] = cards_tmp[0];
        }
        else if(strcmp(cmd, "shiftright") == 0)
        {
            int *cards_tmp[10];
            for(int i = 0; i<10; i++)
                cards_tmp[i] = cards[i];
            for(int i = 1; i<10; i++)
            {
                cards[i] = cards_tmp[i-1];
            }
            cards[0] = cards_tmp[9];
        }
        scanf("%s", cmd);
    }
    return 0;
}

```