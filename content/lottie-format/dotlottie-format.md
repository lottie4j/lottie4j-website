+++
title = "The dotLottie Format"
weight = 3
+++

## The dotLottie Format

dotLottie (`.lottie`) is an enhanced container format for Lottie animations that addresses several limitations of the original JSON format. It's essentially a ZIP archive that can contain:

* **Multiple animations**: Package several related animations in a single file
* **Images and assets**: Embed all required images directly in the file
* **Manifest file**: Metadata about the animations, including IDs, names, and themes
* **Optimized storage**: Compressed format reduces file sizes even further

### Benefits of dotLottie

* **Self-contained**: All assets are bundled together, no external dependencies
* **Better organization**: Multiple animations and themes in one package
* **Smaller file sizes**: ZIP compression reduces overall file size
* **Version control friendly**: Binary format is more efficient than large JSON files
* **Multi-animation support**: Perfect for animation sets like icons or loading states

### File Structure

A `.lottie` file is a ZIP archive with this typical structure:

```
animation.lottie
├── manifest.json          # Metadata and animation definitions
├── animations/
│   ├── animation1.json   # Individual Lottie JSON files
│   └── animation2.json
└── images/               # Embedded image assets
    ├── image1.png
    └── image2.png
```

### Example Manifest

```json
{
  "version": "1.0",
  "author": "Designer Name",
  "generator": "dotLottie",
  "animations": [
    {
      "id": "animation1",
      "speed": 1,
      "themeColor": "#ffffff",
      "loop": true
    }
  ]
}
```

### Creating dotLottie Files

You can create dotLottie files using:

* [LottieFiles Platform](https://lottiefiles.com/): Export animations as dotLottie
* [dotLottie-js](https://github.com/dotlottie/dotlottie-js): JavaScript library for creating and manipulating dotLottie files
* [After Effects Plugin](https://lottiefiles.com/plugins/after-effects): Export directly from After Effects

### Using dotLottie with Lottie4J

Lottie4J supports loading dotLottie files directly. The library handles decompression and asset extraction automatically:

```java
File file = new File("src/test/resources/dot/demo-3.lottie");

// Get the first animation in the .lottie package
Animation animation = LottieFileLoader.load(File);

// Load as a DotLottie object for more advanced features
DotLottie dot = LottieFileLoader.loadDotLottie(file);
System.out.println("Animations in package: " +
    (dot.animations() == null ? 0 : dot.animations().size()));
```

### When to Use dotLottie

Use dotLottie when you need:

* Animations with external image assets
* Multiple related animations in one package
* Smaller file sizes for web delivery
* Better organization for complex animation projects
* Theme support (light/dark mode variations)

For simple vector-only animations, standard Lottie JSON files are sufficient.
