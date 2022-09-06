# Altium Mono
## A TrueType font family to create better-looking copper layer in Altium Designer

### This is project is still a working progress

### Motivation
- Tired of using Adobe Illustrator to handle "texts" as graphics work for each board
- Explore a solution that could potentially work across many projects (and benefit others, too)
- Better typography for PCB as a print medium (to an extent, after all functionality, cost of production and engineering requirements override graphical preferences)

### Observation 
#### "1 mm" Text will never be 1 mm, why?
- Without access to the source implementation, I can only observe the behavior as a user. 
- Good news: actual text height scales linearly with speicifed text height. 
- f(L,H), where L is pixel length in TrueType source file, and H, specified text height in Altium Designer.
#### What kind of correlation is out there?
- Conclusion: For TrueType Fonts with em size of 1000 the text height is (L / 1000 * 0.7553 * H) mm, where L is pixel length in the 1000x1000 em box, and H is the input of text height in Altium Designer.
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
#### Disadvantages
- Requires subscription of Illustrator (TODO: repeat the same method in Inkscape)
- Grainy texture, usually not a big issue when you get the board fabricated
- Too much steps, and have to repeat the same step for each project
- Not possible to dynamically change the content

### Solving this Problem with Custom TrueType Fonts
#### What is TrueType Font, Exactly?
#### Advantages
#### Disadvantages




### How to use this repository
Have not got time to set up the release page. However:
- Install the font from the latest build folder
- Use Altium Mono for Copper Layer
- Use Altium Mono Bold for Solder Mask Layer
- Use Altium Mono Extrabold (Inverted) for Copper layer
- Currently, this font works best for 1mm text height, 0.05mm mask expansion, and 3.5mil trace/clearance capabilities.

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