+++
title = "About the Lottie Format"
weight = 10
+++

## What is Lottie?

Lottie is a JSON-based animation file format that enables designers to ship animations on any platform as easily as shipping static assets. Created by Airbnb, Lottie has become the industry standard for vector animations on mobile and web.

## Why Lottie?

* **Small file sizes**: Vector-based animations are significantly smaller than traditional video or GIF files
* **Scalable**: Works perfectly at any resolution without quality loss
* **Cross-platform**: Runs on iOS, Android, Web, and now Java with Lottie4J
* **Designer-friendly**: Animations are exported directly from Adobe After Effects using the Bodymovin plugin
* **Interactive**: Animations can be modified at runtime (colors, text, speed, etc.)

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

## Resources

### Official Lottie Project

* [Lottie Official Website](https://lottiefiles.com/what-is-lottie): Main website with documentation and examples
* [Lottie GitHub Repository](https://github.com/airbnb/lottie): Original iOS implementation
* [LottieFiles Platform](https://lottiefiles.com/): Browse, test, and download free Lottie animations

### Documentation & Specifications

* [Lottie Format Documentation](https://lottiefiles.github.io/lottie-docs/): Comprehensive format specification
* [Lottie Animation Community](https://github.com/LottieFiles/lottie-docs): Community-driven documentation
* [Bodymovin Plugin](https://aescripts.com/bodymovin/): Adobe After Effects plugin for exporting Lottie files

### Platform Implementations

* [lottie-web](https://github.com/airbnb/lottie-web): Web player for Lottie animations
* [lottie-android](https://github.com/airbnb/lottie-android): Android implementation
* [lottie-ios](https://github.com/airbnb/lottie-ios): iOS implementation
* [lottie-react-native](https://github.com/lottie-react-native/lottie-react-native): React Native wrapper
* [lottie4j](https://github.com/lottie4j/lottie4j): Java(FX) library (this project) on GitHub

### Tools & Editors

* [LottieFiles Editor](https://lottiefiles.com/editor): Online editor for Lottie animations
* [Lottie Creator](https://lottiefiles.com/creator): Create simple Lottie animations online

## Format Version History

The Lottie format has evolved over time. The version is specified in the `v` field of the JSON file:

* **v4.x**: Early versions with basic shape and animation support
* **v5.x**: Added support for expressions, effects, and more complex animations
* **Current**: Ongoing improvements for better feature support and performance

## Feature Support

Not all Lottie players support every feature of the format. Common limitations include:

* Expression support varies by platform
* Some After Effects effects are not supported
* Text rendering may differ across implementations
* 3D layers have limited support

Always test your animations on target platforms to ensure compatibility.

## Getting Started

To work with Lottie animations:

1. **Create**: Design animations in Adobe After Effects or one of the other tools
2. **Export**: Use the Bodymovin plugin to export as Lottie JSON
3. **Optimize**: Use tools like [LottieFiles](https://lottiefiles.com/) to optimize file size
4. **Implement**: Integrate using platform-specific Lottie libraries (like Lottie4J for Java(FX))
5. **Test**: Verify animation behavior across devices and platforms
