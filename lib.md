---
layout: default
---
## Big Hex Standard Library
The Standard Library is automatically added to your program when you run it on the machine, it adds many useful functions. It may help you to browse the standard library source code to better understand what is happening. This page lists all methods that are currently available.

```x
proc delay();
```
Pauses execution for a short period of time.

```x
proc longdelay();
```
Pauses execution for a long period of time.

```x
proc verylongdelay();
```
Pauses execution for a very long period of time.

```x
proc displayBitmap(arr);
```
Copies the array parameter into the display buffer memory. The array should be at least 16 values long

```x
proc clearDisplay();
```
Writes `0`s to the display buffer setting all LEDs off

```x
proc memcpy(src, dst, size);
```
Copies `size` values from the `src` array to the `dst` array

```x
func mul(x,y);
```
Returns the result of `x * y`

```x
func div(x,y);
```
Returns the result of `x / y`

```x
func mod(x,y);
```
Returns `x % y`

```x
func lsh(x, n);
```
Returns `x` shifted left by `n` positions

```x
func rsh(x, n);
```
Returns `x` shifted right by `n` positions

```x
func abs(x);
```
Returns the absolute value of `x`

```x
func isOdd(x);
```
Returns `true` if `x` is odd

```x
func isEven(x);
```
Returns `true` if `x` is even

```x
proc sRand(x);
```
Initialises the random seed value to `x`

```x
proc genRand(x);
```
Returns a random number from `0`(inclusive) up to `x`(exclusive)

#### Alphabet
This family of functions is responsible for the bitmap alphabet. It is taken from this [16x16 Font](http://prettyuglycode.net/16X16.html). The alphabet contains upper and lower case letters, numbers as well as symbols for !, ?, @ and a smiley face (using the # character as X does not support unicode).

```x
func getBitmapForChar(c);
```
Returns an array containing the bitmap representation of the character `c`. The array is returned by reference so should be treated as READ ONLY. To get a mutable copy see `copyBitmapForChar`

```x
func copyBitmapForChar(c, arr);
```
Copies a representation of the character `c` into the passed `arr` array parameter

```x
proc initAlphabet()
proc initUpperCase();
proc initLowerCase();
proc initNumbers();
proc initSymbols();
```
These functions initialise the bitmap alphabet. The `initAlphabet` method simply calls the other 4 methods. If you only need part of the alphabet you can choose to only call the initialisation method you require, this reduces code size and means less time writing to RAM. Initialising a character is required in order to get it's bitmap representation using `getBitmapForChar` and `copyBitmapForChar`.
