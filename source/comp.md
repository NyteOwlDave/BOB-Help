<link rel="stylesheet" href="./assets/help.css"/>

[studio]: <./studio/studio.html>
[prim]: <prim.html>

# Composites

Bob employs a BSP technique known as **bounding slabs**.

This technique uses a **median cut** method to attempt to
balance the tree.

Currently, the slabs are boxes (six sided cubics), but
provisions are stubbed out in code for a more refined
shape using any number of planes.

Any primitive(s) can be used in a composite. Each composite
maintains a list of the primitives it owns.

* See: [Primitive Objects][prim]

# Usage

The only configurable part of the BSP engine is the maximum
size of a bunch. 

This is set in the `studio` structure.

```
studio {
    bunching i             // Composite shape bunch size
}
```

* See: [studio][studio]

---
