## Coastal Drive

## Purpose

This project explores the creation of a short cinematic driving sequence, focusing on controlling motion, speed perception, and spatial continuity within AI-generated video.

The objective was to investigate how a single reference image could be expanded into a multi-shot sequence through prompt-driven animation and chained clip generation. Each segment was generated independently, requiring continuity to be enforced through structured prompts rather than shared state.

The project examines how generative models interpret motion, maintain object identity during high-speed action, and handle continuity across sequential outputs — including camera transitions, directional consistency, and environmental persistence.

It serves as a technical study in motion control and continuity enforcement, where both physical realism (vehicle behavior, speed, and traction) and spatial coherence (road alignment, environment, and camera positioning) must be explicitly defined to avoid model drift.

### Step 1

 - Generate the reference image

**Original Prompt Used to Generate Reference Image**

*Model Used: Nano Banana 2*
```
A photorealistic cinematic shot of a modern sports car driving along a coastal highway overlooking the ocean.

The car is positioned slightly off-center, angled forward, showing both the front and side profile clearly. The road curves gently along the coastline, with a low guardrail separating it from the ocean below.

The camera is positioned at a low angle near the road surface, capturing the car from the side at wheel height. Wide lens perspective, natural proportions, no distortion.

The background shows a deep blue ocean stretching to the horizon, with distant cliffs and soft atmospheric haze. The environment feels open and expansive.

Lighting is warm golden hour sunlight, casting long shadows and strong reflections on the car's surface. Clean sky, no clouds or minimal haze.

Style: cinematic realism, high detail, sharp textures, natural colors, stable composition, no motion blur, no distortion, no artifacts.
```

### Step 2

- Generate first part of the sequence

**Original Prompt Used to Generate Video**

*Mode Used Seedance 2.0 fast*
*Clip 1 - Lead up to Pass*
```
Use the reference image as the exact composition.

The car is already approaching at high speed from mid-distance and rapidly closes the remaining distance to the camera

The vehicle maintains constant high velocity throughout. No acceleration phase, braking, hesitation, or deceleration.

The car begins in the distance and rapidly closes the distance to the camera, growing larger in frame. It passes extremely close to the camera position at high speed and continues beyond frame.

Wheels rotate rapidly and remain physically consistent with vehicle speed. Road markings, roadside details, cliffs, and ocean sweep past during the pass-by, creating strong motion parallax and a powerful sense of speed.

The camera remains low and fixed near the road with subtle vibration caused by the passing vehicle.

The vehicle remains stable and planted on the road surface. No drifting, sliding, tire smoke, or loss of control.

Motion is physically realistic and cinematic. No distortion, no warping, no changes to vehicle shape, identity, color, or proportions.
```

*Clip 2 - Rear Chase Camera*
```
Continue directly from the final frame of the input video.

CONTINUITY RULE:
The vehicle continues traveling along the same coastal road in the same direction established in the input video.

The ocean remains on the right side of the vehicle throughout the sequence. Cliffs, hills, and inland terrain remain on the left side of the vehicle throughout the sequence. Do not reverse the road orientation or swap the positions of the ocean and land.

CAMERA:
The camera transitions naturally into a low rear chase perspective following behind the vehicle. The camera follows as if mounted to a second vehicle traveling in the same lane behind the car.

The camera remains behind the vehicle throughout the clip and looks forward in the direction of travel.

DRIVING ACTION:
The vehicle maintains high speed and continues accelerating along the winding coastal highway.

The road features sweeping bends, elevation changes, and long coastal curves that emphasize speed and vehicle handling.

During one prominent corner, the rear of the car briefly rotates outward in a controlled high-speed drift, producing a short burst of tire smoke before immediately regaining full traction and continuing forward.

MOTION:
Strong motion parallax, realistic wheel rotation, convincing suspension movement, and cinematic speed throughout.

The vehicle remains planted, stable, and under control. No crashes, no loss of control, no unrealistic drifting.

CONSISTENCY:
Maintain vehicle identity, proportions, color, and design. No distortion, warping, deformation, or changes to the car's appearance.
```


*Clip 3 - Exit the Frame*
```
Continue directly from the final frame of the input video.

CAMERA RULE:  
The camera is completely static and locked. No pan, tilt, zoom, tracking, or movement. The framing does not change.

ROAD CONTINUITY RULE:  
The vehicle remains on the exact same physical road geometry shown in the input video. The road does not change shape, does not split, and does not extend beyond the visible layout.

SCENE CONTINUITY:  
No new roads or alternate paths are introduced. No additional lanes, shortcuts, or modified geometry appear. The environment remains identical to the final frame.

ACTION:  
The car continues along the existing curve at high speed, following the visible road exactly as it exists in frame.

As the road bends left, the vehicle naturally follows the curve and gradually exits the frame. The camera remains fixed and does not follow.

The vehicle maintains realistic motion, speed, and traction. No drifting, no off-road movement, no sudden changes in direction.

FINAL MOMENT:  
The car disappears around the bend and out of frame, leaving the empty coastal road visible in the static shot.
```
### Observations

- The initial pass on the first clip started with the car stationary. The prompt was refined to specify that the car is already in motion at the start of the clip, which corrected the pacing and improved realism.
- In the first attempt at clip 2, the car was rendered traveling in the opposite direction from the first clip. A continuity rule defining direction of travel and environmental orientation was added to enforce consistency.
- In the initial attempt at clip 3, the camera did not remain static and instead tracked the vehicle. Additionally, the car deviated from the road, passing through the guardrail and continuing along a non-existent path. This highlighted that both camera behavior and spatial constraints must be explicitly locked to prevent unintended environmental reinterpretation.
## Key Learnings

- Models default to initiating motion from a stationary state unless explicitly instructed otherwise. Beginning a scene "in motion" requires clear temporal initialization.
- Perceived speed is not controlled by abstract descriptors (e.g. “fast”), but by visual indicators such as wheel rotation, environmental parallax, and background motion.
- Directional continuity is not preserved between clips by default. Without explicit constraints, models may reverse travel direction or alter scene orientation between generations.
- Spatial geometry is not inherently respected. Without strict constraints, models may modify road layout or introduce new paths to satisfy motion instructions.
- Camera behavior must be explicitly defined. If not constrained, models may introduce unintended tracking or camera motion.
- Generative models do not simulate collision or physical boundaries reliably. Objects may pass through environmental elements unless movement constraints are explicitly enforced.
- Continuity across clips requires treating each generation as stateless, with all assumptions about direction, layout, and motion explicitly redefined in each prompt.
- This approach mirrors traditional cinematography and vehicle rigging workflows, adapted to a stateless generative system where continuity must be reconstructed at each stage.