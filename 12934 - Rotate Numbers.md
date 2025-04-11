# 12934 - Rotate Numbers

## Brief
Given a large integer, please rotate the whole number by 180o and print out the result.

## Input
The input contains an integer N,  which N is no more than 100 digits.

## Output
Output the 180 degree rotated number, if the rotated number is meaningless, output "No". Please add a newline at the end of your answer.

## Solution
```c=
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

int main(void) {
	
	char s[105], res[105];
	bool invalid = false;
	scanf("%s", s);
	
	int l = strlen(s);
	
	for(int i = 0; i < l; ++i){
		switch(s[i]){
			case '0':
				res[l-i-1] = '0';
				break;
			case '1':
				res[l-i-1] = '1';
				break;
			case '6':
				res[l-i-1] = '9';
				break;
			case '8':
				res[l-i-1] = '8';
				break;
			case '9':
				res[l-i-1] = '6';
				break;
			default:
				printf("No\n");
				return 0;
		}
	}
	
	int start = 0;
	for(int i = 0; i < l; i++)
		if(res[i] == '0')
			++start;
		else
			break;
	
	res[l] = '\0';
	printf("%s\n", res+start);
	
	return 0;
}

```