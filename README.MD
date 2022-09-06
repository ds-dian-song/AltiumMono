# Altium Mono
## A TrueType font family to create better-looking copper layer in Altium Designer

### This is project is still a working progress

### Motivation


### Observation 
#### "1 mm" Text will never be 1 mm, why?
#### What kind of correlation is out there?
- Conclusion: For TrueType Fonts with em size of 1000 the text height is (L / 1000 * 0.7553 * H) mm, where L is pixel length in the 1000x1000 em box, and H is the input of text height in Altium Designer.
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

### Licenses 
Altium Mono was created based on JetBrains Mono, a monospace technical typeface for developers.
There is no restrictions on your use of the content in this repository. However, I as the author accept no liability. 