<link rel="stylesheet" href="../assets/help.css"/>

# Texture Maps

Texture maps allow you to map a color image to a surface.
The image comes from an image file.

Surfaces are strongly affected by light. For lighting and other
related links:

* [See Also](see-also.html)

# Usage

```
surface {
    <texmap>  {                     // Any texture map
        position    x y z           // Location of upper left corner
        across      x y z           // Vector pointing across the top edge
        normal      x y z           // Surface normal
        scale       x y z           // Scale
        scale       f               // Scale
        image       filename.img    // Texture image filename
    }
}
```

The `<texmap>` token is a placeholder for any of the four texture map types:

* ambient
* diffuse
* specular
* transparent

# Placement

Bob uses these parameters to compose a texturing matrix for the surface.

```
surface {
    <texmap>  {                     // Any texture map
        position    x y z           // Location of upper left corner
        across      x y z           // Vector pointing across the top edge
        normal      x y z           // Surface normal
    }
}
```

The `position` keyword determine where in 3D space the upper lef corner
of the texture will be anchored.

The `across` keyword is a vector that gives the direction of the top
edge of the texture.

The `normal` keyword is a vector that gives the surface normal.

# Scale

```
surface {
    <texmap>  {                     // Any texture map
        scale       x y z           // Scale
        scale       f               // Scale
    }
}
```

This sets the scale of the texture.

The default is 1.0 (no scaling).

There are two forms: _uniform_ and _discrete_. Uniform just takes
a single argument and applies it to all three dimensions. Discrete
takes three arguments -- one for each dimension.

# Image

```
surface {
    <texmap>  {                     // Any texture map
        image       filename.img    // Texture image filename
    }
}
```

This determines the actual file that provides the color map for
texels. Currently only BOB images are supported.

# Synonyms

The following synonyms are applicable.

| Keyword | Synonym |
| - | - |
| diffuse | diff |
| specular | spec |
| surface | surf |
| transparent | xpar |

---