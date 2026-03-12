+++
title = "Code Examples"
weight = 30
+++

Lottie4J requires Java 21 or higher.

## Including the Library in Your Project

This library is available from Maven Central.

If you only need the API to load and/or save Lottie json files:

```xml
<dependency>
    <groupId>com.lottie4j</groupId>
    <artifactId>core</artifactId>
    <version>${lottie4j.version}</version>
</dependency>
```

If you want to use the JavaFX LottiePlayer, which includes the core library:

```xml
<dependency>
    <groupId>com.lottie4j</groupId>
    <artifactId>fxplayer</artifactId>
    <version>${lottie4j.version}</version>
</dependency>
```

## Minimal Code Examples

### Using the Core Library

```java
import com.lottie4j.core.loader.LottieFileLoader;
import com.lottie4j.core.model.Animation;

import java.io.File;
import java.io.IOException;

public class MinimalExample {
    public static void main(String[] args) throws IOException {
        // Load a Lottie JSON file
        File lottieFile = new File("animation.json");
        Animation animation = LottieFileLoader.load(lottieFile);
        
        // Access animation properties
        System.out.println("Animation: " + animation.name());
        System.out.println("Version: " + animation.version());
        System.out.println("Dimensions: " + animation.width() + "x" + animation.height());
        System.out.println("FPS: " + animation.framesPerSecond());
        System.out.println("Duration: " + (animation.outPoint() - animation.inPoint()) + " frames");
        System.out.println("Layers: " + animation.layers().size());
    }
}
```

## Using the JavaFX LottiePlayer

```java
import com.lottie4j.core.loader.LottieFileLoader;
import com.lottie4j.core.model.Animation;
import com.lottie4j.fxplayer.LottiePlayer;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.stage.Stage;

import java.io.File;

public class DemoApplication extends Application {

    static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage stage) throws Exception {
        File lottieFile = new File("PATH_OF_LOTTIE_FILE.json");

        Animation animation = LottieFileLoader.load(lottieFile);

        var scene = new Scene(new LottiePlayer(animation),
                animation.width() != null ? animation.width() : 500,
                animation.height() != null ? animation.height() : 500
        );
        stage.setTitle(lottieFile.getName());
        stage.setScene(scene);
        stage.show();
    }
}
```