# Harmonica Tablature Notation Package/Template
Create high-quality harmonica tablature notation with LaTeX, designed specifically for Overleaf, the predominant online cloud-based LaTeX editor.


Think of this as the sheet music for harmonica. It's designed for writers of books or tutorials on harmonica playing, enabling them to swiftly and precisely render the notes they wish to illustrate.
This Template offers a way to create high-quality harmonica tablature notation using LaTeX. By bringing digital precision to harmonica notation, it now stands as a strong alternative to traditional handwritten methods.

While this template is fully operational within the creator's Overleaf project, it's still in the developmental phase for broader public use. Your feedback and contributions can help refine its applicability.

## Features
- Quick notation using simple commands.
- Support for various harmonica nuances including bends, warbles, and more.
- Easily encapsulated notation to minimize errors and ensure consistency.
- Customizable appearance to adjust notation to personal or publication needs.

## Getting started

1. Download the Harmonica Tablature Notation Package/Template from GitHub.
2. Upload the downloaded files into your Overleaf project (overleaf.com).
3. Create a new `.tex` file within the project.
4. Reference the notation in your new `.tex` file using the `\import{path_to_template_folder}{template_file_name}` command.

## Basic Usage - Harmonica Notation Guide and in LaTeX Commands

The harmonica notation used in this template provides a clear and intuitive method to represent harmonica play. Here's a breakdown:

### 1. Hole Numbers
- Indicates which hole number to play.
- Higher numbers correspond to higher pitches.
- The draw note has a higher pitch than the blow note.

### 2. Breathing Direction
In this template different LaTeX commands are employed to represent blow and draw notes for harmonica notations:

Draw notes utilize the numeric version of the hole number.
Blow notes employ the spelled-out version of the hole number.

- Defines whether to breathe in (draw) or breathe out (blow).
  - No Circle: Blow (Breathe out)
  - Circle: Draw (Breathe in)

#### Draw Notes
- **LaTeX Command:** 
- **Example:** 
  ```latex
  \4
   ```
   This produces a notation signifying an inhalation or "draw" through the 4th hole.

## Blow Notes
- **LaTeX Command:** Employ the spelled-out version of the hole number.
- **Example:** 
  ```latex
  \four
  ```   
  This produces a notation signifying an inhalation or "blow" through the 4th hole.

### Draw Bends

**LaTeX Command:** To signify a draw bend, utilize the command with "db" following the hole number.

**Example:**
```
\4db
```

This command produces a notation specifying a bend while drawing or inhaling through the 4th hole.

### Chords

**LaTeX Command:** Chords are played by drawing or blowing through multiple holes simultaneously. To notate this, combine the hole numbers.

**Examples:**
```
\ottb
```
Blow through holes 1 and 2 3 at the same time.

### Summary and examples
- e.g., `\four` results in Four blow (breathe out on the 4th hole).
- e.g., `\4` results in Four draw (breathe in on the 4th hole).
- e.g., `\tfd` is an instruction to breathe in on holes 3 & 4 simultaneously.
- e.g., `\ottd` denotes drawing on holes 1, 2, and 3 all at once.
- e.g., `\ottb` signifies blowing on holes 1, 2, and 3 simultaneously.

> **Note:** There are alternative notations using arrows, but this guide focuses on the circle notation, which is visually easier for the brain to recognize. However, for those familiar with arrow notation, both are included in the template.

# Dive Deep: The Underlying Code


We will now breakdown the code and how LaTeX works so you can modify the code to create your own symbols.


## Basic Single Note

Here is the code that generates a basic single note of the 4 draw tableture and how to call this function:

```LaTeX 
\newcommand{\4}{{ \circled{ $\downarrow$ 4 } } }
```

To utilize this in another file, simply call the function:
```LaTeX 
\4
```

## Complex Notation Abilities: Example of the Warble
```Latex
\newcommand{\bendintowarble}
{
    {
        {\uarr 
            {\circled
                {\hookdownarrow$ 4} 
            }
            \nearrow$
        { 
            \circled{ $\downarrow$ 4 } 
        } $\rightarrow$
        \circled{w$\downarrow$5454...} 
        }
    }
}
```

To utilize this in another file, simply call the function:
```LaTeX 
\bendintowarble
```

## Example
Here is an example from my book which demostrates how this code can be used

```
\section{The Blues scale - easy version (With no bend)}
\subsection{Going up - Main Octave}
\2\3\four\4\5\six

\subsection{Going down - Main Octave}
\six\5\4\four\3\2
``````

# Control Flow for Information Storage (Optional) 

While the core essence of this template is to generate harmonica tablature, an added layer has been incorporated for those who wish to delve deeper. This is the control flow, an advanced and entirely optional mechanism. It's an ideal tool for individuals looking to craft multiple products simultaneously, emphasizing on modular storage of information which can then be deployed in varied configurations. However, this aspect of the template caters primarily to advanced LaTeX users and is separate from the primary tablature generation functionality.

This structure and the associated control flows epitomize how I've leveraged the template to encapsulate all my harmonica knowledge, making it available on demand. The embedded content serves as a demonstrative example. By centralizing this within one template, I can selectively activate different products as needed, ensuring that all of them benefit from enhancements made in any single module. Moreover, any code refinements or the introduction of novel notation methodologies seamlessly find their place across all projects.

This hierarchical design allows for the crafting of "mini lesson modules". These adaptive modules can be integrated into a range of outputs, such as lessons, books, or workshops. By consolidating everything within one template, I've created a system where different products can be activated selectively, ensuring all benefit from updates made to any individual module. Additionally, any enhancements in code or the introduction of new notations are seamlessly integrated across all projects.


## Understanding the Control Flow:

The structure of this template employs a "control flow" mechanism. This ensures the content chosen for the final output fits the desired format, be it a lesson, book, or workshop. This layered approach makes the process streamlined, with a keen focus on flexibility and content reusability.

This way lesson modules, for example, `4_the_blues_scale/1.1_adv_blues_scale_overview`, can be included directly when specific needs arise.


### Main File:

The main file stands as the "master controller". It melds different workflow files, which then pull in the detailed content or lesson modules. (The main file also includes all of the code that generates the tableture.)



### Control Flow Files:

These dedicated files shape the content's layout for each individual product. The `\import{}` command weaves in the right lesson modules.

For instance:

- **2_book_control_flow.tex:** Paves the way for the book. It can commence with basic notation content, transition to rhythm lessons, and end with insights into the blues scale.
- **3_workshop_control_flow.tex:** Tailored exclusively for workshops, this brings in introductory content about the workshop, the instructor's backdrop, core notation details, and particular lesson modules geared towards a workshop audience.

### Using the Control Flow: An Example with Books

Here's how you can harness the control flow, taking the book format as a case in point:

1. In the main file, engage the `\input{0_latex_control_flow/2_book_control_flow.tex}` command.
2. `2_book_control_flow.tex` ushers in content befitting the book structure, covering the notation introduction, rhythm lessons, and nuances of the blues scale.
3. Compile the main file.
4. The result is a meticulously structured harmonica book, designed as per the directives of `2_book_control_flow.tex`.

## Personal Usage and Recommendations for Other Users:

This structure and the associated control flows epitomize how I've leveraged the template to encapsulate all my knowledge, making it available on demand. The embedded content serves as a demonstrative example.

For others eager to employ this template:

- You can either evolve with the content I've shared or infuse your unique materials.
- Conceive your control flows, or you might prefer to dive straight into the main file, shaping the structure in sync with your vision.
- The inherent modularity guarantees that any updates in specific lesson modules are reflected across all products that assimilate that module, establishing consistency and efficiency.

> **Tip:** Always verify the file paths in the `\import{}` commands to sidestep any compilation pitfalls.

# Support the Project
If this package has aided your project or work, consider supporting its future development. Your support can make a difference. Buy me a coffee here: https://www.buymeacoffee.com/micdiamond

# Feedback and Contributions
Your input can shape the future of this package. For bugs, improvements, or features, open an issue. Contributions, from code to documentation, are more than welcome.

# License
This project is free and open-source. Everyone is permitted to copy, distribute, and modify the software.



# Acknowledgments
This harmonica notation template was meticulously crafted using a plethora of LaTeX packages, with a particular emphasis on `tikz`, a versatile LaTeX package primarily intended for mathematics. The beauty and precision of `tikz` allowed for the creation of intricate and aesthetically pleasing harmonica notations. The list of packages instrumental to this project includes, but is not limited to: `tikz`, `xcolor`, `geometry`, `fancyhdr`, `inputenc`, `fontenc`, and `lmodern`. Each package played a pivotal role in shaping the functionality and appearance of the harmonica notations.

 Created by Michael Diamond.