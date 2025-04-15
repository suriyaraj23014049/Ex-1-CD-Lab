# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# Register Number : 212223230073
# Date : 15/04/25
# AIM :
## To write a C program to implement a symbol table.
# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol and memory address are inserted into the symbol table.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and the symbol table has been checked for the corresponding variable, the variable along with its address is displayed as a result.
8.	Stop the program. 
# PROGRAM
```c
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[15]; // Increased size for safety
    char b[MAX_EXPRESSION_SIZE], d[15], c, srch;

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; 
    n = i;

    printf("Given Expression: %s\n", b);

    printf("\nSymbol Table\n");
    printf("Symbol\taddr\ttype\n");

    for (j = 0; j < n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            // Check if it's the last character or followed by an operator
            if (j == n - 1 || b[j + 1] == '+' || b[j + 1] == '-' || b[j + 1] == '*' || b[j + 1] == '=') {
                void *p = malloc(sizeof(char));
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    // Clear input buffer before reading next char
    while ((c = getchar()) != '\n' && c != EOF);

    printf("\nThe symbol to be searched: ");
    srch = getchar();

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c@address%p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (!flag) {
        printf("Symbol Not Found\n");
    }

    // Free allocated memory
    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    return 0;
}

```
# OUTPUT
![alt text](<Screenshot 2025-04-10 141527.png>)
![alt text](<Screenshot 2025-04-10 141553.png>)
# RESULT
### The program to implement a symbol table is executed and the output is verified.
