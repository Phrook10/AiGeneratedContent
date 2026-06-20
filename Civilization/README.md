## The Rise and Fall of Civilization

## Purpose

This project explores the concept of an accelerated civilization timeline, compressing the rise, peak, and collapse of a built environment into a continuous visual sequence.

Rather than generating a single long clip, the approach is based on assembling multiple short, independently generated segments into a unified timeline. The goal was to test whether consistent environmental transformation could be maintained across these segments through controlled prompt design.

The project examines how generative systems handle large temporal shifts, and how continuity can be preserved across drastic changes in structure, density, and decay.

It serves as both a visual experiment and a technical study in composing coherent narratives from fragmented AI-generated outputs.

### First Iteration

- In this video, I attempted to create the video in one prompt, but the time limit on the video, as well as the speed that it necessitates made the end product awkward. Instead I opted to splice 2 clips together to create a 25 second long video
- I generated an image of an open plain with a hill to be used as the starting frame of the first video, and I used the ending frame of the first video as the starting frame of the second, and finally the original image as the final frame

**Original Prompts Used to Generate Video Clip** :
*Rise of Civilization*
```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot. No camera movement, zoom, reframing, or terrain change. Hill position and horizon remain fixed.

A continuous timelapse spans thousands of years of human development expanding outward FROM the hill. All development originates at the hill and grows outward in radial layers. Structures are built ON and AROUND the hill, not replacing it.

Growth always starts at the hill center and expands outward. The highest density and tallest structures remain centered on the hill across all eras.

  
Pollution accumulates continuously and never resets. It increases gradually in haze, sky desaturation, light diffusion, and atmospheric density.

CORE STRUCTURAL RULE:  
The hill remains physically present at all times. Civilization does not replace it. Instead, each era builds over and around it. The hill becomes increasingly embedded inside architecture, eventually forming the base core beneath the tallest buildings.

[0–2s] reference frame.

[2–4s] A primitive hut is built directly on the hilltop, anchored to the terrain rather than replacing it. Small-scale farming begins around it.

[4–6s] Settlement expands outward from the hut. Homes and fields radiate from the hill base. The hut is now part of a small clustered village, still visible as the central origin point.

[6–8s] Medieval era. Stone buildings, walls, and a castle are constructed around and partially over the hill, which now forms the foundation of a fortified town core. Light smoke and early atmospheric haze appear.

[8–11s] Industrial to modern transition accelerates. Dense city growth rapidly expands outward. The hill is now buried beneath layered urban infrastructure, with only elevation revealed through taller central skyscrapers. Heavy smog develops.

[11–15s] Futuristic megacity fully expands across the frame. The hill is no longer visible but exists as the structural core beneath the tallest and densest vertical cluster. Buildings form a central peak that gradually lowers outward in all directions. Thick global haze and diffused polluted light fill the atmosphere.

FINAL FRAME: fully saturated megacity occupying entire landscape. Central vertical density peak marks the buried hill location. Hold 1 second.

Stylized cinematic realism. Continuous architectural layering. Smooth additive construction only. No morphing objects, no object replacement, no cuts, no camera movement, no terrain deformation.
```

**Final Assessment**
- I was unable to achieve enough control over each era of the video with this approach
### Second Iteration

- The core concept in this iteration is to generate 6 individual clips and splice them together
- To maintain consistency, the final frame of each clip with be used as the first frame of the subsequent clip
	- anticipating removing emphasis of evolution around the hill as it seems to distract the model from the rest of the elements in the video

### Prompt Strategy Notes

These prompts intentionally became verbose during development as I explored the limits of rule-based control in generative video models.

This phase was used to test:
- how strictly models follow structural constraints
- how many simultaneous rules can be enforced
- how spatial continuity can be preserved across clips

The resulting prompt length reflects experimentation rather than an ideal production approach. Through this process, I identified that shorter, prioritized constraints produce more reliable outputs.

**Prompts Used to Generate Clips**

*Clip 1 - Birth of Civilization*
```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot. No camera movement, zoom, reframing, or terrain change. Hill position and horizon remain fixed.

All structures are continuous extensions of previous frame. Do not restart or redesign the world. Only evolve existing structures.

STATE: pristine natural hill in open plain.

A single primitive hut is constructed directly on the hilltop. It is the only structure. Small farming begins immediately around it.

The hut is the architectural origin point of all future growth and must remain visually identifiable.

Clean air, clear sky, no pollution.

END STATE: small clustered settlement centered on hut, slightly expanded outward from hill base.
```

*Clip 2 - Early Growth*
```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot. No camera movement, zoom, reframing, or terrain change. Hill position and horizon remain fixed.

All structures are continuous extensions of previous frame. Do not restart or redesign the world. Only evolve existing structures.

STATE: early settlement continues to expand outward radially from hill.

The original hut is now embedded within a growing village core. Add wooden homes, dirt paths, and early clustered agriculture radiating outward from hill base.

No replacement of structures. All additions build around existing ones.

Light atmospheric dust begins. Minimal haze.

END STATE: dense medieval village core centered on hill, with visible radial growth pattern.
```

*Clip 3 - Medieval to Early Industrial*
```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot. No camera movement, zoom, reframing, or terrain change. Hill position and horizon remain fixed.

All structures are continuous extensions of previous frame. Do not restart or redesign the world. Only evolve existing structures. Do not move structures to denote outward expansion, instead, build new structures further out. 

INITIAL FRAME RULE:
The first frame must exactly match the reference image. Preserve all existing structures, roads, terrain, and settlement layout. No walls, castles, factories, or additional districts may appear before the animation begins.

EXPANSION RULE:
The outer boundary of the settlement continuously advances away from the hill. New buildings appear beyond the existing settlement edge. Existing districts remain fixed in position. The city grows through additional outer layers of development, never by shifting, compressing, or rebuilding inward. Never change the shape of the hill, or expand it in any way.

STATE: fortified medieval town transitions into early industrial expansion.

The existing village remains intact. New construction occurs outside the current settlement. Additional homes, workshops, roads, and stone structures expand outward in concentric layers from the hill.

The central hill settlement gradually upgrades into a fortified stone keep and eventually a castle through visible construction and expansion, not sudden replacement.

Stone walls are constructed only after sufficient urban growth exists to justify them. They expand around the developed settlement rather than appearing fully formed.

Early chimney smoke appears. Light atmospheric haze accumulates. Pollution remains minor.

Density remains highest at the hill, while the settlement footprint expands outward to occupy roughly half the foreground.

END STATE: large medieval-industrial hybrid city centered on the buried hill core, with a castle at its center and visible outward urban growth from the original village.
```

*Clip 4 - Industrial Acceleration*
```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot. No camera movement, zoom, reframing, or terrain change. Hill position and horizon remain fixed.

All structures are continuous extensions of previous frame. Do not restart or redesign the world. Only evolve existing structures. Do not move structures to denote outward expansion, instead, build new structures further out. 

INITIAL FRAME RULE:
The first frame must exactly match the reference image. Preserve all existing structures, roads, terrain, and settlement layout. No walls, castles, factories, or additional districts may appear before the animation begins.

EXPANSION RULE:
The outer boundary of the settlement continuously advances away from the hill. New buildings appear beyond the existing settlement edge. Existing districts remain fixed in position. The city grows through additional outer layers of development, never by shifting, compressing, or rebuilding inward. Never change the shape of the hill, or expand it in any way.

STATE: rapid industrial and modern expansion phase.

VISIBILITY RULE:
Atmospheric pollution must never obscure city detail. Foreground and midground architecture remain crisp and readable throughout. Windows, facades, signage, billboards, lighting, and infrastructure are clearly visible despite the polluted atmosphere.  
  
Factories, rail systems, highways, and dense urban infrastructure spread aggressively outward from central hill core.  
  
The hill is no longer visible as terrain; it is fully embedded beneath layered construction. Its location is only implied by maximum building density and tallest structures at center.  
  
Heavy industrial smog fills the atmosphere as a visible volumetric layer. Pollution is apparent through atmospheric haze, muted sky color, and diffused sunlight, but the city remains clearly visible. Foreground and midground buildings retain sharp architectural detail, readable windows, signage, billboards, lighting, roads, rail systems, and infrastructure. Atmospheric effects add depth without obscuring urban detail. 
  
END STATE: vast modern industrial megacity expanding across entire frame with central density peak.
```

*Clip 5 - Futuristic Megacity*

```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot.

CAMERA RULE:
The camera is completely fixed. No movement, zoom, tilt, pan, roll, reframing, or perspective change at any point.

SPATIAL PRIORITY RULE:
The foreground is the primary focus of all transformation and must remain highly detailed, readable, and visually dominant. Midground and background support depth and scale but do not override foreground clarity.

SCENE TRANSFORMATION:
The entire environment transitions from industrial-era city to a fully realized futuristic megacity. Transformation occurs through replacement. 

Existing industrial and modern architecture is replaced with entirely new futuristic structures with different geometry, scale, and design language.

URBAN EXPANSION RULE:
Futuristic construction progressively advances toward the camera, transforming foreground areas over time to full obscure the buildings behind it. The city grows forward through depth, replacing all remaining open land until it reaches and fully occupies the foreground.

NATURAL TERRAIN ELIMINATION:
All grass, soil, fields, and exposed natural ground are progressively replaced by futuristic buildings.

ARCHITECTURE STYLE:
Cyberpunk brutalism fused with high-tech megastructural design. Massive arcologies, dense interconnected towers, layered city platforms, elevated transit systems, and large-scale integrated complexes dominate the scene. Buildings are monolithic and structurally unified, not simple skyscraper extensions.

FOREGROUND TRANSFORMATION RULE:
Foreground areas are actively and progressively redeveloped into futuristic urban infrastructure during the sequence. No foreground terrain remains unchanged. Detail remains high, but all visible foreground surfaces are continuously replaced by architecture, roads, and integrated megastructures.

FINAL STATE:
A complete futuristic megacity fills the frame, with the highest visual density and detail in the foreground and continuous urban expansion into the background. No industrial-era or modern-era architecture remains visible in the final frame. All structures are futuristic in design. No natural terrain remains visible. The camera framing and perspective remain unchanged.
```

*Clip 6 - The Fall of Civilization*
```
Reference image defines exact camera position, framing, lens, and composition. Extreme wide locked static shot.

CAMERA RULE:  
The camera is completely fixed. No movement, zoom, tilt, pan, roll, reframing, or perspective change at any point.

INITIAL STATE:  
The clip begins with a fully formed futuristic megacity occupying the entire frame. Dense skyscrapers, arcologies, transit systems, highways, and layered infrastructure fill the scene.

SYSTEM FAILURE AND SCALE RULE:
All artificial systems fail in a physically realistic order. Electrical systems shut down first, causing all billboards, signage, and emissive lighting to turn off completely and remain dark for the remainder of the sequence.traffic stops, lights flicker out, signage powers down, and energy systems fail.

All urban structures maintain correct physical scale at all times. Natural elements such as grass, soil, and vegetation remain ground-level only and never scale beyond terrain height. Vegetation does not grow vertically at building scale or interfere with architectural proportions.

NATURAL RESTORATION RULE:
As the city collapses, urban materials are replaced at ground level by terrain restoration. Buildings dissolve into rubble and soil, which gradually transitions into flat natural ground and grass coverage consistent with landscape-scale growth, not vertical structures.

ARCHITECTURAL COLLAPSE:  
Buildings do not transform into new structures. Instead, they progressively lose structural integrity and collapse vertically downwards. Skyscrapers break, buckle, and fall into rubble and dust. Megastructures fragment and disassemble.

NATURE RECLAIM RULE:  
As structures collapse, the environment is progressively reclaimed by natural terrain. Concrete, steel, and urban infrastructure dissolve into earth, soil, vegetation, and natural ground formations. Green surfaces reappear and spread outward as urban material disappears. DO NOT use any fantasy effects.

FINAL RESTORATION:  
All urban elements fully vanish. No buildings, roads, infrastructure, or artificial lighting remain. The original natural landscape is restored through regrowth exactly as the reference image’s base state: a grassy hill in an open plain with clean air and clear sky.

FINAL FRAME:  
Only the original hill remains. No trace of civilization is visible. Hold for 2 seconds.
```


**Observations**
- Clip 3 required significantly more constraints as the model seemed to struggle with the outward expansion of the civilization
	- The model also tried to grow the mountain upwards
	- To solve this, the initial frame and expansion rules were implemented
- It is possible the clip length needs to be increased as we go through the periods of civilization to allow for better representation of growth over time
- For clip 4 I pre-emptively added a visibility rule to prevent the pollution effects from obscuring details
- For clip 5, the prompt was becoming long, and logically complex, resulting in failure to generate the correct clip. I tightened and shortened it. Redundant rules and statements were removed, and obsolete directives were trimmed. 
	- The model had a difficult time getting the proper expansion of the civilization. In turn I rewrote the entire prompt
- For clips 1-5 I used Kling 3.0 Turbo, which only allows for a first frame to generate the video. For clip 6, i had to use Kling 3.0 in order to take advantage of the first and last frame feature.

### Final Assembly

- Using Suno, I created a symphonic track for the video
- I stitched it all together using Davinci resolve to create the final composite clip
-  Minor visual discontinuities between clips are present due to limitations in extracting precise final frames for use as subsequent inputs
	- This highlights a tooling constraint rather than a model limitation, and would be mitigated with more precise frame control or native keyframe chaining

### Key Learnings

- Prompt effectiveness was not determined by length alone, but by how well constraints were prioritized and structured. Increasing the number of constraints improved control up to a point, after which outputs became less stable and required additional iteration.
- Stateless generation requires explicit reconstruction of prior context in every prompt
- Spatial consistency is best preserved through reference chaining, not rule enforcement alone
- Complex transformations are significantly more reliable when broken into discrete stages
- Mixing models across clips is not the most effective way to get consistent image quality
