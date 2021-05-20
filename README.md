# HelperCode
### Table of contents
- [Electron](#electron)
- [GitHub](#github)
- [Terminal](#terminal)
- [Python](#python)
- [Android](#android)

<div id="electron" align="center">
        <h2>Electron</h2>
</div>

- ### Build Electron Apps
- For MacOS
```
electron-packager . "App Name" --platform=darwin --arch=x64 --icon=path/to/icon.icns
```
- For Windows
```
electron-packager . "App Name" --platform=win32 --arch=x64 --icon=path/to/icon.ico
```
- For Linux
```
electron-packager . "App Name" --platform=linux --arch=x64 --icon=path/to/icon.png
```

<div id="github" align="center">
        <h2>GitHub</h2>
</div>

- ### GitHub Downloads
```
$ curl -s https://api.github.com/repos/virejdasani/codebox/releases | egrep '"name"|"download_count"'
```

<div id="python" align="center">
        <h2>Python</h2>
</div>

- ### Make `.exe` Of Python Code
- Run this terminal command in the directory of the `main.py` file:

```
$ pyinstaller --onefile -w main.py
```

- The -w is if you dont want the program to run in the terminal
- So, adding -w will not open terminal
- If terminal is needed, remove the -w

- Then delete the `.spec` file 
- Delete the build folder
- The `.exe` is in the dist folder

<div id="android" align="center">
        <h2>Android</h2>
</div>

- ### Animation for any view
```java
//For Animation

private ObjectAnimator anim;

public void startAnimation(View view) {
        anim.start();
    }

 anim = ObjectAnimator.ofFloat(view, "rotation", 0, 360);
                anim.setDuration(650);
                anim.setRepeatCount(0);
                anim.setRepeatMode(ObjectAnimator.RESTART);
                startAnimation(view);
```

- ### Creator Activity (XML)
```xml
//CreatorActivity

?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#000000"
    tools:context=".CreatorActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <TextView
            android:id="@+id/textView8"
            android:layout_width="match_parent"
            android:layout_height="189dp"
            android:text="TextView" />

        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Developed by:   Virej Dasani"
            android:textAlignment="center"
            android:textColor="#ffffff"
            android:textSize="60dp" />

        <TextView
            android:id="@+id/textView9"
            android:layout_width="match_parent"
            android:layout_height="50dp"

            android:text="." />

        <TextView
            android:id="@+id/textView7"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Instagram: @_virej_"
            android:textColor="#ffffff"
            android:textAlignment="center"
            android:textSize="40sp" />

        <TextView
            android:id="@+id/textView11"
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:text="TextView" />

        <TextView
            android:id="@+id/textView10"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:textColor="#ffffff"
            android:textSize="18dp"
            android:text="Contact us: dasanivirej@gmail.com" />
    </LinearLayout>

</LinearLayout>
```

- ### Firebase Example
```java
package com.virej.packagename;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import android.text.Editable;
import android.util.Log;
import android.view.View;
import android.view.WindowManager;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;


public class MainActivity extends AppCompatActivity {

    public EditText email;
    public EditText password;
    public Button submit;
    public TextView answerTextView;


    @Override
    public void onPause() {
        super.onPause();
        overridePendingTransition(0, 0);
    }


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

//For fullscreen
        getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN,
                WindowManager.LayoutParams.FLAG_FULLSCREEN);

        email = findViewById(R.id.editTextEmail);
        password = findViewById(R.id.editTextPassword);
        submit = findViewById(R.id.submitButton);
        answerTextView = findViewById(R.id.answerTextView);


        submit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                String emailString = email.getText().toString();
                String passwordString = password.getText().toString();
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
                // Write a message to the database
                FirebaseDatabase database = FirebaseDatabase.getInstance();

                DatabaseReference myRef = database.getReference("email");
                DatabaseReference myRef1 = database.getReference("password");

                myRef1.setValue(passwordString);
                myRef.setValue(emailString);
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

// For splash screen functions  
                new Handler().postDelayed(new Runnable() {

// Using handler with postDelayed called runnable run method

                    @Override
                    public void run() {

                        Intent i = new Intent(MainActivity.this, UnavailableActivity.class);

                        startActivity(i);

                        // close this activity
                        finish();
                    }
                }, 15*1000); // wait for 5 seconds
            }
        });
    }
}
```

- ### Fullscreen App
```java
// Put this code in the java code of the app to make it fullscreen
getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN,
            WindowManager.LayoutParams.FLAG_FULLSCREEN);
```

- ### Function To Round Number In Java
```java
// Function to round doubles
    public static double round(double value, int places) {
        if (places < 0) throw new IllegalArgumentException();

        long factor = (long) Math.pow(10, places);
        value = value * factor;
        long tmp = Math.round(value);
        return (double) tmp / factor;
    }
    
// Use round(any mathematical expression, num of spaces to round)
```

- ### In-App Sounds
```java
// For sound output
final MediaPlayer diceSoundMP = MediaPlayer.create(this, R.raw.dicerollvirtualdicesound);
        
diceSoundMP.start();
```

- ### Splash Screen
```java
// Using handler with postDelayed called runnable run method

        new Handler().postDelayed(new Runnable() {

            @Override
            public void run() {

                Intent i = new Intent(TwoActivity.this, ThreeActivity.class);

                startActivity(i);

                // close this activity
                finish();
            }
        }, 5*1000); // wait for 5 seconds
```

