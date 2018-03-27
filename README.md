## Jason Schmidt's Raytracer
This project focuses on crisp images simulating reflection and refraction. Depth of field is used to focus on certain areas, and
glossy reflection and refraction is available.

### Objectives:
1.  Reflection off of reflective surfaces, by sending secondary rays, mixed with the diffractive component.
![Basic reflection](/renders/reflect.png)

1.  Refraction through transparent surfaces, according to Snell's law. 
    1. Simply transparent:
    ![Transparency](/renders/transparency.png)
    1. Refraction (n < 1):
    ![Basic refraction](/renders/refraction.png)
    1. Refraction (n > 1):
    ![Basic reflection](/renders/refractionreverse.png)
    1. Lens effect:
    ![Lens effect](/renders/refractionlens.png)

1.  Rough/glossy reflection, by perturbing the secondary rays, giving a blurred rather than mirror-like reflection.
![Glossy reflection](/renders/glossreflect.png)

1.  Rough/glossy transmission, by perturbing the transmission rays, giving a blurred view behind the object.
    1. No gloss on refraction:
    ![Refraction](/renders/halfglossrefract.png)
    1. No gloss on reflection:
    ![Refraction](/renders/halfglossrefract.png)
    1. Both:
    ![Glossy refraction](/renders/glossrefract.png)

1.  New primitives are added and can be intersected: cone, semisphere, cylinder. These are fixed size but can be modified by hierarchical transformation. 
![Primitives](/renders/primitives.png)

1.  Depth of field can be used to focus on a particular plane, unfocusing the rest. This is done using supersampling, not as a postprocess.
    1. None:
    ![No DoF](/renders/nodof.png)
    1. Short:
    ![Short DoF](/renders/shortdof.png)
    1. Medium:
    ![Medium DoF](/renders/mediumdof.png)
    1. Long:
    ![Far DoF](/renders/fardof.png)

1.  Texture mapping maps raster images to UVs on geometric primitives, which gives a varying diffuse colour.
![Basic texture](/renders/texture.png)

1.  Normal mapping perturbs the normals on geometric primitives, where the normals are mapped to UVs using the same technique as texture mapping.
    1. White light:
    ![White light on normals](/renders/blanknormals.png)
    1. Coloured light from different angle:
    ![Colour on normals](/renders/normalscolours.png)
    1. With texture and objects:
    ![Normals](/renders/normalscolours.png)

1.  A final scene is created which demonstrates an object behind refractive materials.
    1. No DoF:
    ![Final](/renders/final.png)
    1. DoFs short to long:
    ![Final](/renders/finaldofclose.png) ![Final](/renders/finaldofmed.png) ![Final](/renders/finaldoffar.png)

Prettiest pictures by far:
![Complex](/renders/complex.png)
![Complex](/renders/complexdof.png)
![Complex](/renders/complexgloss.png)

Notes:
* Multithreading is on by default, and must be recompiled to disable it. (It gives roughly 5x speedup, using 8 threads.)
* Rays bounce up to twice.
* Glossiness, transparency, and refractive index are all optional parameters on materials in the lua scripts.
* Depth of field blur amount and focal distance are optional parameters on the render command.

Constructive solid geometry was originally planned for this project, and is half implemented. But it didn't make the cut.
