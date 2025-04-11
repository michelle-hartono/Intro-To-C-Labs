# 13361 - Cardcaptor Sakura

## Brief
There are 10 tables (indexed from 0 to 9) and no cards on them initially.

Given a command S, Sakura has to follow the instructions below:

(1) print: print the status of each table with the format :"table_idx: cards_on_the tables\n", e.g. "0: 1 3 3 4 5\n". 

Note that if there are no cards, print "No card".

(2) all num len :  Place len cards on each table, and the value on each card is num .

For example, the instruction "all 3 4" changes the status of each table to "table_idx: 3 3 3 3\n";

(3)

place table_idx len

integer_sequence

: Place a stack of cards on table table_idx. len means the number of cards in the stack. An integer sequence integer_sequence of length len is given, in which each integer means the value on the placed card.

For example, the instruction will be like:

place 2 3

3 2 1

And the status of Table_2 will become:

2: 3 2 1

Note that if there are cards already on the target table, the status will be overridden.

(4) swap table_a table_b: Swap the cards on table_a and table_b.

For example:

If the origin status of table 0 and table 1 are:

0: 1 2 3

1: 4 5 6

after "swap 0 1", the status of the two tables become:

0: 4 5 6

1: 1 2 3

This instruction is valid even if one of the tables is empty.

(5) clear: Clean all the tables.

(6) exit: terminates

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
    char cmd[10];
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
        scanf("%s", cmd);
    }
    return 0;
}

```