## Time Squad Teaser

## Purpose


This project explores the creation of a short-form teaser for a fictional video game release, using generative AI to simulate a cohesive, character-driven promotional clip.

The objective was to investigate how consistent character identity and behavior could be maintained across multiple generated elements, including image-based character design, animated motion, and voiceover integration.

Rather than focusing on a single output, the project was structured as a series of controlled transformations, moving from static character concepts into animated sequences. This required maintaining continuity in appearance, movement, and tone across independently generated components.

The project examines how generative systems handle character persistence and expressive variation, and how prompt design can be used to align visual identity, motion, and audio into a unified presentation.

It serves as both a creative prototype and a technical study in coordinating multi-modal outputs within AI-driven production workflows.

## Step 1

### Generate Keyframes
- Created start frame, middle frame, and end frame
	- Original intent was to create 2 separate clips and splice them together
		- Using start frame for first clip, and mid-end frames for the second clip

**Original Prompt used to generate Keyframes**

```
A squad of three futuristic police agents in full police navy blue armor, including an iron man style helmet that cover the entire face are standing in an ancient near eastern bazaar. Their body armor visually transitions into normal period (ancient near east) looking people in period clothing. Realistic characters. The characters should not move, other than the visual effect of the transition to ancient near eastern robes. A high-angle shot from approximately 10 feet above the ground, looking down at the character at a 30-degree angle. The entire body remains visible in frame. Medium-wide composition, subject centered, cinematic depth of field. Any people in the scene who are not part of the squad should be occupied with other matters such that they do not notice or look directly at the squad.
```


- Subsequent frames were created using the original image, and specifying the changes to the image (eg: remove the visual transition, and complete their armor suits, and complete the visual transition)

## Step 2

### Generate Video (Model used: Kling 3.0)
#### Attempt #1

**Original Prompt used to generate Video**
```
Use the reference image as the exact camera setup with no reframing or camera movement. Preserve the original perspective and character placement. The central operative slowly raises his wrist communicator to his mouth and transmits: "Tee Ess One Four Nine, time slip achieved. Initiate Blend Protocol." Male voice, calm and tactical, delivered with measured precision. The team around him remains motionless, maintaining operational readiness. Natural, cinematic performance.
```

- This attempt was going to splice the 2 clips together, but since they flow directly one into the other
	- Attempting to splice two clips proved unreliable due to difficulty in matching terminal and initial frames with sufficient precision for seamless continuity
- Clip time was set at 6 seconds
- The video clip generated exactly as i wanted

#### Attempt #2

**Original Prompt used to generate Video**
```
Use the reference image as the exact camera setup with no reframing, no camera movement, and no changes to lens perspective. Preserve the original composition, formation spacing, and character positions throughout the entire sequence.

The central operative slowly raises his wrist communicator to his mouth and delivers the transmission: "Tee Ess One Four Nine, time slip achieved. Initiate Blend Protocol." Male voice, calm and tactical, with precise military radio discipline and measured pacing.

After completing the transmission, he lowers his hand back to his side. Immediately afterward, all operatives begin transforming simultaneously from the bottom upward. The transformation progresses smoothly from their feet to their heads, gradually revealing the exact characters and appearances shown in the final frame reference image. Preserve each character's final design, clothing, and identity exactly as depicted in the reference. The surrounding operatives maintain their formation and disciplined posture throughout the transformation. Natural, cinematic performance with realistic motion and a seamless transition into the final referenced appearance.
```

- This attempt meant to create the entire sequence in one shot
- Clip time was increased to 10 seconds to allow more time for the transformation
- The model introduced unintended visual effects (blue glow) and compressed the transformation timeline, indicating insufficient constraints on transformation style and pacing

#### Attempt #3

**Original Prompt used to generate Video**
```
Use the reference image as the exact camera setup with no reframing, no camera movement, and no changes to lens perspective. Preserve the original composition, formation spacing, and character positions throughout the entire sequence.

The central operative slowly raises his wrist communicator to his mouth and delivers the transmission: "Tee Ess One Four Nine, time slip achieved. Initiate Blend Protocol." Male voice, calm and tactical, with precise military radio discipline and measured pacing.

After completing the transmission, the central operative lowers his hand back to his side and remains still. There is a brief pause before the Blend Protocol activates.

The transformation begins simultaneously across all operatives and unfolds gradually over approximately 5 to 6 seconds. The change progresses upward in a continuous wave from the feet to the head. Legs and footwear transform first, followed by uniforms and equipment, then arms and upper-body details, with facial features, hairstyles, and final identifying characteristics resolving last.

The transformation is entirely physical and realistic in appearance. Do not use glowing energy, blue light, particle effects, electrical arcs, holographic overlays, magical effects, flashes, or aura effects of any kind. Avoid sudden jumps or instantaneous morphing. Each operative smoothly transitions into the exact characters depicted in the final frame reference image.

Preserve the formation spacing, posture, and camera composition throughout the sequence. The operatives remain disciplined and operationally focused during the transformation, exhibiting only subtle natural movement. By the end of the shot, all characters fully match the final frame reference image exactly in appearance, clothing, proportions, and identity.
```

- Video generated correctly
	- The only minor criticism is the voice is not to my taste, and the sound effect of the transformation is louder than it should be.
## Step 3

### Final Edits

- Added a logo for the game
- Added text "Coming Fall 2028"
- Fade out
## Key Learnings

- Constraining camera prevents hallucinated motion
- Explicit timing significantly improves transition quality
- Multi-stage transformations benefit from explicit sequencing and timing rather than relying on implicit model interpolation across complex actions
- Without restriction, model introduces unwanted visual effects (glow/energy)
- Gradual staged transitions produce more believable results than single-step morph