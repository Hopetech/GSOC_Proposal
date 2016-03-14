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

 The goal of this project is to implement a library of double precision operations in pure [GLSL](https://www.opengl.org/documentation/glsl/) 1.30 for GPU.

## Constraints

Main Mesa code is under MIT license. So it's important to use only compatible license like BSD style license.


## Deliverables

- Implement following functions using bit twiddling operations:
    - Add.    
    - Negate.
    - Absolute value.
    - Multiply.
    - Convert to single precision.
    - Convert from single precision.
    - Comparison


- Nice to have:
    - Sqrt.
    - Log.
    - Exp.

## Schedule

For each implemented function, I will make tests, documentation and then I'll submit my code to the community.


- **Before coding period**:
    - Study current CPU "soft" double precision floating point library to familiarize myself with bit twiddling.
    - During this period I will remain in constant touch with my mentor and the all the Mesa community.


- **May 23rd - May 29th**:
    - Design tests.
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
    - Implement conversion from single precision.


- **July 18th - July 24th**:      
    - Implement comparison.


- **July 25th - July 31st**:
    - Implement log function.


- **August 1st - August 7th**:  
    - Implement exponential function.


- **August 8th - August 14th**:
    - Clean code to comply with Mesa standards.
    - Time for unpredictable delay.


- **August 15th - August 22nd**:
    - Clean code to comply with Mesa standards.
    - Time for unpredictable delay.


- **August 23rd - August 29th**:
    - Final evaluation.

## What's next?

 A stretch goal would be to use this library of functions to implement `GL_ARB_gpu_shader_fp64` on all GPUs for which Mesa supports GLSL 1.30.
