# 13345 - Domo run!

## Brief
Calculate the distance between the minimum one in the alphabetical order and the original name.

## Input
The first line contains an integer T - the number of participants in this race.

For the following T lines, each line contains a string S - the name of each participant.

 

The variable range of each test case is different.

For the test case 1 ~ 2, $1 ≤ T ≤ 10^2$, 1 ≤ the length of S ≤ 5.
For the test case 3 ~ 6, $1 ≤ T ≤ 10^3$, 1 ≤ the length of S ≤ 8.
For the test case 7 ~ 8, $1 ≤ T ≤ 10^4$, 1 ≤ the length of S ≤ 15.

 

Note that each participant's name is in lower case, and will not have any repetitive letters.

## Output
Print the distance each participant needs to run one per line.

## Solution
```c=

#include <stdio.h>
#include <string.h>

long long ans;

int len;
char str[26], order[26];

long long permutation(long long i)
{
    if (i <= 1)
        return 1;
        
    return i * permutation(i-1);
}

int main()
{
    int t;
    scanf("%d", &t);
    
    while (t--)
    {
        ans = 0;
        for (int i = 0; i < 26; i++) order[i] = 0;
        
        scanf("%s", str);
        
        len = strlen(str);
        
        for (int i = 0; i < len; i++)
            for (int k = str[i] - 'a' + 1; k < 26; k++)
                order[k]++;
                
        for (int i = 0; i < len; i++)
        {
            ans += order[str[i] - 'a'] * permutation(len - i - 1);
            
            for (int k = str[i] - 'a' + 1; k < 26; k++)
                if (order[k] != 0)
                    order[k]--;
        }
        
        printf("%lld\n", ans);
    }
}
```