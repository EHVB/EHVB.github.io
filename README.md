# Const and & usage
## const usage  
**const** keyword is generally used to declare data that can't be modified
1. we can use **const** to declare a constant variable in C++. Also, the constant variables must be initialized while they are declared.
```
{
    const int x = 7;
    const int j = i + 10;     // works fine
    i++;    // this leads to Compile time error   
    const int k;    //leads to compile time error(no initilization)
}

```
2. we can use **const** with pointers and this has three cases
- pointer to constant variable
``` 
const int* u;
```
*or*
```
int const* u;
```
- constant pointer to variable
```
