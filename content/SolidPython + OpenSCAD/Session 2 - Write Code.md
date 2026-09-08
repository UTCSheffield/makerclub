# Session 2 - Write Code

### Note
Some of the clever BSOL stuff like height maps might take until next week before we can do them

---
## [SolidPython](https://github.com/jeff-dh/SolidPython/wiki) is Python

```python
#Stepped Pyramid
from solid2 import *
assembly = cube(0,0,0)
levels = 5
for i in range(0, levels):
    side = (i+1) * 2
    c = cube(side, side, 1)
    assembly +=  c.translate(-side/2, -side/2, (levels-i)-1)
    #assembly +=  c.up((levels-i)-1).left(side/2).back(side/2) # Does the same thing
assembly.save_as_scad()
```

![[Pasted image 20250305143303.png|250]]

#### Task : Try twisting the levels 

---

## Primitives

- square(size, center, r, x, y)
- cylinder(r, h, r1, r2, $fn, center)
- circle(r, $fn)
- polygon(points, paths, r)
- union(r)
- difference(r)
- intersection(r)
- translate(v, x, y, z)
- scale(v)
- rotate(a, v)
- linear_extrude(height, center, twist, scale, translate, r)
- pack(size, sep)
- shell(w)
- rotate_extrude(a, r, translate, rotate)
- unit(unit)

---

## Ideas

- Try lots of spheres
- Try alternating Adding and Subtracting things
- 

```python
from solid2 import *
assembly = cube(0,0,0)
levels = 5
for i in range(levels, 0, -1):
    side = (i+1) * 2
    c = cube(side, side, side/2).translate(-side/2, -side/2, (levels-i)-1)
    if (i % 2):
        assembly +=  c
    else:
        assembly -=  c
assembly.save_as_scad()
```

---

## Text and Input

This really is python, you can do everything including input and validation.
```python
from solid2 import *
valid = False

while not valid:
    name = input("What is your Name? ")
    valid = len(name) > 2 and len(name) < 10
length = (len(name) * 7.5) + 7.5
shape = cube(length, 12, 1) - text(text=name).translate(5, 1, 1)
shape -= cylinder(3,1,1,True).translate(2, 8, 0)
shape.save_as_scad()
```

![[Pasted image 20250306104132.png|300]]

---

## Simple App for making Key Fobs and other stuff

* [Solid Design Live](https://soliddesign.streamlit.app/) 
* [UTCSheffield/solid_design: Github](https://github.com/UTCSheffield/solid_design)

### Fork the repo 

### Play with the prototype.py code to try different shapes / ideas


---

## Basic Tutorials

- Find OpenSCAD Designs on [Printables](https://www.printables.com/search/models?q=tag:openscad) and [Thingiverse](https://www.thingiverse.com/tag:openscad)
- [OpenSCAD - Documentation](https://openscad.org/documentation.html#tutorial)
- [SolidPython Wiki](https://github.com/jeff-dh/SolidPython/wiki)

---
# Next Week
[[Session 3 - Make shapes]]