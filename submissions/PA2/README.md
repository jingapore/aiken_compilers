# Understanding Flex

## Toy example

We run this toy example, to get a feel of Flex.

```
%{

/* The compiler assumes these identifiers. */
#define yylval cool_yylval
#define yylex  cool_yylex

/* Max size of string constants */
#define MAX_STR_CONST 1025
#define YY_NO_UNPUT   /* keep g++ happy */

int words = 0;
%}

%%

[a-zA-Z]+ { words++; }
.

%%

int main(void) {
    printf("Enter text, pressing Crtl-D to complete entry.\n");
    yylex();
    printf("\nYou entered %d words.", words);
    return 0;
}
```

Then we run `flex cool.flex` followed by `clang++ lexx.yy.c -ll -o lexer`. (TODO: port this to build script.)

Upon running `./lexer`, we get a simple lexer that counts the number of words.

### Generated code

Taking a look at the generated code, we see that our snippet from `int main(void)` got copied in. Where did `yylex` resolve to? First, the macros define yylex as cool_yylex. A few lines later, the macros define YY_DECL as yylex. So that block labelled as YY_DECL represents `yylex` that `main` invokes.
