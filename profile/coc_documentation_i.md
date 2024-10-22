# C Object Configuration I
## The Basics
Let's start by creating our first ***config*** file. Use the file extension ***.coc***, short for ***.c-object-configuration***. We declare variables in a very familiar way by first giving it a ***type***, an ***identifier*** and follow it up by assigning our desired ***value*** using an equals sign ***( = ).***
___
Example of ***config.coc***, where ***int*** is the ***type***, ***Foo*** the ***identifier***, and ***42*** the ***value***.
```cpp
int Foo = 42
```
___
The language is strongly typed, and there is no auto type deduction.
***Invalid Declaration:*** No Type
```cpp
Foo = 42
```
___
It's a config language so variables must have a value, there are no default assignments.
***Invalid Declaration:*** No Value
```cpp
int Foo
```
## Types
There are multiple data types available at your disposal.
- ***int:*** 32-bit signed integer
- ***long:*** 64-bit signed integer
- ***float:*** 32-bit floating-point number (single precision)
- ***double:*** 64-bit floating-point number (double precision)
- ***bool:*** Either ***true*** or ***false***
- ***char:*** One single ***character***
- ***string:*** Multiple ***characters***, a piece of ***text***
- ***struct:*** A ***structure***, an arrangement of ***variables***
___
***int:*** A 32-bit signed integer ranges from ***-2 147 483 648*** to ***2 147 483 647***
```cpp
int Min = -2147483648
int Max = 2147483647
```
___
***long:*** A 64-bit signed integer ranges from ***-9 223 372 036 854 775 808*** to ***9 223 372 036 854 775 807***
```cpp
long Min = -9223372036854775808
long Max = 9223372036854775807
```
___
***float:*** A 32-bit floating-point number ranges from ***1.17549e-38*** to ***3.40282e+38***, use a dot ***( . )*** for defining decimals
```cpp
float Min = -340282346638528859811704183484516925440.000000
float Max = 340282346638528859811704183484516925440.000000
```
___
***double:*** A 64-bit floating-point number ranges from ***2.22507e-308*** to ***1.79769e+308***, use a dot ***( . )*** for defining decimals
```cpp
double Min = -179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368.000000
double Max = 179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368.000000
```
___
***bool:*** Booleans are either ***true*** or ***false***, value must be lowercase
```cpp
bool Foo = true
bool Bar = false
```
___
***char:*** It's one character, value must be enclosed in single quotes ***( ' )***
```cpp
char Foo = 'X'
```
___
***string:*** A piece of text, value must be enclosed in double quotes ***( " )***
```
string Foo = "hello world"
```
___
***struct:*** A container for a ***collection*** of ***variables***, value must be enclosed by opening ***' { '*** and closing ***' } '*** curly brackets
```cpp
struct Foo = {
	int Bar = 42
	string Baz = "hello world"
}
```
***struct's*** may also contain another ***struct***, so called ***nested struct's***
```cpp
struct Foo = {
	int Bar = 42

	struct Baz = {
		string Qux = "hello world"
	}
}
```
## Arrays
Any data type can be declared as an ***array***, meaning it will hold a collection of variables, all being the same data type. Enclosing your value with opening ***' [ '*** and closing ***' ] '*** square brackets will declare an ***array***.

Here we declare an ***array*** of type ***int***, containing the first ***10*** elements of the ***Fibonacci Sequence***. Each ***element*** must be separated with a comma ***( , ).***
```cpp
int Fibonacci = [
	0, 1, 1, 2, 3, 5, 8, 13, 21, 34
]
```
___
***struct's*** can also be declared as an ***array*** using the same principles. Let's explore this example in detail.

We declare a ***struct People***, and populate it with two ***elements***, representing individuals.
- ***Alice,*** being ***25*** years old
- ***Bob,*** being ***30*** years old
```cpp
struct People = [
	{
		string Name = "Alice"
		int Age =  25
	},
	{
		string Name = "Bob"
		int Age = 30
	}
]
```
## Files are struct's
In ***C Object Configuration*** we work with ***.coc*** files. We can easily declare variables outside a ***struct***. This is possible since a ***.coc*** file is implicitly wrapped in a ***struct*** itself.

This is a valid ***.coc*** file.
```cpp
int Foo = 42

struct Bar = {
	string Baz = "hello world"
}

bool Qux = true
float Quux = 3.14
```
Here, the file is treated as a ***struct*** containing the following members:
- int Foo
- struct Bar (which itself contains the member ***string Baz***)
- bool Qux
- float Quux