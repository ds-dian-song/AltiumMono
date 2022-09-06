# Altium Mono
## An (unofficial) TrueType font family based on JetBrains Mono to create better-looking copper layer in Altium Designer

### How to use this repository
This repo is currently WIP. If you happen to understand what I am doing without me explaining, you can:
- Install on your Windows machine the fonts from the latest build folder.
- Use Altium Mono Regular for Copper Layer (Text height = 1mm)
- Use Altium Mono Bold for Solder Mask Layer (Text height = 1mm)
- Use Altium Mono Extrabold for Copper layer (Text height = 1mm, inverted)
- Adjust rules to allow 0 mm text-polygon clearance; Allow Short circuit between text and all nets.
- Please use query language to create and manage specific rules.
- Please limit its use to one-off projects to avoid long-term maintenance headache.
- Write a poem on your piece of PCB and get it fabricated.

### Some Pictures
![Demonstration 2D](/Images/Demo1.jpg)
![Demonstration 3D](/Images/Demo1-1.jpg)

### What I am currently working on 
- Optimizing this Github repo (README page, links and pictures, Release page, License, etc.)
- Writing a Python script for automating some of the FontForge methods explained below
- Convert more fonts!
- Adding commonly used glyphs (*e.g.* UL, RoHS, Open Source Hardware, diodes) to the TrueType font package, and ship a copy-paste list for it. 
- Guidelines to embed Logos & other vector graphics in a custom font based on an arbitrary existing font.
- Test print something and release photos!
- More Altium tips, tricks, and hacks.

### Other Notes
- I am assuming typical trace/width 5mil/5mil (OSHPark) and 3.5mil/3.5mil (JLCPCB)
- Solder Mask Expansion to be 0.05mm
- Minimum silkscreen width to be 6mil
- Typical text height 1mm, 1.27mm, 2.54mm, 5.08mm


### Motivation
- Tired of using Adobe Illustrator to handle "texts" as graphics work for each board
- Explore a solution that could potentially work across many projects (and other people's projects, of course)
- Better typography for PCB as a print medium (to an extent, after all functionality, cost of production and engineering requirements override graphical preferences)
- Create a decent-looking PCB business card as a show-off.

### Observation 
#### "1 mm" Text will never be 1 mm, why?
- Without access to the source implementation, I can only observe the behavior as a user. 
- Good news: actual text height scales linearly with speicifed text height.
- f(L,H), where L is pixel length in TrueType source file, and H, specified text height in Altium Designer.
#### What kind of correlation is out there?
- Conclusion: For TrueType Fonts with em size of 1000 the text height is (L / 1000 * 0.7553 * H) mm, where L is pixel length in the 1000x1000 em box, and H is the input of text height in Altium Designer. This formular works for H > 0.125mm, which seems to be the minimum textbox height in Altium.
- This conclusion is, obviously, a brute force engineering solution to approach the problem. It works, but would be better if fully understand how Altium handles TrueType fonts under the hood.
### Solving this Problem with Altium's Default Stroke Font
#### Advantages
- Looks great and very compatible with Altium Designer's way of handling texts/primitives
#### Disadvantages
- Limited choice of typefaces
- Limited special symbols
- It can be better
### Solving this Problem with Adobe Illustrator
#### Advantages
- Content is saved as an Altium primitive (regions) and thus portable across systems
- True "polygon pour" look around typographical elements.
#### Disadvantages
- Requires subscription of Illustrator (TODO: repeat the same method in Inkscape)
- Grainy texture, usually not a big issue when you get the board fabricated. But think about it, Altium supports importing images at maximum 1200 dpi. 1200 may sound like a lot, but it is only 47 pixels per 1 mm. 
- High fidelity graphics costs compile time during polygon repour.
- A lot of calculations if a standard approach is not establish *a priori*. 
- Repetitive task.
- Not possible to dynamically change the content. To accomodate any change, you have to do it again.

### Solving this Problem with Custom TrueType Fonts
#### What is TrueType Font, Exactly?
#### Advantages
#### Disadvantages





### Known Limitations
- Have to generate and install new typeface and install for each new typeface/fab capabilities
- If sharing the project to multiple machines, typeface have to be installed on each.
- Must follow best practice and save the typeface in dedicated project folder.
- Ligature and kerning 
### Related Projects
My own:

- Will slowly release more PCB / Altium related stuff to Github

Public:
- [Scalable Graphics in the PCB Editor](https://forum.live.altium.com/#/posts/61899) by Darren Moore 

### Typography Tutorial and References
- Coursera stuff
- Youtube stuff
- My working guidelines & conventions

### Licenses 
Altium Mono was created based on JetBrains Mono, a monospace technical typeface for developers.
There is no restrictions on your use of the content in this repository. However, I as the author accept no liability. (TODO: )