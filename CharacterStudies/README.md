
# Controlled Character Identity Generation in AI Systems

## Objective

Develop a controlled workflow for generating and maintaining consistent character identity across multiple transformations, including stylistic reinterpretation, multi-angle turnaround sheets, and attribute modifications (clothing and expressions).

## System Insight

Maintaining character identity across transformations requires treating the initial design as a fixed reference state. All subsequent prompts must be framed as constrained modifications rather than generative reinterpretations.
## Step 1

### Generate Initial Character Models

- Pixel art images of the characters to be modeled were created using Krita
- The pixel art was then passed into several LLMs to create a cartoon character from each image
	- Ultimately, the best results came from **Gemini Flash**

**Original prompt used to generate character models**
```
A full-body illustration of this exact character. Use the reference image as the canonical design. Preserve facial structure, beard shape, hairstyle, body type, clothing details, and proportions. Do not redesign or reinterpret the character. Original stylized western cartoon aesthetic, clean linework, simple readable shapes, animation-ready character design, white background. smooth drawing lines.
```

- The first character, Arlo came out as intended
- The second character, Larry required a second pass to refine the image as the uniqueness of the original character design led the model to infer certain elements about the character that did not fit the desired look
	- On the third attempt a correct interpretation was produced


### Convert Character Models Into Animation Character Sheets

- The characters were passed into Seedream 4.5 to create animation turnaround sheets

**Original prompt used to generate turnaround sheets**
```
Use the reference image as the canonical character design.

Create a professional animation turnaround sheet for this exact character.

Show the character in:
- Front view
- 3/4 front view
- Side profile
- 3/4 rear view
- Back view

The character must remain identical across all views.

Preserve exactly:
- Facial structure
- Beard shape and thickness
- Hairstyle
- Body proportions
- Clothing design
- Color palette
- Accessories

This is a technical animator reference sheet, not a concept-art redesign.

Maintain orthographic consistency between views. The character should appear as the same individual rotated in space rather than separate illustrations.

Clean white background.
Production model-sheet presentation.
Professional animation studio reference quality.
Clear spacing between views.
No dramatic posing.
Neutral expression.
Arms relaxed at sides.
Full body visible.
```

- The Arlo sheet worked on the first attempt. Front, side and back views were generated, preserving the features of the original image
- The initial Larry turnaround introduced unintended facial hair, demonstrating the model’s tendency to infer attributes from ambiguous features. Removing references to facial hair corrected the output and restored identity accuracy.

### Changing the Character's Attire

- The original character models were generated in clothing that did not fit the general mood of the final piece, as such I attempted to alter their attire.

**Original prompt used to modify the character's clothing**
```
Use the provided character sheet as the canonical reference.

Preserve the character's identity exactly:
- facial structure
- beard
- hairstyle
- body proportions
- age
- skin tone
- overall silhouette

Only change the clothing.

Replace the current outfit with a gray crew cut t-shirt, jeans, and the same boots they are wearing.

Do not redesign the character.
Do not alter the face.
Do not alter the body shape.
Do not alter the hairstyle or beard.

The result should clearly be the same character wearing different clothes.
```


### Character Expressions

**Original prompt used to modify the character's facial expressions**
```
Use the reference image as the canonical character design.

Create a professional animation expression sheet.

Show the same character with:
- Neutral
- Happy
- Angry
- Confused
- Surprised
- Determined
- Smug
- Concerned

Maintain exact consistency in facial structure, beard, hairstyle, and proportions.

Clean white background.
Animation production reference sheet.
Head and shoulder studies.
Studio model-sheet presentation.
```


## Key Learnings

- Models tend to introduce or remove inferred attributes (e.g., facial hair) when constraints are ambiguous
- Explicit negative constraints are required to prevent stylistic reinterpretation
- Identity consistency degrades when modifying multiple attributes simultaneously
- Using a canonical reference significantly improves consistency across transformations
- Multi-view outputs (turnaround sheets) require strict orthographic constraints to avoid drift