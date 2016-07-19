* **Name:** Elie TOURNIER
* **Email:** tournier.elie@gmail.com

---
# "Soft" double precision floating point support.

_by Elie ([Hopetech](https://github.com/Hopetech)) TOURNIER, for GSoC 2016_

---

## 1. Organization

This project will take place with [X.org foundation](http://www.x.org/wiki/).
>The X.Org project "provides a free and open source implementation of the X Window System".

[Mesa3D](http://www.mesa3d.org/), a graphics library, is part of the X.org project.
>"Mesa is an open-source implementation of the OpenGL specification - a system for rendering interactive 3D graphics - which provide OpenGL support to users of X on Linux, FreeBSD and other operating systems."

During the "Google Summer of Code", I will contribute to Mesa by implementing a double precision floating point library.

## 2. Aims

GPUs natively support single precision, but only OpenGL 4.0 class GPUs have hardware support for double precision.
The goal of this project is to implement a library of double precision operations in pure [GLSL](https://www.opengl.org/documentation/glsl/) 1.30 for this GPU using bit twiddling operations and integer math.
There are many library of software double precision floating point for devices that lack floating-point hardware.
I should therefore translate one of this library (generally write in C) to pure GLSL 1.30.

## 3. Constraints

* [Main Mesa code is under MIT license](http://www.mesa3d.org/license.html). It will be important throughout the project period to only use compatible license files.
You can find a list of licenses [here](https://spdx.org/licenses/).
* The code must comply with the [Mesa coding style](http://www.mesa3d.org/devinfo.html#style).
* The code must be commented by respecting the [Mesa standard](http://www.mesa3d.org/sourcedocs.html).
* Each double precision value would be stored in a `uvec2`.

## 4. Deliverables

* A library with the following functions:
 * Add.
 * Negate.
 * Absolute value.
 * Multiply.
 * Reciprocal.
 * Convert to single precision.
 * Convert from single precision.
 * Comparison.
 
* Nice to have:
 * Rsqrt.
 * Log.
 * Exp.

These last functions are not necessary for the implementation of `GL_ARB_gpu_shader_fp64` ([see What's next section](#6-whats-next)) but may be useful for other uses.


## 5. Schedule

For each implemented function, I shall realize tests, documentation and then submit my code to the community for reviewing.

* **Before coding period**:
  * During this period I will remain in constant touch with my mentor and the all the Mesa community.
  * Study current CPU "soft" double precision floating point libraries to familiarize myself with bit twiddling operations.
  * Prepare tests architecture.

* **May 23rd - May 29th**:
  * Implement absolute value function.
```C
uvec2 abs_fp64(uvec2 a);
```

* **May 30th - June 5th**:
  * Implement add function.
```C
uvec2 add_fp64(uvec2 a, uvec2 b);
```

* **June 6th - June 12th**:
  * Implement negate function.
```C
uvec2 neg_fp64(uvec2 a);
```

* **June 13th - June 19th**:
  * Implement multiply function.
```C
uvec2 mul_fp64(uvec2 a, uvec2 b);
```

* **June 20th - June 26th**:
  * Mid-term evaluation.

* **June 27th - July 3rd**:
  * Implement conversion to single precision.
```C
uint fp64-to-fp32(uvec2 a);
```

* **July 4th - July 10th**:
  * Implement conversion from single precision.
```C
uvec2 fp32-to-fp64(uint a);
```

* **July 11th - July 17th**:
  * Implement comparison.
```C
/**
 * Returns `true` if the double-precision floating-point value `a' is equal to the
 * corresponding value `b', and `false` otherwise.
 */
bool eq_fp64(uvec2 a, uvec2 b);
/**
 * Returns true if the double-precision floating-point value `a' is less than or
 * equal to the corresponding value `b', and false otherwise.
 */
bool le_fp64(uvec2 a, uvec2 b);
/**
 * Returns true if the double-precision floating-point value `a' is less than
 * the corresponding value `b', and false otherwise.
 */
bool lt_fp64(uvec2 a, uvec2 b);
```

* **July 18th - July 24th**:
  * Port reciprocal and rsqrt from [NIR](https://github.com/Igalia/mesa/blob/i965-fp64/src/compiler/nir/nir_lower_double_ops.c) to GLSL 1.30.
```C
uvec2 recip_fp64(uvec2 a);
uvec2 rsqrt_fp64(uvec2 a);
```

* **July 25th - July 31st**:
  * Port floor, ceil and truncate from [NIR](https://github.com/Igalia/mesa/blob/i965-fp64/src/compiler/nir/nir_lower_double_ops.c) to GLSL 1.30.
```C
uvec2 floor_fp64(uvec2 a);
uvec2 ceil_fp64(uvec2 a);
uvec2 trunc_fp64(uvec2 a);
```

* **August 1st - August 7th**:
  * Time for unpredictable delay.

* **August 8th - August 14th**:
  * Time for unpredictable delay.

* **August 15th - August 22nd**:
  * Final evaluation.

## 6. What's next?

* Implement log and exponential functions. This can be done in August if I have enough time.
* A stretch goal would be to use this library of functions to implement `GL_ARB_gpu_shader_fp64` on all GPUs for which Mesa supports GLSL 1.30.

## 7. Student Information

### 7.1 Personal Information

* **Name:** Elie TOURNIER
* **Email:** tournier.elie@gmail.com
* **IRC:** Elie_
* **GitHub:** [GitHub](https://github.com/Hopetech/)
* **Linkedin:** [Linkedin](https://fr.linkedin.com/in/elietournier)
* **Resume:** [Resume](https://github.com/Hopetech/myResume/blob/master/CV_Elie.pdf)
* **Country:** France
* **Time zone:** GMT+1

### 7.2 Education

* **Engineering school:** Telecom Physique Strasbourg, France
* **Subject/Major:** Medical Information and Communication Technology (**Sandwich Course**)
* **Year:** Last year
 
### 7.3 Work Experience

I am currently working on the development of an image quality measurement software for a French medical X-ray sensors company named [Thales Electron Devices](https://www.thalesgroup.com/en/microwave-imaging-sub-systems/radiology). My code is written in C++ with [BOOST library](http://www.boost.org/). To build the software, I use [CMake](https://cmake.org/).

### 7.4 Summer Availability

* **Exams End Date:** 05/26/2016
* **Time Commitments:** I'm available all the summer. However, as I will be graduate in September, I will find work this summer which will take me some of my time. But the GSoC remains my main priority.

## 8. Why did I choose this subject?

I chose this subject for two reasons.
First because I want to contribute to something I daily use.
Secondly because GPU are the most beautiful component of the computer.
