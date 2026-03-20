+++
title = "Lottie4J Releases"
weight = 10
+++

## 2026-03-20, 1.2.0

Many improvements after 1.1.0, with new .lottie format support, rendering fixes, performance work, and dependency updates.

{{< youtube 9lE6UO8XNpU >}}

* **Core**
  * Added `.lottie` (dotLottie) loader support.
  * Added support for merge and modifier shapes.
  * Added missing blend mode support.
  * Added spatial bezier interpolation for position animations.
  * Fixed model field types and added missing JSON properties for mask, layer, and animation objects.
  * Improved JSON output and value ordering when recreating JSON structures.
  * Upgraded to Jackson 3 (`tools.jackson`), including follow-up compatibility fixes and CVE-related dependency updates.
* **LottiePlayer** in module FXPlayer
  * Improved playback speed by reducing rendering passes.
  * Added caching of layer/precomp render metadata to improve heavy animation playback.
  * Added adaptive rendering mode toggle.
  * Made `LottiePlayer` resizable.
  * Added cropping support.
  * Integrated animated mask rendering.
  * Added play-between-markers.
  * Fixed last-frame/keyframe boundary issues that could cause disappearing layers.
  * Improved consistency in path stroke rendering.
  * Extended unit test to compare loaded and recreated JSON.
* **FXFileViewer**
  * Refactored duplicated WebView JavaScript bridge code into reusable components.
  * Improved FX vs JS debug views.
  * Improved compare test synchronization and added resized-player validation.
* **Project and docs**
  * Added Java 21 support and badge updates.
  * Fixed package names and build warnings, and completed additional JavaDoc cleanup.
  * General cleanup/restructuring and test improvements.
  * Added README/media updates and extra links.

The list of all changes between 1.1.0 and 1.2.0 is [available on GitHub](https://github.com/lottie4j/lottie4j/compare/v1.1.0...v1.2.0).

## 2026-03-10, 1.1.0

Many rendering improvements after testing more animations. This contains some API changes, that's the reason for the version bump to 1.1.0.

{{< youtube _zZ1q6zbRgM >}}

* Changed license to **Apache V2**
* Changed logging to **SLF4J**
* Code restructuring and **JavaDoc** improvements
* The **Core** module has been extended with new Java objects to support missing Lottie animation definitions related to the improvements in the player.
* **LottiePlayer** in module FXPlayer
  * Correctly close paths, fixing a gap in the thick border
  * Better border rendering
  * Added Track Matte support
  * Fix layer disappearance at exact keyframe boundaries
  * Fix gradient alpha channel parsing for correct transparency rendering
  * Added image layer rendering 
  * Fix GradientStroke deserialization conflict and color format
  * Added solid color layer rendering support
  * Added text objects and rendering
  * Improved animation handling
  * Added Gaussian Blur effect
  * Fixed layer opacity
  * Combine multiple trim paths 
  * Fixed the handling of animations starting later
  * Fixed stroke style for dotted lines
  * Fixed correct fade transitions for overlapping shapes
  * Improved gradient fills
* Extended **LottieFileDebugViewer** in module FXFileViewer to make it easier to compare JavaFX player with JavaScript player and debug differences:
  * Added screenshot buttons to save single or all frames
  * Added a tile viewer to visualize each layer
  * Layers/objects in a tile view can be exported as a new Lottie file to test specific rendering issues
* New **LottieFileSimpleViewer** in module FXFileViewer to show the animation in a simple way with the JavaFX player only.
* Integrated a unit test **CompareFxViewWithWebViewTest** in FXFileViewer to compare the JavaFX player with the JavaScript player, using a screenshot comparison approach. This test can not run on CI, because it requires a display output, but it can be run locally. Hopefully this can be fixed later with headless JavaFX, see [this issue](https://github.com/lottie4j/lottie4j/issues/4).

The list of all changes between 1.0.0 and 1.1.0 is [available on GitHub](https://github.com/lottie4j/lottie4j/compare/v1.0.0...v1.1.0).

## 2026-03-02, 1.0.0

The first release with many files tests and working OK. Still needs further improvements for more complex animations and drawings.

More info and details in [this blog post](/status/2026/20260302-2/) and check the older blog posts for the steps taken up to the first release.