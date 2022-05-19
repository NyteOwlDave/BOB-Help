<link rel="stylesheet" href="../assets/help.css"/>

[texmap]: <texmap.html>
[texproc]: <texproc.html>
[shine]: <surf.html#shine>
[ior]: <surf.html#ior>

# Solid Color

If you do not specify any procedural textures or texture maps, Bob generates a
surface with a solid color. Bump maps are okay here.

Surfaces are strongly affected by light. For lighting and other
related links:

* [See Also](see-also.html)

# RGB

The RGB values all use _normalized_ components. In other words, the values
are real numbers in the range `[0 .. 1]`.

This implies that in Bob colors are ordinary vectors. They are interchangeable.

# Ambient

This is the ambient color.

```
surf {
    ambient r g b
}
```

The default is black (0, 0, 0).

Ambient colors tend to wash out other colors, as they do not take into
account lighting.

# Diffuse

This is the diffuse color.
```
surf {
    diff r g b
}
```

The default is black (0, 0, 0).

The diffuse color is probably the most important and commonly used.
It adds color like ambient, but only when struck by light.

# Specular Color

This is the specular (reflective) color. Using this adds a mirrorlike
effect to the surface.

__NOTE__ Do not confuse this with [specular shine][shine].


```
surf {
    spec r g b
}
```

The default is black (0, 0, 0).

# Transmissive Color

The transmissive (transparent) color allows Bob to "see through"
an object to some extent.

```
surf {
    xpar r g b
}
```

The default is black (0, 0, 0).

Generally, unless you want a filter, this should be a gray scale value.
That is, R=G=B.

This is generally used with [ior][ior].

---

# Coefficients

If the shape has a texture map or procedural texture, these colors are
used as coefficients. Generally, this means best results will be obtained
by using gray scale values (R=G=B).

* See: [Texture Maps][texmap]
* See: [Procedural Textures][texproc]

# Synonyms

The following synonyms are applicable.

| Keyword | Synonym |
| - | - |
| diffuse | diff |
| specular | spec |
| surface | surf |
| transparent | xpar |

---