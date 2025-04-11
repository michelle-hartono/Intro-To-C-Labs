# 13364 - Mom, don't do that

## Brief
Given testcases T, each with two strings, O (origin directory) and D (decoded directory), please print "valid" if you can rearrange D into a sub-directory of O; if it's not possible, print "not valid".

## Input
The first line of the input is an intger T, denoting the number of testcases. 1<= T <= 100

Next 2*T lines contain information of T pairs of O and D.

O is a directory, composed of a sequence of folders separated by a "/", e.g. "/home/hii/it/is/a/folder".

D is a decoded directory, which may be a sub-directory of O or an invalid directory:

example 1: "/hii/home/it", which is valid because you rearrange it into "/home/hii/it".

example 2: "/hii/it/home/nooo", which is invalid because "nooo" is not a part of folders of O.

1 <= length of O or D <= 5000

1 <= number of folders in O <= 50

Note that O and D must start from a "/", and there is no "/" in the end and each folder are not identical.

## Output
For each testcases, if D may be valid, print "valid".

Otherwise, print "not valid".

Note that you have to print "\n" after each answer.

## Solution
```c=

#include <stdio.h>
#include <string.h>

int main()
{
    int n;
    scanf("%d", &n);
    for(int i=0; i<n; i++)
    {
        char root[5000];
        int layer = 0;
        char *token;
        char *all_dir[40];
        scanf("%s", root);
        token = strtok(root, "/");
        while( token != NULL )
        {
            all_dir[layer] = token;
            token = strtok(NULL, "/");
            layer++;
        }
        
        char test[5000];
        int test_len = 0;
        char *test_dir[40];
        scanf("%s", test);
        token = strtok(test, "/");
        while( token != NULL )
        {
            test_dir[test_len] = token;
            token = strtok(NULL, "/");
            test_len++;
        }
        int flag = 1;
        for(int j=0; j<test_len; j++)
        {
            int found = 0;
            for(int k=0; k<layer; k++)
            {
                if(strcmp(all_dir[k], test_dir[j])==0)
                {
                    found = 1;
                    break;
                }
            }
            if(!found)
            {
                flag = 0;
                break;
            }
        }
        if(flag==1)
            printf("valid\n");
        else
            printf("not valid\n");
        
    }
    return 0;
}
```