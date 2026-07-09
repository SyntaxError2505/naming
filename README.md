# SyntaxError's C naming convention
Because naming things is hard
## Structs (and unions)
Struct and untions definitions follow PascalCase and always use a typedef with the same name:
```C
typdef struct CoolStruct {
    int cool_field;
} CoolStruct;
```
As seen in the example, fields use snake_case. They are always as descriptive as needed to understand their use in the context. Struct objects use camelCase to clear up confusion and make it possible for objects and definitions to have the same wording:
```C
CoolStruct coolStruct;
printf("%i\n", coolStruct.cool_field);
```
## Macros
Macros are always used in SCREAMING_SNAKE_CASE:
```C
#define THIS_MACRO 3245.0 / 3.0

return THIS_MACRO
```
## Variables
Throwaway variables or single args can use abreviations but mental scope that is bigger than a few lines requires descriptive snake_case names:
```C
// a simple-to-undestand function does not need descriptive names
bool isDigit(char c){
    return c <= '9' && c >= '0';
}

// a function that needs descriptive names to be readable
void doThings(char* name, int x_velocity, int y_velocity){
    int angular_velocity = sqrt(pow(x_velocity, 2) + pow(y_velocity, 2));
    // very complicated code
}
```
There is no reason to not use descriptive names. Only short functions that do not require maintaining are allowed to not use them.  

Counters for for loops use the i, j, k characters. If more scope is required, then all need descriptive names using snake_case:
```C
// 3 dimensional for-loop
for(int i = 0; i < 5; i++){
    for(int j = 100; j != 0; j--){
        for(int k = 0; k < 2; k++){
            return i * j * k;
        }
    }
}
// 4 dimensional for-loop
for(int planet = 0; planet < 100; planet++){
    for(int continent = 0; continent < 100; continent++){
        for(int country = 0; country < 100; country++){
            for(int person = 0; person < 100; person++){
                printf("%i %i %i %i\n", planet, continent, country, person);
            }
        }
    }
}
```
## Pointers
Pointers are handled as their types -> snake_case for variables and fields and camelCase for pointers to structs. Giving them prefixes is not needed in my eyes, since modern tooling like compilers and lsp's will catch any errors. This produces more readable code.
## Functions
Functions use camelCase for names and snake_case for args. Args can be shortened to abreviations if data type or other context gives away their use.
```C
void coolFunction(char important_arg);
```
## Enums
Enums do not have their best implementation in C but we need to live with it and need to name em. Since normally people just use them the same way one would use macros for storing information in numbers, enum members are going to use SCREAMING_SNAKE_CASE. Most enums describe kinds/types of thins. TokenTypes, PersonKinds. Since types sounds more "official", we are going to be standardizing it. Also, if you have read the last sentence, I have already leaked that enum names are using PascalCase because they are often being used as a data type:
```C
typedef enum TokenKinds {
    PRINT,
    HELLO_WORLD
} TokenKinds
```
