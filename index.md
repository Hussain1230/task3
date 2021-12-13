# using const in C++

-The const keyword specifies that a variable's value is constant and tells the compiler to prevent the programmer from modifying it.
```
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```
-In C++, you can use the const keyword instead of the #define preprocessor directive to define constant values. Values defined with const are subject to type checking, and can be used in place of constant expressions. In C++, you can specify the size of an array with a const variable as follows:
```
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```
-In C, constant values default to external linkage, so they can appear only in source files. In C++, constant values default to internal linkage, which allows them to appear in header files.
The const keyword can also be used in pointer declarations.
```
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```
-A pointer to a variable declared as const can be assigned only to a pointer that is also declared as const.
```
// constant_values4.cpp
#include <stdio.h>
int main() {
   const char *mybuf = "test";
   char *yourbuf = "test2";
   printf_s("%s\n", mybuf);

   const char *bptr = mybuf;   // Pointer to constant data
   printf_s("%s\n", bptr);

   // *bptr = 'a';   // Error
}
```
-You can use pointers to constant data as function parameters to prevent the function from modifying a parameter passed through a pointer.
For objects that are declared as const, you can only call constant member functions. This ensures that the constant object is never modified.
```
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```
-You can call either constant or nonconstant member functions for a nonconstant object. You can also overload a member function using the const keyword; this allows a different version of the function to be called for constant and nonconstant objects.
You cannot declare constructors or destructors with the const keyword.
