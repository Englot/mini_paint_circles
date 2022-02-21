# mini_paint-circles
ASCII art. A program that will read a configuration-file that contains circle parameters to produce a "painting" that is displayed in the terminal using characters.

## Table of contents
* [Introduction](#introduction)
* [Requirements](#requirements)
* [Launch](#launch)

## Introduction
Inspired by the 42 coding school exercise "mini_paint" (November 2021).

### Allowed functions
fopen, fread, fscanf, fclose, write, malloc, calloc, realloc, free, memset, powf, sqrtf

### Aim
The aim of the exercise is to write a program that will read a "configuration-file" and display the result in the terminal.

The program must take one argument, the path to the "configuration-file".
If the number of arguments doesn't meet these requirements the program must display "Error: argument" followed by a newline in STDOUT.

If any problem occure while you opening or reading the "configuration-file" the program must display "Error: Operation file corrupted" followed by a newline in STDOUT.

The "configuration-file" will contain one operation per line.
If a line is incorrect an error occurs.
If an error has occured the program must return 1.
If no error has occured it must return 0.
The last line of the "configuration-file" can be with or without a newline.
The lines must be read in order and the operations must be executed in the same order.
There must be at least one space between each variable in a line.


The first line of the file defines the drawing zone. The program should not display anything outside of it. The format is as follows:
__WIDTH HEIGHT CHAR__
* WIDTH: The horizontal number of characters to use for the draw zone. An int that has to be bigger than 0 and smaller or equal to 300.
* HEIGHT: The vertical number of characters to use for the draw zone. An int that has to be bigger than 0 and smaller or equal to 300.
* CHAR: The char used to fill the drawing zone (background).

The following lines of the file define the circles to be drawn. The format is as follows:
__TYPE X Y RADIUS CHAR__
This operation will draw a empty circle, where only the border of the circle is drawn
* TYPE: Type of circle to be drawn. Two options are possible: 'c' or 'C'. Character 'c' stands for an empty circle (only the border of the circle is drawn). Whereas the character 'C' stands for a filled circle.
* X: The horizontal position of the center of the circle. It is of type float.
* Y: The vertical position of the center of the circle. It is of type float.
* RADIUS: The radius of the circle. A float bigger than 0.
* CHAR: The char used to draw the circle.

The draw zone is divided in rectangles that can contain one character each. They can be seen as "pixels".
Only the top left corner of the "pixels" will be used as point of reference to determine its position. If the distance between the top left corner of a "pixel" and the center of a circle is lower or equal to the radius of the circle, the pixel is part of the circle.

A "pixel" with a top left corner with a distance bigger or equal to 1 from the border of a circle is not part of an empty circle.

A "pixel" with a top left corner with a distance lower than 1 from the border of a circle is part of an empty circle.

The distance between two points (Xa,Ya) and (Xb,Yb) can be calculated like this: srqt((Xa - Xb) * (Xa - Xb) + (Ya - Yb) * (Ya - Yb))
	
## Requirements
* gcc
	
## Launch
Compile the program as follows (using the "-lm" flag to link "<math.h>"):

```
$ gcc mini_paint.c -lm
```
Run it by giving it the path to the configuration-file as argument (in this case the file "blueprint2" within the directory "examples"):

```
$ ./a.out examples/blueprint2
```

## Example
![grafik](https://user-images.githubusercontent.com/80413516/154933714-7e821380-b55b-4b4d-ae9b-b2a1776e1e48.png)
_Screenshot of the terminal output using the example configuration-file "blueprint2"_
