<link rel="stylesheet" href="../assets/help.css"/>

[bkg]: <../bkg/bkg.html>
[bob]: <../tools/bob.html>
[camera]: <camera.html>
[aa_mode]: <aa-mode.html>
[prim]: <../prim.html>
[comp]: <../comp.html>

# Studio Structure

The `studio` structure is where much of the magic happens. It's sort of a
catch-all for a variety of settings. Most notably:

* Background and environment
* Camera
* Session
* System

# Usage

```
  studio {

    ambient         r g b         // Ambient color
    haze            f r g b       // Haze density and color
    at              x y z         // Point to observe
    from            x y z         // Eye location
    up              x y z         // Up direction

    angle           degrees       // Field of view
    aperture        f             // Lens aperture
    aspect          f             // View aspect ratio
    focal_length    f             // Lens focal length
    haze            f             // Haze density (black)
    width           f             // Lens aperture width

    bunching        i             // Composite shape bunch size
    depth           i             // Maximum recursion depth
    resolution      w h           // View dimensions
    samples         i             // Sample count (non-pinhole lens)
    start           line          // Session start line
    stop            line          // Session stop line
    threshold       i             // Adaptive threshold

    jitter                        // Enable camera jitter
    no_exp_trans                  // Disable experimental transparency
    no_shadows                    // Disable shadows
    caustics                      // Enable caustic effects

    projection      fisheye       // Fisheye projection
    projection      flat          // Flat projection
    projection      no_parallax   // Same as flat
    projection      orthogonal    // Perspective projection

    antialias       none          // No antialiasing
    antialias       corners       // Average four pixel corners
    antialias       quick         // Quick sliding window
    antialias       adaptive      // Adaptive sliding window

    background      r g b         // Solid background color
    background      {}            // Color plane background
  }
```

# Background and Environment

These settings control ambient color, haze density and the background.

```
  studio {
    haze            f             // Haze density (black)
    haze            f r g b       // Haze density and color
    ambient         r g b         // Ambient color
    background      r g b         // Solid background color
    background      {}            // Color plane background
  }
```

## Haze

Sets the haze density. Optionally, sets the haze color.

```
  studio {
    haze            f             // Haze density (black)
    haze            f r g b       // Haze density and color
  }
```

The default is density 0, which means no haze effect.

The default color is black.

## Ambient

```
  studio {
    ambient         r g b         // Ambient color
  }
```

The ambient color for the scene. If you're going to use lights, this should
be set rather low for best results.

The default is black { 0 0 0 }.

## Background

```
  studio {
    background      r g b         // Solid background color
    background      {}            // Color plane background
  }
```

The background may be an inner structure, so it's discussed in a chapter
of its own.

* See: [Background][bkg]

# Session

Bob allows for rendering partial scenes in sessions. It also allows continuing
a session that was interupted due to a fatal error.

You can also set the dimensions of the output image.

```
  studio {
    start           line          // Session start line
    stop            line          // Session stop line
    resolution      w h           // View dimensions
  }
```
By default, the `start` line is set to 0 and the `stop` line is set to the
height of the display minus 1.

By default, the `resolution` is set to 320x240.

# Camera

Since the camera is such a large topic, it has a chapter all its own.

* See: [Camera][camera]

# System

```
  studio {
    bunching        i             // Composite shape bunch size
    depth           i             // Maximum recursion depth
    threshold       i             // Adaptive threshold

    no_exp_trans                  // Disable experimental transparency
    no_shadows                    // Disable shadows
    caustics                      // Enable caustic effects

    antialias       none          // No antialiasing
    antialias       corners       // Average four pixel corners
    antialias       quick         // Quick sliding window
    antialias       adaptive      // Adaptive sliding window
  }
```

## Bunching

> This determines the maximum number of primitives that can be bunched together into a composite object.

```
  studio {
    bunching        i             // Composite shape bunch size
  }
```

The default is 4 (macro BUNCHINGFACTOR).

* See: [Primitive Objects][prim]
* See: [Composite Objects][comp]

## Depth

> This determines the maximum recursion depth for a ray.

```
  studio {
    depth           i             // Maximum recursion depth
  }
```

The default is 20 (macro MAXLEVEL).

Larger values increase rendering time and consume more resources.

## Threshold

> This is the threshold for adaptive antialiasing.

```
  studio {
    threshold       i             // Adaptive threshold
  }
```

The default is 8.

It should be an integer in the range 0 to 255.

This determines when a ray is "close enough" to avoid further
sampling.

## No Transparency

> Turns off transparency.

```
  studio {
    no_exp_trans                  // Disable experimental transparency
  }
```

When present, this flag turns off tranparency globally.

## No Shadows

> Turns off shadows.

```
  studio {
    no_shadows                    // Disable shadows
  }
```

When present, this flag turns off shadows globally.

## Caustics

> Turns on caustics.

```
  studio {
    caustics                      // Enable caustic effects
  }
```

When present, this flag turns on experimental caustics.

Caustics are the effect that a ray experience when inside
of a partially transparent shape. This is a fudged effect,
since the real calculations would take too much time by far.

## Antialiasing

> Sets the antialiasing mode.

```
  studio {
    antialias       none          // No antialiasing
    antialias       corners       // Average four pixel corners
    antialias       quick         // Quick sliding window
    antialias       adaptive      // Adaptive sliding window
  }
```

The default is none.

* See [AA Mode][aa_mode]

---

# Overrides

Many of these settings can be overridden from the command line.

| Switch | Studio Setting | Notes |
|-|-|-|
| -i | resolution | 1 |
| -l | start, stop | 1 |
| -n | no_shadows | 2 |
| -d | depth | 3 |
| -a | antialias | 3 |
| -b | bunching | 3 |

### Notes

1. Session
2. Environment
3. System
4. Camera

* See: [Bob][bob]

# Synonyms

The following synonyms are applicable.

| Keyword | Synonym |
| - | - |
| center | translate |
| position | translate |
| offset | translate |
| from  | translate |
| res | resolution |
| bkg | background |

---
