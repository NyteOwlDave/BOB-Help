<link rel="stylesheet" href="../assets/help.css"/>

[bmp]: <https://docs.microsoft.com/en-us/windows/win32/api/wingdi/ns-wingdi-bitmapv4header>

# Chum Toolkit

The main folder contains a collection of image processing tools. Currently this consists of some image file conversion commands.

# Image File Formats

| Name | Purpose | Notes |
|-|-|-|
| BMP | Windows DIB | |
| IMG | BOB Ray Tracer Image | |
| PIC | NCS Picture | |
| RAW | NCS Raw Image | |
| VGA | NCS VGA Image | |
| PPM | Portable Pixel Map Image | 1 |
| PCX | Paintbrush Image | 1 |
| GIF | Graphics Exchange Format Image | 1 |
| TGA | Targa Image | 1 |
| BC | Bob Color Definitions | 1 |
| PAL | NCS Palette | 1 |
| RIFF | Win32 RIFF Palette | 1 |
| MAP | Bob Palette  | 1 |

### Notes
1. This is not yet implemented.

## BMP - Windows DIB

This one is far too complex to summarize easily. Refer to Microsoft docs for the DIB file format BI_RGB.

* See: [Bitmap Format][bmp]

## IMG - BOB Ray Tracer Image

This run length encoded format comes from the book
_Photorealism and Ray Tracing in C_. It's used by the BOB Ray Tracer provided
by that book, as well as a number of apps I've designed.

The header is 10 bytes long. This is broken up into 5 fields:

1. Width
2. Height
3. Start Line
4. Stop Line
5. Bits per pixel

NOTE: All fields are in BIG-ENDIAN (Motorola) byte order.

Width and height are unsigned (1-65535). Same for Start and Stop Line. Zero for start and stop line indicates full size image. Otherwise, these can be used to determine partial images that span multiple rendering sessions. Bits per pixel must be 24.

Scanlines are RLE encoded, with anywhere from 0 to 255 pixels in a run. Extra pixels are ignored. Missing pixels are undefined. Note that because of the way this is encoded, it's possible for the sum of pixels for a logical scanline to not match the image width. Some tools try to handle this gracefully, but it may cause a load failure for some. Those that handle it gracefully will generally produce mangled results beginning at the point of misalignment.

Each run is a single length byte, followed by B, G then R byte fields.

__NOTE__ For compatibility with the BOB app, run lengths should be in the range 1 to 254. No zero length runs or runs of length 255 are permitted.

## PIC - NCS Picture

This is a planar type based on the one introduced in the book
_Practical Ray Tracing in C_.

The file consists of a simple header, which is two unsigned 16-bit integers
defining the width and height (1-65535). This is immediately followed by a series of scanlines. The (dis)advantage of this format is that each scanline is written in three color planes (R, then G, then B) rather than each pixel containing all three color components. Each scanline also begins with an unsigned 16-bit word, which is the length of the scanline in pixels. Theoretically this could allow for truncated lines, but this is not done in the code. Rather each scanline length should equal the image width from the header.

## RAW - NCS Raw Image

This is a custom format I came up with for use with Linux apps. Silly of me to create yet another format.

This has a short header, followed by a series of scanlines in ARGB format. This is the same format used by Windows DIBs and the HTML5 2D graphics context.

The header is the signature string "RAW" followed by a NULL (zero) byte, then the image dimensions. First height then width as 16-bit unsigned values (1-65535).

## VGA - NCS VGA Image

This is an extremely simple format I came up with to compete with the BOB Ray Tracer image file format. Whereas IMG files are compressed as RLE, and have some extra header info, this just uses raw ARGB pixel scanlines.

The header contains just two signed 32-bit integers, one for each image dimension. This allows for some incredibly large images and also had lots of values that are out of range (0 and negative values). In this format, the width is first followed by the height.

PPM - Portable Pixel Map Image

> NOT YET IMPLEMENTED

PCX - Paintbrush Image

> NOT YET IMPLEMENTED

GIF - Graphics Exchange Format Image

> NOT YET IMPLEMENTED

TGA - Targa Image

> NOT YET IMPLEMENTED

BC - Bob Color Definitions

> NOT YET IMPLEMENTED

PAL - NCS Palette

> NOT YET IMPLEMENTED

RIFF - Win32 RIFF Palette

> NOT YET IMPLEMENTED

MAP - Bob Palette

> NOT YET IMPLEMENTED

---
