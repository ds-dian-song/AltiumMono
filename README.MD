# Altium Mono
## An (unofficial) TrueType font family based on JetBrains Mono to create better-looking text on copper layer in Altium Designer

### How to use this repository
This repo and its documentation is currently WIP. If you happen to understand what I am doing without me being pedantic about it, you can:
- Know that some features are still broken (for instance, inverting "i" will create undesirable result)
- Install on your Windows machine the fonts from the latest build folder.
- Apply `Altium Mono Regular` for a string object on the Copper Layer (Text height = 1mm), this is the "text"
- Apply `Altium Mono Bold` for a string object on the Solder Mask Layer (Text height = 1mm), this is the "mask expansion"
- Apply `Altium Mono Extrabold` for a string object on the Copper layer (Text height = 1mm, inverted), this is the "polygon pour"
- Observe that text to mask expansion is 0.05mm, and text to pour distance > 3.5mil.
- Adjust rules to allow 0 mm text-polygon clearance; Allow short circuit between text and touching net (most likely GND).
- The above rule may undermine DRC's capability of detecting troubles. Therefore, please use query language to create and manage specific rules.
- Please limit its use to one-off projects to avoid long-term maintenance headache, considering everything may change at this point.
- Write a poem on your piece of PCB and get it fabricated.
- To uninstall the font, use shortcut "WIN + S" to open search, and then find and enter "font settings". You will need to click "uninstall" three times for each variation. 
- If something unexpected happened, try disable "embed TrueType Font" & "automatically replace unavailable font" in Altium systems settings, and save project. 
- I would love your feedback! 

### Some Primitive Demo Pictures
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
- Better typography for PCB as a print medium (to an extent. After all: functionality, cost of production and engineering requirements override graphical preferences). There are still some wiggle room for personal touch outside functionality requirements.
- Create a decent-looking PCB business card as a show-off.

### Observation 
#### "1 mm" Text will never be 1 mm, why?
- Without access to the source implementation, I can only observe system behavior as a user. 
- Good news: actual text height scales linearly with speicifed text height.
- Conjecture: the text height is a function of **L**, the pixel length in its respective TrueType source file, and **H**, the user-specified text height in Altium Designer, f(L, H).
#### What kind of correlation is out there?
- Conclusion: For TrueType Fonts with em size of 1000 (very common choice of em height, actually) the text height is (L / 1000 * 0.7553 * H) mm, where L is pixel length in the 1000x1000 em box, and H is the input of text height in Altium Designer. This formular works for H > 0.125mm, which seems to be the minimum textbox height in Altium. BTW, the default TrueType "Arial" has em box size of 2048, which makes it behave differently. However, linearity still applies.
- This conclusion is, obviously, a brute force engineering solution to approach the problem. It works, but would be better if fully understand how Altium handles TrueType fonts under the hood.
### Solving this Problem with Altium's Default Stroke Font
- Copper, 0.5mm height, 3.5mil stroke
- Mask, 0.5mm height, 7.437mil stroke
- over lap two text boxes, you get your masked txt in a rectangular box.
#### Advantages
- Looks great and very compatible with Altium Designer's way of handling texts/primitives
- Measures almost true to the size 
- Portable across machines and software versions.
#### Disadvantages
- Altium introduces this typeface as "a simple vector font designed for pen plotting and vector photo plotting", and indeed to many people, this typeface has a 80s look.
- No alternatives
- Limited special symbols
- It can be better
### Solving this Problem with Adobe Illustrator/Inkscape
#### Advantages
- Content is saved as an Altium primitive (regions) and thus portable across systems
- True "polygon pour" look around typographical elements.
#### Disadvantages
- Using Illustrator requires subscription of Illustrator (TODO: repeat the same method in Inkscape)
- Grainy texture, usually not a big issue when you get the board fabricated. But think about it, Altium supports importing images at maximum 1200 dpi. 1200 may sound like a lot, but it is only 47 pixels per 1 mm. 
- High fidelity graphics costs compile time during polygon repour.
- A lot of calculations if a standard approach is not established *a priori*. 
- Repetitive. Good or bad depending you are paid by the hour or not ;)
- Not possible to dynamically change content. To accomodate any change, you have to do it again, which becomes pure labor sometimes.

### Solving this Problem with Custom TrueType Fonts
#### What is TrueType Font, Exactly?
Putting some keywords here, but will populate content soon:
- en, em, and em box
- ascend line & descend line
- Monospace font, and why JetBrains Mono
- Ligature and kerning
#### Advantages
- Once three layers are aligned correctly, edit all three boxes at once
- does not affect repour time
- Say bye to grainy texts (at least in 3D view, ultimately grainy or not depends on the fabricator)
#### Disadvantages
- maintainability issues
- portability issues

### Known Limitations
- Have to generate and install new typeface and install for each new typeface/fab capabilities
- If sharing the project to multiple machines, typeface have to be installed on each.
- Must follow best practice and save the typeface in dedicated project folder, and make note of it, to avoid jeprodizing maintainability.
- Ligature and kerning 
### Related Projects
My own:

- Will slowly release more PCB / Altium related stuff to Github

Public:
- [Scalable Graphics in the PCB Editor](https://forum.live.altium.com/#/posts/61899) by Darren Moore in year 2006

### Typography Tutorial and References
- Coursera stuff
- Youtube stuff
- Books
- My working guidelines & conventions

### Licenses & Intellectual Properties
Altium Mono was created based on JetBrains Mono. As a matter of fact, Altium Mono Regular is identical to JetBrains Mono 2.242. JetBrains Mono is a monospace technical typeface engineered for developers.It contains some nice features a technical person would be excited to see. JetBrains Mono is available under the SIL Open Font License 1.1 license, and can be used free of charge, for both commercial and non-commercial purposes. *The credit is yours, JetBrains.* 

There is no restrictions on your use of the content in this repository. However, I as the author assume no liability.

Altium as a trademark belongs to its respective owner. This project is not affiliated with or endorsed by this entity. The name of this typeface is chosen because of relevance. For IP related issues please connect with me directly. 
