---
comments: "false"
---
# MakerClub - 3D Printed Art

https://makerclub.netlify.app/

An experimental series of sessions to make 3D printed sculpture for display at school using SolidPython & OpenSCAD.

---
## [OpenSCAD - The Programmers Solid 3D CAD Modeller](https://openscad.org/)

Write code - Make shapes - Print things

![[Pasted image 20250226140046.png|800]]

---
## Play with the OpenSCAD examples


---

## [SolidPython](https://github.com/jeff-dh/SolidPython/wiki)

Write Python - Make shapes - Print things
```python
from solid2 import cube, sphere
c = cube([10, 20, 30])
s = sphere(10)
d = c - s
d.save_as_scad()
```

![[Pasted image 20250226141537.png|400]]

note:
SolidPython is a tool for creating 3D CAD models using Python and OpenSCAD. Creating 3D CAD models using Python can be simple, fast, and powerful.

---

## Simple App for making Key Chains

[Solid Design Live](https://soliddesign.streamlit.app/)  [UTCSheffield/solid_design: Simple Streamlit frontend for solidpython widget maker](https://github.com/UTCSheffield/solid_design)


---

## Try SolidPython

- Open Visual Studio Code
- Create new file
- Paste in the doe and run it

```python
from solid2 import cube, sphere
c = cube([10, 20, 30])
s = sphere(10)
d = c - s
d.save_as_scad()
```

---
## Basic Tutorials

- Find OpenSCAD Designs on [Printables](https://www.printables.com/search/models?q=tag:openscad) and [Thingiverse](https://www.thingiverse.com/tag:openscad)
- [OpenSCAD - Documentation](https://openscad.org/documentation.html#tutorial)
- [SolidPython Wiki](https://github.com/jeff-dh/SolidPython/wiki)

---

## Code Ideas - Shape along a path


```python
#! /usr/bin/env python
from solid2.extensions.bosl2 import circle
path = [ [0, 0, 0], [33, 33, 33], [66, 33, 40], [100, 0, 0], [150,0,0] ]

assembly = circle(r=10, _fn=6).path_extrude(path)
assembly.save_as_scad()
```

![[Pasted image 20250226150506.png]]


---

## Code Ideas - Height map


```python
#! /usr/bin/env python
from solid2.extensions.bosl2 import heightfield
def get_data():
    from math import sqrt,sin
    data = []
    for y in range(50):
        yrow = []
        data.append(yrow)
        for x in range(50):
            yrow.append(sin(sqrt((y-25)**2+(x-25)**2)))
    return data

assembly = heightfield(size=[100,100], bottom=-1, data=get_data())
assembly.save_as_scad()
```
![[Pasted image 20250226150345.png]]

---

## Barbara Hepworth - Yorkshire Sculptor

<iframe src="https://hepworthwakefield.org/whats-on/the-hepworth-family-gift-hepworth-at-work/" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>

note:
https://hepworthwakefield.org/whats-on/the-hepworth-family-gift-hepworth-at-work/


---

## Car

```python
#! /usr/bin/env python
from solid2 import cylinder, cube

def wheel():
    return cylinder(r=35, h=15, center=True).rotate(0, 90, 0)

def axle():
    a = cylinder(r=10, h=120, center=True).rotate(0, 90, 0)
    w1 = wheel().left(70)
    w2 = wheel().right(70)
    return w1 + w2 + a

def chasis():
    bottom = cube(100, 250, 50, center=True)
    top = cube(80, 100, 60, center=True)
    window_cube = cube(200, 55 ,50, center=True).down(10)
    top -= (window_cube + window_cube.rotate(0, 0, 90))
    return bottom + top.up(50)

def car():
    c = chasis()
    front_axle = axle().down(20).back(80)
    rear_axle = axle().down(20).forward(80)
    return c + front_axle + rear_axle

car().save_as_scad()
```


![[Pasted image 20250227112234.png]]



---

# Next Week
[[Session 2 - Write Code]]