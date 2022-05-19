<link rel="stylesheet" href="./assets/help.css"/>

# TODO

* Add paths file
* stop_line logic
* OpenHelpFile function
* Title function
* Prompt (console) modules
* Degenerate cases
* Tools
* Haze Color
* Memory management
* Object Generators
* Sprites
* Text

# Add Paths File

I'd like to add a simple text file that contains search paths.

As of right now, the `general-file.c` source file loads search paths
from the `BOB` environment variable. It would be nice to overload
search paths with an external text file as well.

# Stop Line Logic

The stop line logic appear broken to me. Where (if ever) does it get
set prior to calling `enact_command_options`?

This is in the file `genera-main.c`.

# OpenHelpFile Function

The `OpenHelpFile()` function in `system.c` needs rewritten.

# Title Function

The `Title()` function in `system.c` needs rewritten.

# Prompt (Console) Modules

Finish the modules for the diagnostic console mode.

# Degenerate Cases

The interpreter should check for all degenerate cases when
building primitives.

# Tools

There are a couple of Chum image converters that need rewritten. Namely. those that
deal with PPM, PCX, GIF, and TGA files.

Also, write an `optpal` tool. It creates an optimal palette from a 24-bit image.

Need a tool to convert BMP (or PNG) to IMG files

# Memory Management

In bob, the clip stack and the transform stack may cause memory leaks. Both
allocate dynamic structures and do not release them when popping.

# Object Generators

Ray Tracing Chapter 12 has some cool shape generators.

Also, my Fractal tools might be used as well.

# Sprites

Sprites and 2D graphics effects over top of the 3D scene.

# Text

Text over top of the 3D scene.

3D fonts.

# Convert BC to MAP

Tool to convert a BC file to a MAP file.

Perhaps CLISP?

---
