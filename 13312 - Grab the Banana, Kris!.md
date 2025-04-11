# 13312 - Grab the Banana, Kris!

## Brief
Kris can use the words to create a single string which must be spelled as 'BANANA' or else the magic letters won't work. To do this, Kris will input a character one by one into the string. However because the words are very hard to control and that Kris has eaten too much moss, Kris is bound to make many spelling errors. Luckily, he can transform the letter to the '/' sign to delete his mistake So if he accidentally spelled ' BANANP', he can use a '/' to change it back to 'BANAN', and continue from there.

While Kris is doing the work, Queen will keep count of the number of letters Kris got right so far, so if the string so far is 'BANA', Queen will output '4'. If the string Kris created is wrong (e.g. 'BANANP'), Queen will output '-1'.

If he manages to create the string 'BANANA', Queen will output 'Potassium!', and every other character in the input will be ignored. (e.g. 'BANANANANANA' will still output 'Potassium!' since the word 'BANANA' is made) 

On the other hand, if he accidentally puts a number 0 into the string, no more letters can be added. The letters in the box can also run out. In this case, Queen will output 'No Potassium.' in disappointment.

Help Kris make a banana with the magic letters.

## Input
A string of characters (special characters included and all alphabetical letters will be uppercase) Scan until EOF

## Output
If the banana is successfully made, print:

'Potassium!'

else print:

'No potassium.'

with a newline character trailing both.

## Solution
```c=
#include <stdio.h>

int main(){
    int counter_1 = 0, counter_2 = 0, false_1 = 0, false_2 = 0, length = 0;
    char c, temp;
    char banana[6] = {'B', 'A', 'N', 'A', 'N', 'A'};
    while(scanf("%c", &c)){
        if(counter_1 == 6 || counter_2 == 5) break;
        if(c == '/'){
            if(length != 0){
                length--;
                if(counter_1 != 0 && false_1 == 0) counter_1--;
                else if(false_1 != 0) false_1--;
            }
        }
        else if(c == '0') break;
        else{
            length++;
            if(banana[counter_1] != c || false_1 != 0) false_1++;
            if(banana[counter_1] == c && false_1 == 0) counter_1++;
        }
        temp = c;
    }
    if(counter_1 == 6) printf("Potassium!\n");
    else printf("No potassium.\n");
    return 0;
}
```