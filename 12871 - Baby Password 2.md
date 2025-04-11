# 12871 - Baby Password 2

## Brief
In order to prevent a "hacker" like you from stealing passwords by peeking at the database, the passwords are shifted by some integer (possibly zero or negative) and then changed the case before being stored.

For example, if the original password is the character 'A', then after shifting by '+2' and changing the case, the actual password recorded on the database will be the second character after 'A', which is 'c'.

Original + Shift = Actual

Note that we will be dealing the alphabetic sequence as if it is a cycle, i.e., the letter before 'A' is 'Z', and the letter after 'Z' is 'A'.

Hence, if the original password is the character 'a', and the shift is '-1', the new password will be 'Z'.

You have stolen the shifted password stored on the database, denoted as C.

You also know the shift that had been applied to the original password, denoted as D.

Show the original password, followed by a newline character.

## Input
The input will consist of the actual password and the shift

C D

(Note that C may be uppercase or lowercase character, D may be in form "-X" or "+X", where X is an integer between 0 and 25)

## Output
The original password, with a trailing newline character.

## Solution
```c=

#include <stdio.h>

int main() {
	char c;
	int x;
	scanf("%c %d", &c, &x);
	if(c >= 'A' && c <= 'Z') {
		c += ('a' - 'A');
		c = ((c - 'a' - x) % 26 + 26) % 26 + 'a';
	}
	else {
		c += ('A' - 'a');
		c = ((c - 'A' - x) % 26 + 26) % 26 + 'A';
	}
	printf("%c\n", c);
	return 0;
}
```
