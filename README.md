## Ex. No : 1

IMPLEMENTATION OF SYMBOL TABLE

## NAME : Naveen kumar.R

## Register Number : 212223230139

## Date : 22.10.2024

## AIM:

To write a C program to implement a symbol table.

## ALGORITHM:

Start the program.
Get the input from the user with the terminating symbol ‘$’.
Allocate memory for the variable by dynamic memory allocation function.
If the next character of the symbol is an operator then only the memory is allocated.
While reading, the input symbol is inserted into symbol table along with its memory address.
The steps are repeated till ‘$’ is reached.
To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
Stop the program.
PROGRAM:
```
#include <stdio.h> 
#include <ctype.h> 
#include <string.h>
#include <stdlib.h>
#define MAX_EXPRESSION_SIZE 100
int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[5];  // Stores addresses of dynamically allocated memory
    char b[MAX_EXPRESSION_SIZE], d[5], c, srch;  // d size reduced to 5 since we're storing only a few identifiers
    printf("Enter the Expression terminated by $: ");
    
    // Read the expression until '$' is encountered or max size is reached
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) { 
        b[i++] = c;
    }
    b[i] = '\0';  // Null terminate the string
    n = i - 1;    // Correctly initialize n
    printf("Given Expression: %s\n", b);
    printf("\nSymbol Table\n"); 
    printf("Symbol\taddr\ttype\n");
    for (j = 0; j <= n; j++) { 
        c = b[j];
        
        if (isalpha((unsigned char)c)) {  // Check if character is alphabetic
            if (j == n || b[j + 1] == '+' || b[j + 1] == '-' || b[j + 1] == '*' || b[j + 1] == '=') {
                void *p = malloc(sizeof(char));  // Dynamically allocate memory
                add[x] = p;
                d[x] = c; 
                printf("%c\t%p\tidentifier\n", c, p); 
                x++;  // Increment x to store new identifier
            }
        }
    }
    printf("\nThe symbol to be searched: ");
    getchar();  // Consume the newline from the previous input
    srch = getchar();
    for (i = 0; i < x; i++) {  // Search for the symbol
        if (srch == d[i]) {
            printf("Symbol Found\n"); 
            printf("%c@address %p\n", srch, add[i]);
            flag = 1;
            break;  // Exit loop once symbol is found
        }
    }
    if (flag == 0)
        printf("Symbol Not Found\n");
    // Free dynamically allocated memory
    for (i = 0; i < x; i++) {
        free(add[i]);
    }
    return 0;
}
```

## OUTPUT:


![cd](https://github.com/user-attachments/assets/6bd21bb8-c443-4c22-85e4-1a9840a7e58d)

## RESULT:

The program to implement a symbol table is executed and the output is verified.
