Ex.No:4
RECOGNITION OF A VALID VARIABLE WHICH STARTS WITH A LETTER FOLLOWED BY ANY NUMBER OF LETTERS OR DIGITS USING YACC
Register Number: 212224220054
Date:25/02/26
Aim:
To write a YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits.

ALGORITHM
Start the program.
Write a program in the vi editor and save it with .l extension.
In the lex program, write the translation rules for the keywords int, float and double and for the identifier.
Write a program in the vi editor and save it with .y extension.
Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
Compile the yacc program with YACC compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
Compile these with the C compiler as gcc lex.yy.c y.tab.c
Enter a statement as input and the valid variables are identified as output.
PROGRAM
%{
#include "y.tab.h"
%}
%%
"int" { return INT; }
"float" { return FLOAT; }
"double" { return DOUBLE; }
[a-zA-Z][a-zA-Z0-9]* {
printf("\nIdentifier is %s", yytext); return ID;
}
. { return yytext[0]; }
05/05/2025, 23:19 Ex-4-CD-Lab/README.md at main · Diviyadharshini4/Ex-4-CD-Lab
https://github.com/Diviyadharshini4/Ex-4-CD-Lab/blob/main/README.md 2/5
\n { return '\\n'; }
%%
int yywrap() { return 1;
}
%{
#include <stdio.h>
/* This YACC program is for recognizing the Expression */
%}
%token ID INT FLOAT DOUBLE
%% D: T L;
L: L ',' ID | ID;
T: INT | FLOAT | DOUBLE;
%%
extern FILE *yyin; int main() {
do {
yyparse();
} while (!feof(yyin)); return 0;
}
void yyerror(char *s) { fprintf(stderr, "Error: %s\n", s);
}
Output
image
Result
A YACC program to recognize a valid variable which starts with a letter followed by any number of letters or digits is executed successfully and the output is verified.
