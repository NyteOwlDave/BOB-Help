<link rel="stylesheet" href="../assets/help.css"/>

# Circle

The circle tool creates a list of raw points that map at regular intervals
around the edge of a circle. This could also be used to create a regular
polygon with n sides.

# Usage

```
circle <radius> <numverts>
```

# Radius

The radius can be an valid real number greater than zero.

# Number of Vertices

The vertex count can be any valid integer greater than two.

# Output

The output is directly to the standard output stream. Redirect to capture
to a file.

Only raw vectors are emitted. Although each vector has three elements,
the third is always zero.

# Future Enhancements

Future enhancements might include using a custom surface normal
to orient the circle.

---

