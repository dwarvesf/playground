---
tags: engineering
author: Toan Ho
github_id: toanbku
date: 2022-08-28
---

![](./_assets/refactoring-ui-book-cover.png)


# Why should you read this book?
- Make your ideas look awesome, without relying on a designer.
- You'll have an answer for this: “I know this looks terrible, but I have no idea why.”

# Summarize
For a better reading experience, I recommend buying this book.

## Starting from Scratch
### Start with the feature, not a layout
- When designing an app, it’s best to start with a piece of actual functionality instead of trying to design the app’s shell.
- An app = a collection of features
- An app's shell = side bar, navigation,...
- For an example, when starting with a feature like “searching for a flight” and building the interface around that feature. The interface will need fields for the departure city, destination city, departure date, return date, and a button to perform the search.
### Detail comes later
- In the early stages of designing a feature, avoid getting caught up in low-level design decisions such as typefaces, shadows, and icons. Focus on the overall structure and functionality first.

### Don’t design too much
- It's not necessary to design every single feature of an app before moving on to implementation. Instead, work in short cycles, designing and implementing one feature at a time.

### Choose a personality:
- Consider the personality and branding of the app when making design decisions. Align the visual elements with the desired tone and style to create a cohesive and engaging user experience.

### Limit your choices:
- Too many design options can lead to decision paralysis. Limiting the number of choices for colors, fonts, and other design elements can help maintain consistency and streamline the design process.

## Hierarchy is Everything
### Not all elements are equal:
- Not all elements in a user interface should have the same visual weight. By assigning different levels of importance to different elements, you can guide the user's attention and create a more organized and intuitive design.

### Size isn't everything:
- While larger elements tend to attract more attention, size alone is not enough to establish a hierarchy. Other factors such as color, contrast, and positioning also play a crucial role in creating visual hierarchy.

### Don't use grey text on colored backgrounds:
- Using grey text on colored backgrounds can make the text difficult to read. It's important to ensure sufficient contrast between the text and the background to maintain readability.

### Emphasize by de-emphasizing:
- Sometimes, reducing the visual weight of certain elements can actually draw more attention to the important ones. By de-emphasizing less important elements, you can create a stronger visual hierarchy.

### Labels are a last resort:
- Instead of relying solely on labels to convey information, try to use visual cues and context to make the purpose and functionality of elements clear. Labels should be used sparingly and only when necessary.

### Separate visual hierarchy from document hierarchy:
- Visual hierarchy is about guiding the user's attention, while document hierarchy is about organizing content. It's important to separate these two concepts and design them accordingly.

### Balance weight and contrast:
- Finding the right balance between the weight of elements and the contrast between them is crucial for creating a visually pleasing and effective hierarchy. Too much contrast can be overwhelming, while too little can make the design appear flat.

## Layout and Spacing

### Start with too much white space:
- Giving every element more room to breathe can help clean up a design and create a more organized and intuitive layout.
### Establish a spacing and sizing system:
- Using a constrained set of values for spacing and sizing can help create consistency and efficiency in design.
### You don't have to fill the whole screen:
- Leaving some empty space on the screen can create a more balanced and visually pleasing design.
### Grids are overrated:
- While grids can be useful for some designs, they are not always necessary and can sometimes limit creativity.
### Relative sizing doesn't scale:
- Using relative sizing can create inconsistency in design across different devices and screen sizes.
### Avoid ambiguous spacing:
- Clear and consistent spacing can help create a more organized and intuitive design.

## Designing Text
### Establish a type scale:
- Creating a consistent and harmonious hierarchy of font sizes helps establish visual hierarchy and improves readability. By defining a set of font sizes that relate to each other, you can create a more cohesive and balanced design.
### Use good fonts:
- Choosing the right fonts for your UI is crucial. Select fonts that are legible, appropriate for the content, and align with the overall style and tone of the design. Avoid using too many different fonts, as it can create visual clutter.
### Keep your line length in check:
- The length of a line of text affects readability. Avoid extremely long lines that require excessive eye movement, as well as very short lines that can make reading feel disjointed. Aim for a comfortable line length that allows for easy scanning and reading.
### Baseline, not center:
- Aligning text to the baseline rather than the center creates a more visually pleasing and balanced design. Center-aligned text can appear awkward and unbalanced, while baseline alignment provides a more solid foundation.
### Line-height is proportional:
- Adjusting the line-height, or the vertical spacing between lines of text, is important for readability. Use a proportional line-height that is appropriate for the font size and typeface being used.
### Not every link needs a color:
- Using color alone to indicate links can be overwhelming and distracting. Instead, consider using underlines or other visual cues to make links stand out while maintaining a clean and uncluttered design.
### Align with readability in mind:
- When aligning text, consider readability and legibility. Left-aligned text is generally the most readable, while right-aligned and centered text can be more challenging to read, especially for longer passages.
### Use letter-spacing effectively:
- Adjusting the spacing between letters can have a significant impact on the overall look and feel of the text. Use letter-spacing to improve legibility, emphasize certain words or phrases, or create a specific visual style.

## Working with Color
### Ditch hex for HSL:
- Instead of relying solely on hexadecimal color codes, consider using HSL (Hue, Saturation, Lightness) values. HSL provides more flexibility and control over color variations.
### You need more colors than you think:
- Don't limit yourself to a small set of colors. Having a wider range of colors allows for more visual interest and flexibility in design.
### Define your shades up front:
- Establish a set of shades for each color in your palette. This helps maintain consistency and makes it easier to create harmonious designs.
### Don't let lightness kill your saturation:
- Be mindful of the balance between lightness and saturation in your color choices. Avoid using colors that are too light and washed out, as they can lack impact.
### Greys don't have to be grey:
- Experiment with using colored greys instead of traditional neutral greys. This can add depth and visual interest to your design.
### Accessible doesn't have to mean ugly:
- Prioritize accessibility in your color choices, but don't sacrifice aesthetics. There are ways to create visually appealing designs that are also accessible.
### Don't rely on color alone:
- Use color as a visual cue, but ensure that important information is also conveyed through other means, such as text or icons.

## Creating Depth
### Emulate a light source:
- When adding depth to your design, imagine a light source and create shadows and highlights accordingly. This helps create a sense of depth and realism.
### Use shadows to convey elevation:
- Shadows can be used to simulate the elevation of elements. By adding shadows beneath elements, you can create a layered effect and enhance the perception of depth.
### Shadows can have two parts:
- Consider using both an ambient shadow and a directional shadow to create a more realistic and nuanced sense of depth.
### Even flat designs can have depth:
- Depth doesn't have to be limited to skeuomorphic or realistic designs. Even in flat designs, subtle shadows and layering can add depth and visual interest.
### Overlap elements to create layers:
- Overlapping elements can create a sense of depth and hierarchy. By strategically layering elements, you can guide the user's attention and create a more engaging design.

## Working with Images
### Use good photos:
- Choose high-quality and visually appealing photos that align with the style and tone of your design. Avoid using generic or low-resolution images.
### Text needs consistent contrast:
- Ensure that text placed on top of images maintains sufficient contrast for readability. Adjust the color or opacity of the text to ensure legibility.
### Everything has an intended size:
- Be intentional about the size and placement of images in your design. Consider the context and purpose of each image and resize them accordingly.
### Beware user-uploaded content:
- If your design allows users to upload images, be prepared to handle variations in quality, aspect ratio, and content. Implement guidelines or restrictions to maintain visual consistency.


# Reference
- https://www.refactoringui.com/