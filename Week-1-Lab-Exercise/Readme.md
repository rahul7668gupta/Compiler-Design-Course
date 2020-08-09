## Week -1 Lab Exercise

#### Implementation of Language recogniser for set of all strings ending with two symbols of same type.

### DFA Diagram 

![](https://github.com/rahul7668gupta/Compiler-Design-Course/blob/master/Week-1-Lab-Exercise/image.jpg?raw=true)

#### ∑ = {a, b}

#### Test Cases

| Input 	| Expected Output 	|
|-------	|-----------------	|
| aa    	| Accepted        	|
| abb   	| Accepted        	|
| baabb 	| Accepted        	|
| bba   	| Not Accepted    	|
| abc   	| Invalid Input   	|

#### Code

```
#include <stdio.h>

int main()
{
    int state = 0, i = 0;
    char cur, inp[30];
    printf("Enter test string ending with two symbols of same type\n");
    scanf("%s", inp);
    while(cur=inp[i++]){
        switch(state) {
            case 0: 
                if(cur == 'a'){
                    state = 1;
                } else if(cur == 'b') {
                    state = 3;
                } else {
                    printf("Invalid Token");
                }
                break;
            case 1:
                if(cur == 'a'){
                    state = 2;
                } else if(cur == 'b') {
                    state = 3;
                } else {
                    printf("Invalid Token");
                }
                break;
            case 2:
                if(cur == 'a'){
                    state = 2;
                } else if(cur == 'b') {
                    state = 3;
                }else {
                    printf("Invalid Token");
                }
                break;
            case 3:
                if(cur == 'a'){
                    state = 1;
                } else if(cur == 'b') {
                    state = 4;
                } else {
                    printf("Invalid Token");
                }
                break;
            case 4:
                if(cur == 'a'){
                    state = 1;
                } else if(cur == 'b') {
                    state = 4;
                } else {
                    printf("Invalid Token");
                }
                break;
        }
    }

    if(state == 2 || state == 4){
        printf("\nString accepted\n");
    } else {
        printf("\nString not accepted\n");
    }
    return 0;
}
```