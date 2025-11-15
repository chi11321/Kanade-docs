# 🔢 math

## Functions:

### abs

`math.abs(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the absolute value of x.

### acos

`math.acos(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the arc cosine of x (in radians).

### asin

`math.asin(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the arc sine of x (in radians).

### atan

`math.atan(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the arc tangent of x (in radians).

### atan2

`math.atan2(x: number, y: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr><tr><td>y</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the arc tangent of y/x (in radians), but uses the signs of both parameters to find the quadrant of the result. (It also handles correctly the case of x being zero.)

### ceil

`math.ceil(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the smallest integer larger than or equal to x.

### clamp

`math.clamp(value: number[, min: number, max: number]):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>value</td><td>number</td><td>The value to clamp</td></tr><tr><td>min</td><td>number</td><td>The minimum value</td></tr><tr><td>max</td><td>number</td><td>The maximum value</td></tr></tbody></table>

Returns the clamped value.

### cos

`math.cos(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the cosine of x (assumed to be in radians).

### cosh

`math.cosh(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the hyperbolic cosine of x.

### deg

`math.deg(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the angle x (given in radians) in degrees.

### exp

`math.exp(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the value e power x.

### floor

`math.floor(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the largest integer smaller than or equal to x.

### fmod

`math.fmod(x: number, y: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr><tr><td>y</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the remainder of the division of x by y that rounds the quotient towards zero.

### frexp

`math.frexp(x: number):` <mark style="color:purple;">`number`</mark>, <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

$$
x = m2^e
$$

Returns `m` and `e` such that `x = m2e`, `e` is an integer and the absolute value of `m` is in the range `[0.5, 1)` (or zero when `x` is zero).

### ldexp

`math.ldexp(x: number, e: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr><tr><td>e</td><td>number</td><td>Number</td></tr></tbody></table>

$$
output = m2^e
$$

Returns `m2e` (e should be an integer).

### log

`math.log(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the natural logarithm of x.

### log10

`math.log10(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the base-10 logarithm of x.

### map

`math.map(value: number, in_from: number, in_to: number, out_from: number, out_to: number[, should_clamp: boolean]):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>value</td><td>number</td><td>The value to map</td></tr><tr><td>in_from</td><td>number</td><td>In minimum value</td></tr><tr><td>in_to</td><td>number</td><td>In maximum value</td></tr><tr><td>out_from</td><td>number</td><td>Out minimum value</td></tr><tr><td>out_to</td><td>number</td><td>Out maximum value</td></tr><tr><td>should_clamp</td><td>number</td><td>Clamp <code>In</code> range</td></tr></tbody></table>

Linearly maps two number ranges and returns the mapped value.

### max

`math.max(x: number[, ...]):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr><tr><td><strong>...</strong></td><td></td><td>Comma-separated numbers to concatenate with <code>x</code></td></tr></tbody></table>

Returns the maximum value among its arguments.

### min

`math.min(x: number[, ...]):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr><tr><td><strong>...</strong></td><td></td><td>Comma-separated numbers to concatenate with <code>x</code></td></tr></tbody></table>

Returns the minimum value among its arguments.

### modf

`math.modf(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns two numbers, the integral part of x and the fractional part of x.

### pow

`math.pow(x: number, y: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr><tr><td>y</td><td>number</td><td>Number</td></tr></tbody></table>

Returns x^y. (You can also use the expression x^y to compute this value.)

### rad

`math.rad(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the angle x (given in degrees) in radians.

### random

`math.random([m [, n]]):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>m</td><td>number</td><td>Number</td></tr><tr><td>n</td><td>number</td><td>Number</td></tr></tbody></table>

This function is an interface to the simple pseudo-random generator function rand provided by ANSI C.When called without arguments, returns a uniform pseudo-random real number in the range \[0,1). When called with an integer number m, math.random returns a uniform pseudo-random integer in the range \[1, m]. When called with two integer numbers m and n, math.random returns a uniform pseudo-random integer in the range \[m, n].

### randomseed

`math.randomseed(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Sets x as the "seed" for the pseudo-random generator: equal seeds produce equal sequences of numbers.

### sin

`math.sin(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the sine of x (assumed to be in radians).

### sinh

`math.sinh(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the hyperbolic sine of x.

### sqrt

`math.sqrt(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the square root of x. (You can also use the expression x^0.5 to compute this value.)

### tan

`math.tan(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the tangent of x (assumed to be in radians).

### tanh

`math.tanh(x: number):` <mark style="color:purple;">`number`</mark>

<table><thead><tr><th width="170.08022516342308">Name</th><th width="150">Type</th><th width="395.7341676883734">Description</th></tr></thead><tbody><tr><td>x</td><td>number</td><td>Number</td></tr></tbody></table>

Returns the hyperbolic tangent of x.

## Variables:

### huge

`math.huge:` <mark style="color:purple;">`number`</mark>

The value HUGE\_VAL, a value larger than or equal to any other numerical value.

### pi

`math.pi:` <mark style="color:purple;">`number`</mark>

The value of pi.
