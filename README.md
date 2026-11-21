# HW7: F1 Night Pit Lane (WebGL2 Ray Tracer)

**Live demo:** https://amlc16.github.io/computer-graphics-hw7/hw7.html

A real-time ray tracer written as a single HTML file (`hw7.html`). Everything on screen is traced in the fragment shader; the only rasterized geometry is a full-screen quad. Runs at about 60 FPS on my machine at 640x400.

## Scene
- Formula 1 car built from analytic primitives (boxes, ellipsoids, finite cylinders): chassis, nose, sidepods, cockpit and helmet, front and rear wings, four wheels with rims and hubs, suspension arms.
- Glass sphere, reflective green cube, and an animated red sphere.
- Polished checkered floor with a painted pit box, procedural garage-bay back wall, striped pit barriers, and glowing light bars and strips.

## Ray tracing features
- **Recursion as a loop:** reflection and refraction bounces run in a GLSL `for` loop (GLSL has no recursion).
- **Local Phong shading:** ambient, diffuse and specular, with per-material specular strength and shininess.
- **Shadows:** one shadow ray per light. Glass casts a lighter, tinted shadow.
- **Multiple lights:** three colored point lights (warm white key, red fill, blue rim).
- **Glass:** Schlick Fresnel, total internal reflection, entering and exiting handled correctly. Uses the dominant-ray approach (reflect or refract per interaction) for noise-free output.
- **Reflections:** floor, car paint, cube, rims and hubs.
- **Intersections:** box (slab method), sphere, ellipsoid, finite cylinder with end caps, and planes, with a bounding box around the car for speed.
- **Image:** ACES tone mapping, vignette, gamma correction.

## Controls
- **Drag** on the canvas to orbit the camera around the car.
- **Max Bounces** (1-8): ray recursion depth.
- **Ambient Strength:** fill light.
- **Light Intensity:** brightness of all point lights.
- **Shininess:** specular highlight tightness.
- **Glass IOR** (1.1-2.0): refractive index of the glass sphere.
- The shader editors on the left recompile live as you type.

## Run locally
```bash
python3 -m http.server 8000
# open http://localhost:8000/hw7.html
```
Requires a browser with WebGL2.
