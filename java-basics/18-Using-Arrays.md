---
layout: page
title: Using Arrays
description: Idioms and methods for array
---
### Loops for Processing Array Elements

You often want to process every element in an array.
The typical logic is:
```
initialize variables and values

foreach element in array
{
    process this element
}

compute the result
```
Here are 3 kinds of loops for arrays.

#### 1. "for" loop with index

This loop is useful if you need to know the index of the array element,
or you don't want to process every element.  The syntax is:
```
for(int index=start; test_condition; increment_operation) {
   statements for loop
}
```
**Example**: print the index and the array element value.
```java
double[] array = /* some array of values */;
for(int k=0; k<array.length; k++) {
    System.out.printf("[%d] = %f\n", k, array[k]);
```

**Example**: Sum the squares of values in an array.
```java
double[] array = /* some array of values */;
double sumSquares = 0; // initialization
for(int k=0; k<array.length; k++) {
    sumSquares += array[k]*array[k];
}
```
**Example**: evaluate this polynomial
![a_{n}x^{n}+a_{n-1}x^{n-1}+...+a_{0}](https://latex.codecogs.com/gif.latex?a_{n}x^{n}&plus;a_{n-1}x^{n-1}&plus;...&plus;a_{0})
where the array `a[]` contains coefficients of a polynomial. `a[]={5,10}` means the polynomial 5*x + 10.

The efficient way to compute this is **not** to compute powers of x.
Compute the polynomial like this:
```java
(((a[n]*x + a[n-1])*x + ... + a[1])*x + a[0]
```
A "for" loop that computes this starts from the last element of `a[]`:
```java
double poly = 0;
for(int k=a.length-1; k>=0; k--) poly = poly*x + a[k];
```
This shows how a "for" loop can run from high value (n) to low value (0).

#### 2. for-each loop

If you want to process all the elements in an array and don't need
to know the *index* of each element, use a for-each loop.
The syntax is:
```
for( Datatype x : array )  { ... }
```
The `Datatype` should be the type of elements in the array, and `x` is the name of the loop variable (anything you like).

**Example:** sum squares of array elements using a for-each loop
```java
double[] array = /* some array */;
double sumSquares = 0;
// "foreach x in array"
for(double x: array) {
    sumSquares += x*x;
}
```
The loop is much easier to read with the index (k).
Another example: print each element in an array of names.
```java
String[] animals = {"Cat", "Bird", "Horse" };
// "for-each who in names"
for(String who: animals) {
    System.out.println( who );
}
```

#### 3. while loop or do-while loop

These can also be used with arrays, of course.

---
### Useful Methods for Arrays

The [Arrays](https://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html) class in package `java.util` contains static methods for array operations.  You should use this class instead of writing the methods yourself!

#### Arrays.copyOf: copy an array to a new array

```java
String[] fruit = {"apple","banana","grape"};
// make a copy
String[] copy = Arrays.copyOf(fruit, fruit.length);
// make a copy of just 2 elements
String[] copy2 = Arrays.copyOf(fruit, 2);
```

#### System.arraycopy: copy array to an existing array

[System.arraycopy()](https://docs.oracle.com/javase/7/docs/api/java/lang/System.html#method_summary) lets you copy
any part of one array into any part of another array.
```java
// copy source[] array to dest[] array.
// You must make sure dest[] has enough space for copy.
System.arraycopy(source[], int start, dest[], int destStart, int length)
```
**Example**: copy each element of `a` to `b` starting at index 0:
```java
double[] a = {2, 4, 6, 8, 10};
double[] b = new double[5];    // same size as a
System.arraycopy(a, 0, b, 0, a.length);
```

#### Sort an Array

Useful method can sort any array of any type that is *Comparable*, 
which includes all numeric types, Strings, Dates, and many more.
It sorts the array in place.
```java
String[] words = {"cat", "ZEBRA", "frog", "bird"};
Arrays.sort(words);
System.out.println( Arrays.toString(words) );
```
prints:
```
["ZEBRA", "bird", "cat", "frog"]
```
ZEBRA is first because UPPERCASE come before lowercase letters!

#### Print an Array as a String

Useful for testing:
```
double[] a = {5,10,3.0E8};
System.out.println("a=" + Arrays.toString(a));
```
prints
```
a=[5, 10, 3.0E8]
```

#### Arrays.fill: set all array values at once

To fill all elements on an array with a constant, use:
```java
double[] x = new double[10];
Arrays.fill(x, 1.0); 
// sets x[0] = x[1] = x[2] = ... = 1.0
```
You can fill just part of the array by specifying extra parameters.




