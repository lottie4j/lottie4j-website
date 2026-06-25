+++
title = "Lottie4J — Lottie Animations for Java & JavaFX"
description = "Lottie4J is an open-source Java library to parse Lottie animations into Java objects, generate Lottie files, and play them as native JavaFX animations, no WebView required."
type = "home"
+++

<div class="l4j-hero">
  <img class="l4j-hero-logo" src="/favicon/android-chrome-512x512.png" alt="Lottie4J logo" width="120" height="120" loading="eager">
  <h1 class="l4j-hero-title">Lottie Animations for Java &amp; JavaFX</h1>
  <p class="l4j-hero-sub">
    Parse, generate &amp; play Lottie animations natively in JavaFX.
    <br/>
    <strong>No WebView required.</strong>
  </p>
  <p class="l4j-hero-release"><span class="l4j-hero-dot"></span> Latest release: <a href="/releases/">v1.2.4 · 2026-06-15</a></p>
  <p class="l4j-hero-cta">
    <a class="l4j-btn l4j-btn-primary" href="#quick-start"><i class="fas fa-rocket"></i> Get Started</a>
    <a class="l4j-btn l4j-btn-ghost" href="https://github.com/lottie4j/lottie4j" target="_blank"><i class="fab fa-github"></i> View on GitHub</a>
  </p>
</div>

**Lottie4J is an open-source Java library that parses Lottie animations into Java objects and plays them as native JavaFX animations — no WebView, no browser engine, no JavaScript bridge.**

## Quick start

Lottie4J requires **Java 21 or higher** and is available from Maven Central. Add the `fxplayer` dependency (it includes the `core` library):

{{< tabs >}}
{{% tab title="Maven" %}}
```xml
<dependency>
    <groupId>com.lottie4j</groupId>
    <artifactId>fxplayer</artifactId>
    <version>1.2.4</version>
</dependency>
```
{{% /tab %}}
{{% tab title="Gradle (Kotlin)" %}}
```kotlin
implementation("com.lottie4j:fxplayer:1.2.4")
```
{{% /tab %}}
{{% tab title="Gradle (Groovy)" %}}
```groovy
implementation 'com.lottie4j:fxplayer:1.2.4'
```
{{% /tab %}}
{{< /tabs >}}

Then load a Lottie file and drop the player into your scene:

```java
Animation animation = LottieFileLoader.load(new File("animation.json"));
stage.setScene(new Scene(new LottiePlayer(animation),
        animation.width(), animation.height()));
stage.show();
```

See the [code examples](/code-examples/) for the full, runnable application and the core-only (parse/generate) usage.

## Why Lottie4J

{{< cards >}}
  {{% card title="Native JavaFX rendering" icon="fas fa-bolt" %}}
Animations are drawn directly to a JavaFX `Canvas`. No embedded browser, no JavaScript bridge — just a standard JavaFX `Node` you can style and lay out like any other.
  {{% /card %}}
  {{% card title="Parse &amp; generate" icon="fas fa-code" %}}
Read Lottie JSON into typed Java objects, inspect or modify them, and write valid Lottie files back out.
  {{% /card %}}
  {{% card title="Modern, minimal Java" icon="fab fa-java" %}}
Built on Java 21 LTS using Records to keep the codebase small and easy to maintain, test, and extend.
  {{% /card %}}
  {{% card title="Lightweight &amp; offline-first" icon="fas fa-feather" %}}
Needs only `javafx.graphics` — no `javafx.web`. That means a fast startup, a small jlink/jpackage footprint, and no network dependency.
  {{% /card %}}
{{< /cards >}}

Wondering how this compares to embedding a browser? Read [Lottie4J vs WebView](/lottie4j-vs-webview/).

The sources of this project are available on [github.com/lottie4j/lottie4j](https://github.com/lottie4j/lottie4j).

**Watch:** an introduction to Lottie4J — playing Lottie animations natively in JavaFX.

{{< youtube 9lE6UO8XNpU >}}

## Learn About Lottie

New to Lottie? Check out our [introduction to the Lottie format](/lottie-format/) to learn about this powerful animation format, its capabilities, and available resources.

## Current status

Lottie4J is released and under active development. The library can parse Lottie files into Java objects, generate Lottie files from Java objects, and play animations in JavaFX, including keyframe interpolation, animated properties, shape rendering, fills and gradients, stroke styling, trim paths, layer transforms and parenting. It already handles many complex real-world animations.

Follow the progress in the [status posts](/status/) and check the [release notes](/releases/) for the latest changes.
