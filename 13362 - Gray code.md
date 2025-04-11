# 13362 - Gray code

## Brief
Given an integer n, print the gray code sequence.

## Input
1<=n<=20

## Output
The corresponding gray code sequence.

Note that you have to print "\n" after each numbers.

## Solution
```c=
//by 景璞

#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    int num = 1;
    num = num<<n;
    int res[num];
    res [0] = 0;
    
    int cur_n = 1;
    for(int i = 1; i <= n; i++)
    {
        for(int j = cur_n-1; j >= 0; j--)
        {
            res[cur_n] = (1 <<(i-1) | res[j]);
            cur_n++;
        }
    }
    for(int i=0; i<num; i++)
        printf("%d\n", res[i]);
    return 0;
}
```

```c=

#include <stdio.h>

int main()
{
	int n;
	scanf("%d", &n);
	
	for (int i = 0; i < (1 << n); i++)	printf("%d\n", (i ^ (i >> 1)));
}
```