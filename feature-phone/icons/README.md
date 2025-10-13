# Icons for KaiOS/JioPhone

## Required Icons:
- icon-56.png (56x56 pixels)
- icon-112.png (112x112 pixels)

## How to Create Icons:

### Option 1: Use an online tool
1. Go to: https://www.favicon-generator.org/
2. Upload your Pacman image
3. Download 56x56 and 112x112 sizes

### Option 2: Use Photoshop/GIMP
1. Create 56x56 px image
2. Create 112x112 px image
3. Export as PNG

### Option 3: Use command line (ImageMagick)
```bash
convert pacman.png -resize 56x56 icon-56.png
convert pacman.png -resize 112x112 icon-112.png
```

## Temporary Placeholder:
For testing, you can use data URIs in manifest.webapp or create simple colored squares.

## Design Guidelines:
- Use simple, recognizable Pacman character
- Yellow background (#FFFF00) recommended
- Black or transparent background
- High contrast for small screens
- No text (too small to read at 56px)

