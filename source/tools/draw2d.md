<link rel="stylesheet" href="../assets/help.css"/>

# Draw 2D (draw2d)

This tool supplements Bob's 3D capabilities by providing a set of
2D graphics. Generally, the 2D graphics are overlaid over a 3D
image that has been produced by Bob. However, it can function as
a standalone system.

# Features

There are several broad categories of features:

1. Pixel and line drawing
2. Filled shapes
3. Bitmap and sprite blitting
4. Device Context
5. Text
6. Transforms

# Pixels

The pixel function is very simple: read or write a solid pixel.

# Lines

The line drawing functions offer dashed features as well as
color blending, but no texturing.

# Filled Shapes

The filled shapes offer solid coloring, blending, texturing and blended textures.

# Blitting and Sprites

The blit functions offer texturing and blended texturing. The sprite functions
also feature using a stencil (keyed to a transparent color).

# Device Contexts

The device context functions manage settings used by all the other features.

# Text

The text functions are currently pending. The intention is to provide
fixed-pitch, variable-pitch and vector fonts.

# Transforms

The `gdi` library, which is the backbone of the draing tool, contains a
subsection devoted to geometric primitives (point, size, rect) as well
as vector and matrix math for transformations.

# Status

This tool is currently under development. Completion is shown below:

| Feature | Solid | Dotted | Blended | Notes |
|-|-|-|-|-|
| DrawPoint    | X | . | . | 1 |
| DrawPoints   | X | . | . | 1 |
| DrawHLine    | X | X | X |  |
| DrawVLine    | X | X | X |  |
| DrawLine     | X | X | X |  |
| DrawPolyLine | X | X | X |  |
| DrawLineList | X | X | X |  |
| DrawCircle   | X | X | X |  |
| DrawEllipse  | . | . | . |  |
| DrawPatch    | . | . | . |  |
| DrawPoly     | . | . | . |  |
| DrawRect     | X | X | X |  |

| Feature | Solid | Blended | Textured | Textured Blended | Notes |
|-|-|-|-|-|-|
| FillCircle  | X | X | X | X | |
| FillEllipse | . | . | . | . | |
| FillPatch   | . | . | . | . | |
| FillPoly    | . | . | . | . | |
| FillRect    | X | X | X | X | |

| Feature | Textured | Textured Blended | Notes |
|-|-|-|-|
| BlitImage    | X | X | |
| StretchImage | X | X | |

### Notes

1. No special rendering

---

