>**Name:** Elie TOURNIER

>**Email:** tournier.elie@gmail.com

>**Phone:** +33 6 37 41 44 96

>**Time zone:** GMT+1

---
# "Soft" double precision floating point support.

_by Elie (Hopetech) TOURNIER, for GSoC 2016_

---

## The organization

This project will take place with [X.org fundation](http://www.x.org/wiki/) , for [Mesa](http://www.mesa3d.org/), a graphics library.
The X.Org project "provides a free and open source implementation of the X Window System".

## Aims

GPUs natively support single precision, but only OpenGL 4.0 class GPUs have hardware support for double precision.
The goal of this project is to implement a library of double precision operations in pure [GLSL](https://www.opengl.org/documentation/glsl/) 1.30 for GPU using bit twiddling.
There are many library of software double precision floating point for devices that lack floating-point hardware.
I should therefore translate one of this library (generally write in C) to pure GLSL 1.30.

## Constraints

 - Main Mesa code is under MIT license. It will be important throughout the project period to only use compatible license files.
 You can find a list of licenses [here](https://spdx.org/licenses/).

 - Each double precision value would be stored in a `uvec2`.


## Deliverables

 - A library with the following functions:
    - Add.    
    - Negate.
    - Absolute value.
    - Multiply.
    - Convert to single precision.
    - Convert from single precision.
    - Comparison

- Nice to have:
    - Rsqrt.
    - Log.
    - Exp.

These last functions are not necessary for the implementation of `GL_ARB_gpu_shader_fp64` [see What's next section](#what's-next?) but may be useful for other uses.


## Schedule

For each implemented function, I will make tests, documentation and then I'll submit my code to the community for reviews.


- **Before coding period**:
    - Study current CPU "soft" double precision floating point libraries to familiarize myself with bit twiddling.
    - Prepare tests architecture.
    - During this period I will remain in constant touch with my mentor and the all the Mesa community.


- **May 23rd - May 29th**:
    - Implement absolute value function.


- **May 30th - June 5th**:
    - Implement add function.


- **June 6th - June 12th**:
    - Implement negate function.


- **June 13th - June 19th**:
    - Implement multiply function.


- **June 20th - June 26th**:
    - Mid-term evaluation.


- **June 27th - July 3rd**:
    - Implement conversion to single precision.


- **July 4th - July 10th**:
    - Implement conversion from single precision.


- **July 11th - July 17th**:
    - Implement comparison.


- **July 18th - July 24th**:      
    - Implement log function.


- **July 25th - July 31st**:
    - Implement exponential function.


- **August 1st - August 7th**:  
    - Convert reciprocal, sqrt, rsqrt, and floor/ceil/truncate from [Intel NIR](https://github.com/Igalia/mesa/blob/i965-fp64/src/compiler/nir/nir_lower_double_ops.c) to GLSL.


- **August 8th - August 14th**:
    - Clean code to comply with Mesa standards.
    - Time for unpredictable delay.


- **August 15th - August 22nd**:
    - Final evaluation.

## What's next?

 A stretch goal would be to use this library of functions to implement `GL_ARB_gpu_shader_fp64` on all GPUs for which Mesa supports GLSL 1.30.
