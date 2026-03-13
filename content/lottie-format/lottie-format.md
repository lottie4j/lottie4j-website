+++
title = "The Lottie Format"
weight = 2
+++

## The Lottie Format

Lottie files are JSON documents that describe vector animations frame by frame. The format includes:

* **Layers**: Shape layers, solid layers, image layers, text layers, etc.
* **Shapes**: Paths, rectangles, ellipses, and more
* **Animations**: Keyframe-based animations for position, scale, rotation, opacity, and other properties
* **Effects**: Fills, strokes, gradients, and various visual effects
* **Assets**: Embedded or referenced images, fonts, and precompositions

### Example Structure

```json
{
  "v": "5.5.7",
  "fr": 60,
  "ip": 0,
  "op": 180,
  "w": 1920,
  "h": 1080,
  "nm": "Animation Name",
  "ddd": 0,
  "assets": [],
  "layers": []
}
```

## Format Version History

The Lottie format has evolved over time. The version is specified in the `v` field of the JSON file:

* **v4.x**: Early versions with basic shape and animation support
* **v5.x**: Added support for expressions, effects, and more complex animations
* **Current**: Ongoing improvements for better feature support and performance

## Feature Support

Not all Lottie players support every feature of the format. Common limitations include:

* Expression support varies by platform
* Some After Effects features are not supported
* Text rendering may differ across implementations
* 3D layers have limited support

Always test your animations on target platforms to ensure compatibility.

## Getting Started

To work with Lottie animations:

1. **Create**: Design animations in Adobe After Effects or one of the other tools.
2. **Export**: Use the Bodymovin plugin to export as Lottie JSON.
3. **Optimize**: Use tools (like you can find on [LottieFiles](https://lottiefiles.com/)) to optimize file size.
4. **Implement**: Integrate using platform-specific Lottie libraries (like Lottie4J for JavaFX).
5. **Test**: Verify animation behavior across devices and platforms.
