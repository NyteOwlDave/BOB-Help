<link rel="stylesheet" href="../assets/help.css"/>

[dib]: <https://en.wikipedia.org/wiki/BMP_file_format>

# Bitmap Header (bmphdr)

Pixel maps formats can be complicated. The Windows DIB (BMP) format is no
exception. This tool allows you to list either (or both) the

* BITMAPFILEHEADER
* BITMAPINFOHEADER

For more details on these headers:

* See: [Windows DIB][dib]

# Usage

```
bmphdr [flags] <filename>
```

The filename must include the `.bmp` extension.

| Flag | Description | Notes |
|-|-|-|
| -h | Show BITMAPFILEHEADER | 1, 2 |
| -i | Show BITMAPINFOHEADER | 1, 2 |

### Notes

1. At least one flag must be present
2. Flags may be combined

---
