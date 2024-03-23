# PHP is a Loosely Typed Language:

In the example above, notice that we did not have to tell PHP which data type the variable is.

PHP automatically associates a data type to the variable, depending on its value. Since the data types are not set in a strict sense, you can do things like adding a string to an integer without causing an error.

In PHP 7, type declarations were added. This gives an option to specify the data type expected when declaring a function, and by enabling the strict requirement, it will throw a "Fatal Error" on a type mismatch.

You will learn more about `strict` and `non-strict` requirements, and data type declarations in the [PHP Functions](https://www.w3schools.com/php/php_functions.asp) chapter.

# Syntax:

```PHP
<!DOCTYPE html>
<html>
<body>

<?php //the code should be between this two dilimeiters
$txt = "Hello world!";
$x = 5; //variable declaration
$y = 10.5;

echo $txt;
echo "<br>";
echo $x; //to print the variables
echo "<br>";
echo $y;
?>

</body>
</html>
```

**output** 🏳️:

![[Untitled 28.png|Untitled 28.png]]

**Output Variables:**

```PHP
<?php
$txt = "hhh";
echo "I love $txt!"; //output: I love hhh!
?>
```

The following example will produce the same output as the example above:

```PHP
<?php
$txt = "W3Schools.com";
echo "I love " . $txt . "!";
?>
```

to get the sum of two variables:

```PHP
<?php
$x = 5;
$y = 4;
echo $x + $y;
?>
```

# **PHP Variables Scope:**

PHP has three different variables scopes:

- local
- global
- static

### Global and local scope:

a variable declared Outside a function has a **GLOBAL SCOPE** and can only be accessed outside a function:

```PHP
//variable with global scope
<?php
$x = 5; // global scope

function myTest() {
  // using x inside this function will generate an error
  echo "<p>Variable x inside function is: $x</p>";
}
myTest();

echo "<p>Variable x outside function is: $x</p>";
?>
```

a variable declared **within** a function has a **LOCAL SCOPE** and can only be accessed within that function:

```PHP
<?php
function myTest() {
  $x = 5; // local scope
  echo "<p>Variable x inside function is: $x</p>";
}
myTest();

// using x outside the function will generate an error
echo "<p>Variable x outside function is: $x</p>";
?>
```

## PHP the `global` keyword

The `global` keyword is used to access a global variable from within a function.

```PHP
<?php
$x = 5;
$y = 10;

function myTest() {
  global $x, $y;
  $y = $x + $y;
}

myTest();
echo $y; // outputs 15
?>
```

PHP also stores all global variables in an array called `$GLOBALS[``_index_``]`.  
The  
`_index_` holds the name of the variable. This array is also accessible from within functions and can be used to update global variables directly.

The example above can be rewritten like this:

```PHP
<?php
$x = 5;
$y = 10;

function myTest() {
  $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
}

myTest();
echo $y; // outputs 15
?>
```

### PHP the `static` keyword:

Normally, when a function is completed/executed, all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.

```PHP
<?php
function myTest() {
  static $x = 0;
  echo $x;
  $x++;
}

myTest();
myTest();
myTest();
?>
```

## PHP `echo` and `print` statements:

`echo` and `print` are more or less the same. They are both used to output data to the screen.

The differences are small: `echo` has no return value while `print` has a return value of 1 so it can be used in expressions. `echo` can take multiple parameters (although such usage is rare) while `print` can take one argument. `echo` is marginally faster than `print`.

**php** `**echo**` **statement:**

The `echo` statement can be used with or without parentheses: `echo` or `echo().`

**display text:**The following example shows how to output text with the `echo` command (notice that the text can contain HTML markup):

```PHP
<?php
echo "<h2>PHP is Fun!</h2>";
echo "Hello world!<br>";
echo "I'm about to learn PHP!<br>";
echo "This ", "string ", "was ", "made ", "with multiple parameters.";
?>
```

**Display Variables**

the following example shows how to output text and variables with the `echo` statement:

```PHP
<?php
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
$x = 5;
$y = 4;

echo "<h2>" . $txt1 . "</h2>";
echo "Study PHP at " . $txt2 . "<br>";
echo $x + $y;
?>
```

## The php print statement:

The `print` statement can be used with or without parentheses: `print` or `print()`.

**Display Text**

The following example shows how to output text with the `print` command (notice that the text can contain HTML markup):

```PHP
<?php
print "<h2>PHP is Fun!</h2>";
print "Hello world!<br>";
print "I'm about to learn PHP!";
?>
```

The following example shows how to output text and variables with the `print` statement:

```PHP
<?php
$txt1 = "Learn PHP";
$txt2 = "W3Schools.com";
$x = 5;
$y = 4;

print "<h2>" . $txt1 . "</h2>";
print "Study PHP at " . $txt2 . "<br>";
print $x + $y;
?>
```

## **PHP Data Types**

Variables can store data of different types, and different data types can do different things.  
PHP supports the following data types:  

- String
- Integer
- Float (floating point numbers - also called double)
- Boolean
- Array
- Object
- Null ($x = null;)
- Resource

In the following example $x is an integer. The PHP var_dump() function returns the data type and value:

```PHP
<?php
$x = 5985;
var_dump($x);
?>
```

**php Array:**

```PHP
<?php
$cars = array("Volvo","BMW","Toyota");
var_dump($cars);
?>
```

### **PHP Casting Strings and Floats to Integers**

Sometimes you need to cast a numerical value into another data type.  
The (int), (integer), or intval() function are often used to convert a value to an integer.  

```PHP
<?php
// Cast float to int
$x = 23465.768;
$int_cast = (int)$x;
echo $int_cast;

echo "<br>";

// Cast string to int
$x = "23465.768";
$int_cast = (int)$x;
echo $int_cast;
?>
```

**constants:**

```PHP
<?php
define("GREAT", "hello world");
echo GREAT;
?>
```

Create a constant with a **case-insensitive** name:

```PHP
<?php
define("GREAT", "hello world", true);
echo great;
?>
```

**create arrays of constants:**

In PHP7, you can create an Array constant using the `define()` function.

```PHP
<?php
define("cars", [
  "Alfa Romeo",
  "BMW",
  "Toyota"
]);
echo cars[0];
?>
```

# Operators:

## PHP Arithmetic Operators

The PHP arithmetic operators are used with numeric values to perform common arithmetical operations,  
such as addition, subtraction, multiplication etc.  

|Operator|Name|Example|Result|
|---|---|---|---|
|+|Addition|$x + $y|Sum of $x and $y|

|   |   |   |   |
|---|---|---|---|
|-|Subtraction|$x - $y|Difference of $x and $y|
|*|Multiplication|$x * $y|Product of $x and $y|
|/|Division|$x / $y|Quotient of $x and $y|
|%|Modulus|$x % $y|Remainder of $x divided by $y|
|**|Exponentiation|$x ** $y|Result of raising $x to the $y'th power|

---

## PHP Assignment Operators

The PHP assignment operators are used with numeric values to write a value to a variable.

The basic assignment operator in PHP is "=". It means that the left operand gets set to the value of the assignment expression on the right.

|Assignment|Same as...|Description|
|---|---|---|
|x = y|x = y|The left operand gets set to the value of the expression on the right|

|   |   |   |
|---|---|---|
|x += y|x = x + y|Addition|
|x -= y|x = x - y|Subtraction|
|x *= y|x = x * y|Multiplication|
|x /= y|x = x / y|Division|
|x %= y|x = x % y|Modulus|

## **PHP Comparison Operators**

The PHP comparison operators are used to compare two values (number or string):

|Operator|Name|Example|Result|
|---|---|---|---|
|==|Equal|$x == $y|Returns true if $x is equal to $y|

|   |   |   |   |
|---|---|---|---|
|===|Identical|$x === $y|Returns true if $x is equal to $y, and they are of the same type|
|!=|Not equal|$x != $y|Returns true if $x is not equal to $y|
|<>|Not equal|$x <> $y|Returns true if $x is not equal to $y|
|!==|Not identical|$x !== $y|Returns true if $x is not equal to $y, or they are not of the same type|
|>|Greater than|$x > $y|Returns true if $x is greater than $y|
|<|Less than|$x < $y|Returns true if $x is less than $y|
|>=|Greater than or equal to|$x >= $y|Returns true if $x is greater than or equal to $y|
|<=|Less than or equal to|$x <= $y|Returns true if $x is less than or equal to $y|
|<=>|Spaceship|$x <=> $y|Returns an integer less than, equal to, or greater than zero, depending on  <br>if $x is less than, equal to, or greater than $y. Introduced in PHP 7.|

## **PHP Increment / Decrement Operators**

The PHP increment operators are used to increment a variable's value.

The PHP decrement operators are used to decrement a variable's value.

|   |   |   |
|---|---|---|
|Operator|Name|Description|
|++$x|Pre-increment|Increments $x by one, then returns $x|

|   |   |   |
|---|---|---|
|$x++|Post-increment|Returns $x, then increments $x by one|
|--$x|Pre-decrement|Decrements $x by one, then returns $x|
|$x--|Post-decrement|Returns $x, then decrements $x by one|

## PHP Logical Operators

The PHP logical operators are used to combine conditional statements.

|   |   |   |   |
|---|---|---|---|
|Operator|Name|Example|Result|
|and|And|$x and $y|True if both $x and $y are true|

|   |   |   |   |
|---|---|---|---|
|or|Or|$x or $y|True if either $x or $y is true|
|xor|Xor|$x xor $y|True if either $x or $y is true, but not both|
|&&|And|$x && $y|True if both $x and $y are true|
|\||Or|$x \| $y|True if either $x or $y is true|
|!|Not|!$x|True if $x is not true|

## **PHP String Operators**

PHP has two operators that are specially designed for strings.

|   |   |   |   |
|---|---|---|---|
|Operator|Name|Example|Result|
|.|Concatenation|$txt1 . $txt2|Concatenation of $txt1 and $txt2|

|   |   |   |   |
|---|---|---|---|
|.=|Concatenation assignment|$txt1 .= $txt2|Appends $txt2 to $txt1|

## **PHP Array Operators**

The PHP array operators are used to compare arrays.

|   |   |   |   |
|---|---|---|---|
|Operator|Name|Example|Result|
|+|Union|$x + $y|Union of $x and $y|

|   |   |   |   |
|---|---|---|---|
|==|Equality|$x == $y|Returns true if $x and $y have the same key/value pairs|
|===|Identity|$x === $y|Returns true if $x and $y have the same key/value pairs in the same order and of the same types|
|!=|Inequality|$x != $y|Returns true if $x is not equal to $y|
|<>|Inequality|$x <> $y|Returns true if $x is not equal to $y|
|!==|Non-identity|$x !== $y|Returns true if $x is not identical to $y|

## **PHP Conditional Assignment Operators**

The PHP conditional assignment operators are used to set a value depending on conditions:

|   |   |   |   |
|---|---|---|---|
|Operator|Name|Example|Result|
|?:|Ternary|$x = _expr1_ ? _expr2_ : _expr3_|Returns the value of $x.The value of $x is _expr2_ if _expr1_  <br>= TRUE.  <br>The value of $x is _expr3_ if _expr1_ = FALSE|

|   |   |   |   |
|---|---|---|---|
|??|Null coalescing|$x = _expr1_ ?? _expr2_|Returns the value of $x.The value of $x is _expr1_ if _expr1_  <br>exists, and is not NULL.  <br>If _expr1_ does not exist, or is NULL, the value of $x is  <br>  <br>_expr2_.Introduced in PHP 7|

# PHP `if…else…elseif` Statements

```PHP
<?php
if (condition) {
  code to be executed if this condition is true;
} elseif (condition) {
  code to be executed if first condition is false and this condition is true;
} else {
  code to be executed if all conditions are false;
}
?>
```

`switch` :

This is how it works: First we have a single expression _n_ (most often a  
variable), that is evaluated once. The value of the expression is then compared with the values for each case in the structure. If there is a match, the block of code associated with that case is executed. Use  
`break` to prevent the code from running into the next case automatically. The `default` statement is used if no match is found.

```PHP
switch (n) {
  case label1:
    code to be executed if n=label1;
    break;
  case label2:
    code to be executed if n=label2;
    break;
  case label3:
    code to be executed if n=label3;
    break;
    ...
  default:
    code to be executed if n is different from all labels;
}
```

# PHP Loops:

```PHP
while (condition is true) {
  code to be executed;
}
/******************************/
do {
  code to be executed;
} while (condition is true);
/******************************/
for (init counter; test counter; increment counter) {
  code to be executed for each iteration;
}
/*****************************/
foreach ($array as $value) {
  code to be executed;
}
```

we can also use `break` and `continue` on this loops.

# Functions:

```PHP
function functionName(args) {
  code to be executed;
}
```

```PHP
<?php declare(strict_types=1); // strict requirement

function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is enabled and "5 days" is not an integer, an error will be thrown
?>
```

```PHP
<?php declare(strict_types=1); // strict requirement
function sum(int $x, int $y) {
  $z = $x + $y;
  return $z;
}

echo "5 + 10 = " . sum(5, 10) . "<br>";
echo "7 + 13 = " . sum(7, 13) . "<br>";
echo "2 + 4 = " . sum(2, 4);
?>
```

## **Passing Arguments by Reference:**

In PHP, arguments are usually passed by value, which means that a copy of the value is used in the function and the variable that was passed into the function cannot be changed.  
When a function argument is passed by reference, changes to the argument also change the variable that was passed in. To turn a function argument into a reference, the  
`&` operator is used:

```PHP
<?php
function add_five(&$value) {
  $value += 5;
}

$num = 2;
add_five($num);
echo $num;
?>
```

## PHP Associative Arrays

Associative arrays are arrays that use named keys that you assign to them.  
There are two ways to create an associative array:  

```PHP
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
//or
$age['Peter'] = "35";
$age['Ben'] = "37";
$age['Joe'] = "43";

<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";
?>
```

**loop through an associative array:**

```PHP
<?php
$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach($age as $x => $x_value) {
  echo "Key=" . $x . ", Value=" . $x_value;
  echo "<br>";
}
?>
```