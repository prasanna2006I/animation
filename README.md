# Ex.No: 6 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


# AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

# EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

# ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Design xml files for all operations such as blink, rotate, move, slide, zoom, fade.

Step 6: Display the button operations in MainActivity file.

Step 7: Save and run the application


# PROGRAM:
```
/*
Program to display animation operation”.
Developed by: PRASANNA I
Registeration Number :212223220079
*/
```
## MAIN_ACTIVITY.JAVA
```
package com.example.animation;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    Button blinkBtn, fadeBtn, moveBtn, rotateBtn, slideBtn, zoomBtn, stopBtn;
    Animation currentAnimation;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blinkBtn = findViewById(R.id.blinkBtn);
        fadeBtn = findViewById(R.id.fadeBtn);
        moveBtn = findViewById(R.id.moveBtn);
        rotateBtn = findViewById(R.id.rotateBtn);
        slideBtn = findViewById(R.id.slideBtn);
        zoomBtn = findViewById(R.id.zoomBtn);
        stopBtn = findViewById(R.id.stopBtn);

        blinkBtn.setOnClickListener(v -> startAnimation(R.anim.blink));
        fadeBtn.setOnClickListener(v -> startAnimation(R.anim.fade));
        moveBtn.setOnClickListener(v -> startAnimation(R.anim.move));
        rotateBtn.setOnClickListener(v -> startAnimation(R.anim.rotate));
        slideBtn.setOnClickListener(v -> startAnimation(R.anim.slide));
        zoomBtn.setOnClickListener(v -> startAnimation(R.anim.zoom));

        stopBtn.setOnClickListener(v -> stopAnimation());
    }

    private void startAnimation(int animRes) {
        stopAnimation(); // stop if already animating
        currentAnimation = AnimationUtils.loadAnimation(this, animRes);
        imageView.startAnimation(currentAnimation);
    }

    private void stopAnimation() {
        if (currentAnimation != null) {
            currentAnimation.cancel();
            imageView.clearAnimation();
        }
    }
}
```
## ACTIVITY MAIN.XML
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:orientation="vertical"
        android:gravity="center"
        android:padding="20dp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <ImageView
            android:id="@+id/imageView"
            android:layout_width="200dp"
            android:layout_height="200dp"
            android:layout_marginBottom="30dp"
            android:src="@drawable/csk" />

        <Button
            android:id="@+id/blinkBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Blink" />

        <Button
            android:id="@+id/fadeBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Fade" />

        <Button
            android:id="@+id/moveBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Move" />

        <Button
            android:id="@+id/rotateBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Rotate" />

        <Button
            android:id="@+id/slideBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Slide" />

        <Button
            android:id="@+id/zoomBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Zoom" />

        <Button
            android:id="@+id/stopBtn"
            android:layout_width="200dp"
            android:layout_height="wrap_content"
            android:text="Stop Animation"
            android:backgroundTint="#FF5252"
            android:textColor="#FFFFFF"
            android:layout_marginTop="10dp" />
    </LinearLayout>
</ScrollView>




```
## BLINK.XML
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />
```
## ROTATE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<rotate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromDegrees="0"
    android:toDegrees="360"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1500"
    android:repeatCount="infinite" />

```
## MOVE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXDelta="0%"
    android:toXDelta="75%"
    android:duration="1000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />
```
## FADE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:duration="2000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />
```
## SLIDE.XML
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromYDelta="100%"
    android:toYDelta="0%"
    android:duration="1000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />
```
## ZOOM.XML
```
<?xml version="1.0" encoding="utf-8"?>
<scale xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXScale="1.0"
    android:toXScale="1.5"
    android:fromYScale="1.0"
    android:toYScale="1.5"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatCount="infinite"
    android:repeatMode="reverse" />

```
# OUTPUT
## BLINK
<img width="1920" height="1080" alt="Screenshot 2025-10-29 091952" src="https://github.com/user-attachments/assets/77a65803-3807-4b85-9e62-4bf2b81a9bee" />

## FADE
<img width="1920" height="1080" alt="Screenshot 2025-10-29 092043" src="https://github.com/user-attachments/assets/cd58a819-89be-4167-bb85-c6eb17cbae2a" />

## MOVE
<img width="1920" height="1080" alt="Screenshot 2025-10-29 092112" src="https://github.com/user-attachments/assets/13313693-f2b3-4d3f-86cc-30459422d00b" />

## DEFAULT
<img width="1920" height="1080" alt="Screenshot 2025-10-29 091931" src="https://github.com/user-attachments/assets/14609c8f-a810-4244-a752-d027aa9a67c3" />


## RESULT
Thus a Simple Android Application to add animations: Move,blink,fade,clockwise,zoom,slide operations using Android Studio is developed and executed successfully.
