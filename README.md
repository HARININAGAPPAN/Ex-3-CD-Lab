# Ex-3-RECOGNITION-OF-A-VALID-ARITHMETIC-EXPRESSION-THAT-USES-OPERATOR-AND-USING-YACC
# Date:8/5/25
# AIM
To write a yacc program to recognize a valid arithmetic expression that uses operator +,- ,* and /.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the operators =,+,-,*,/ and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter an arithmetic expression as input and the tokens are identified as output.
# PROGRAM
cd3.l
```
%{
#include "y.tab.h"
%}

%%

"="  { printf("\nOperator is EQUAL"); return '='; }
"+"  { printf("\nOperator is PLUS"); return '+'; }
"-"  { printf("\nOperator is MINUS"); return '-'; }
"/"  { printf("\nOperator is DIVISION"); return '/'; }
"*"  { printf("\nOperator is MULTIPLICATION"); return '*'; }

[a-zA-Z_][a-zA-Z0-9_]* {
    printf("\nIdentifier is %s", yytext);
    return ID;
}

.  { return yytext[0]; }
\n { return 0; }

%%

int yywrap() {
    return 1;
}

cd3.y

%{
#include<stdio.h>
%}

%token A ID

%%

statement: A'='E

| E {

printf("\n Valid arithmetic expression");

$$=$1;

}

;

E: E'+'ID

| E'-'ID

| E'*'ID

| E'/'ID

| ID

;

%%

extern FILE*yyin; main() {
do { yyparse();
}while(!feof(yyin)); } yyerror(char*s)
{

}

```
# OUTPUT
![Screenshot 2025-05-08 135826](https://github.com/user-attachments/assets/49f706c5-ff2f-4dd0-893a-2e0cf87a954a)


# RESULT
A YACC program to recognize a valid arithmetic expression that uses operator +,-,* and / is executed successfully and the output is verified.
