# opengl-glew

Bindings to OpenGL with GLEW extension loading. This egg should work (at least) on Linux, OS X, Windows, and on OpenGL ES platforms.

Chicken's other [opengl](http://wiki.call-cc.org/eggref/4/opengl) bindings are based on the old fixed function pipeline OpenGL. These bindings generated by [bind](http://wiki.call-cc.org/eggref/4/bind) with the OpenGL [core header file](http://www.opengl.org/registry/api/GL/glcorearb.h). Additionally, bindings to [GLEW](http://glew.sourceforge.net/) are provided for extension management.

This egg can also be compiled to provide bindings for OpenGL ES. This will be done automatically when compiled on ARM systems, or with the feature `gles` (e.g. `chicken-install -D gles`).

## Installation
This repository is a [Chicken Scheme](http://call-cc.org/) egg.

It is part of the [Chicken egg index](http://wiki.call-cc.org/chicken-projects/egg-index-4.html) and can be installed with `chicken-install opengl-glew`.

## Requirements
- make
- bind

## Documentation
All functions and constants from the OpenGL [core header file](http://www.opengl.org/registry/api/GL/glcorearb.h) are exported. Scheme style names are provided (underscores and camelCase replaced with hyphens), the `gl` prefix is removed from names, functions starting with `is` instead end in question marks, and constants are bookended by `+`s (e.g. `delete-texture`, `enabled?`, `+arb-viewport-array+`). The terms `1D`, `2D` and `3D` are additionally hyphen separated in order to match their constant counterparts (e.g. `tex-image-2d` and `+texture-2d+`).

Functions whose C counterparts accept or return `GLboolean` accept or return a Scheme boolean value. *Do not* pass `+true+` or `+false+` to these functions.

### GLEW functions

    [procedure] (init)

Required to initialize GLEW/OpenGL. An OpenGL context must be created before this is called.

    [procedure] (supported? EXTENSION-NAME)

Query whether the OpenGL extension, given as a string, is supported.

## Example
For numerous examples of opengl-glew usage, look at the [gl-utils](http://wiki.call-cc.org/eggref/4/gl-utils) egg, [glls](http://wiki.call-cc.org/eggref/4/glls) egg, or the [noise](http://wiki.call-cc.org/eggref/4/noise) egg.

## Version history
### Version 0.9.0
28 November 2014

* Add support for OpenGL ES
* Fixes for Windows

### Version 0.8.0
24 August 2014

* Split [gl-utils](http://wiki.call-cc.org/eggref/4/gl-utils) into its own egg
* Hyphen-separate `2D`, `3D`, and `4D` in name conversion

### Version 0.7.0
8 August 2014

* Export `->pointer`, `size`
* Improve shader error messages

### Version 0.6.0
17 June 2014

* Remove gl-math module (which is now its own egg: [gl-math](http://wiki.call-cc.org/eggref/4/gl-math))

### Version 0.5.0
3 June 2014

* `make-vao` accepts vectors and blobs
* `load-ply` returns u8vectors rather than blobs
* gl-utils exports a non-garbage collected by default version of srfi-4
* gl-math can create non-garbage collected matrices

### Version 0.4.4
2 June 2014

* `load-ply-vao` now returns buffer data (which is important to keep around!)

**Version 0.4.3**

30 May 2014

* Add optional program argument to `make-program`
* gl-math short-circuits rotations of 0

**Version 0.4.2**

24 May 2014

* Fix segfaults caused by glewExperimental not being set (thanks, Terpri!)

**Version 0.4.1**

12 May 2014

* Remove rogue print statement

**Version 0.4.0**

11 May 2014

* Add gl-math module
* Add gl-utils module
* Add `check-error`

### Version 0.3.0
* Add single element `gen` and `delete` functions

### Version 0.2.0
* Add glcorearb.h - no longer downloaded at install time

### Version 0.1.0
* Initial release

## Source repository
Source available on [GitHub](https://github.com/AlexCharlton/chicken-opengl-glew).

Bug reports and patches welcome! Bugs can be reported via GitHub or to alex.n.charlton at gmail.

## Author
Alex Charlton

## Licence
BSD
