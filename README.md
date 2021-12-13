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
{
int x =1;
int y= 5;
int* const a = &x;  
a =&y;      //compile time error(IT'S CONST POINTER!) 
}
```

- constant pointer to constant variable

```
{
const int e = 7;
const int* const z= &e; 
}
```

3. function arguments and return types
We can make the return value type or arguments of a function as **const**. Then we cannot change any of them.

```
void function(const int e)
{
    e++;    // compile time error
}
```

```
const int g()
{
    return 1;
}
```

4. Defining Class Data members as **const** <br/>
defining class data variables using **const** doesn't require their initilization during declaration. it can be done in the constructor

```
class Try{
    const int x;
    public:
    test(int x){
        i = x;
    }
}
```

5. Defining Class Object as **const** <br/>
when we define object as **const** its data members can't be changed once initialized <br/>
for example we can define constant object from the class Try as follows:

```
const Try obj(70);
```

6. Defining Class's Member function as **const** <br/>
A const member functions can do anything but will not modify any data members

```
return_type function_name() const;
```

to sum up the part related to classes see the following code:

```
class StarWars
{
    public:
    int i;
    StarWars(int x)    // constructor
    { 
        i = x; 
    }

    int falcon() const  // constant function
    { 
        cout << "Falcon has left the Base";
    }

    int gamma()
    { 
        i++; 
    }
};

int main()
{
    StarWars objOne(10);        // non const object
    const StarWars objTwo(20);      // const object

    objOne.falcon();     // No error
    objTwo.falcon();     // No error

    cout << objOne.i << objTwo.i;

    objOne.gamma();     // No error
    objTwo.gamma();     // Compile time error
}
```

## & uasge
1. to get the address of a variable

```
{
    int x = 1;
    int* y = &x;
}
```

2. to declare a reference to a type

```
{
    int e = 5;
    int & eRef = e;     //both eRef and e point to the same location and have the same value
}
```

references can be used to modify the values of the referenced variables <br/>
it can also be used to avoid copying of large structures to save time and memory, this is illustrated as follows:

```
// this code is from a geeksforgeeks
struct Student {
   string name;
   string address;
   int rollNo;
}
  
// If we remove & in below function, a new
// copy of the student object is created. 
// We use const to avoid accidental updates 
// in the function as the purpose of the function
// is to print s only.
void print(const Student &s)
{
    cout << s.name << "  " << s.address << "  " << s.rollNo;
} 
```

3. we can use **&&** in logical expressions as it acts as logical AND(returns true when all conditions are true)
this is seen in the following example:

```
{
    int v = 7;
    if (v != 6 && v < 10){
        cout << "true";
    }
    // prints true
}
```

other usages of **&&** include declaring rValue ref, universal ref, or in the end of a function signature as a way of function overloading.
