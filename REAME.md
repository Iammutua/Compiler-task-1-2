### Group members

121891 &nbsp; Salomon Metre <br>
131548 &nbsp; Nathan Ruru <br>
134977 &nbsp; Jeff Munyigi <br>
119314 &nbsp; Oguta Cassey Moses <br> 
129040 &nbsp; Wambua James Mutua <br>

### Task 1

#### Logic used

The Python script reads a C++ file line by line and identifies comments within the code. The comments can be single-line comments starting with `//` or multi-line comments enclosed between `/*` and `*/`.

#### Function to Check if a Line is a Comment

```python
def is_comment(line):
    if line.strip().startswith("//"):
        return True
    return re.match(r'/\*.*\*/', line.strip()) is not None
```

#### Importance of Lexical and Syntax Analysis Concepts

In the logic used to identify comments in a C++ file, both lexical analysis and syntax analysis concepts are important. Here's how they play a role:

##### Lexical Analysis

Lexical analysis involves the process of breaking the input code into meaningful elements, also known as tokens. In our case, identifying comments as tokens is essential for recognizing them within the code. The function `is_comment` utilizes lexical analysis concepts by using regular expressions to identify patterns that represent comments. The regular expressions help in tokenizing the code and identifying comments based on patterns like `//` or `/* */`.

##### Syntax Analysis

Syntax analysis is the process of analyzing the structure of a program to determine its syntactic correctness. Although the provided logic primarily focuses on identifying comments based on lexical analysis, the concept of syntax analysis indirectly comes into play. Recognizing comments accurately is crucial for proper syntax analysis of the code. Incorrectly identifying comments could potentially lead to errors or misinterpretations during subsequent phases of the compilation process. Therefore, ensuring correct comment identification is vital for maintaining the syntactic integrity of the C++ code.

### Task 2

Our implementation uses Flex, a lexical analyzer generator, to identify valid identifiers in a programming language. Identifiers typically start with a letter or an underscore, followed by letters, digits, or underscores. We use regular expressions to define patterns that represent valid identifiers. Below we explain how to use a Flex lexer to identify valid identifiers in a programming language. We will walk through the provided Flex specification and demonstrate how to generate the corresponding C code, compile it, and test it with interactive inputs :

#### Flex Specification

The given Flex specification defines rules to identify valid identifiers. It uses regular expressions to match patterns of valid and invalid identifiers.

```flex
%{
#include <stdio.h>
%}

%%
[a-zA-Z_][a-zA-Z0-9_]*    { printf("'%s' is a valid identifier\n", yytext); }
[0-9]+[a-zA-Z_]+[a-zA-Z0-9_]*   { printf("'%s' is not a valid identifier\n", yytext); }
[0-9]+                   { printf("'%s' is not a valid identifier\n", yytext); }
.                        { printf("'%s' is not a valid identifier\n", yytext); }
%%

int main() {
    yylex();
    return 0;
}
```
In this Flex specification:

[a-zA-Z_][a-zA-Z0-9_]* matches identifiers that start with a letter or underscore, followed by letters, digits, or underscores.
[0-9]+[a-zA-Z_]+[a-zA-Z0-9_]* matches identifiers that start with digits followed by letters, digits, or underscores.
[0-9]+ matches identifiers that consist only of digits.
. matches any other characters that do not form valid identifiers.

#### Generating C Code
To generate the C code from the Flex file (identifier_lexer.l), we use the flex command:
```
flex identifier_lexer.l

```
#### Compiling the generated C code into an executable using gcc:
```
gcc -o identifier_lexer lex.yy.c -lfl
```
This command compiles lex.yy.c into an executable named identifier_lexer, using the Flex library (-lfl).

#### Running the compiled lexer in interactive mode to test identifiers:
We can run the compiled lexer in interactive mode to test identifiers
```
./identifier_lexer
```