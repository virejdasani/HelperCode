# HelperCode
### Table of contents
<details>
        <summary><a href="#electron">Electron</a></summary>
        <a href="#electron">Main.js File</a>
        </br>
        <a href="#open-links-in-external-browser">Open Links In External Browser</a>
        </br>
        <a href="#build-and-package-electron-apps">Build And Package Electron Apps</a>
</details>
<details>
        <summary><a href="#github">GitHub</a></summary>
        <a href="#github-downloads">GitHub Downloads</a>
</details>
<details>
        <summary><a href="#terminal">Terminal</a></summary>
        <a href="#colors-in-the-terminal">Colors In The Terminal</a>
</details>
<details>
        <summary><a href="#vim">Vim</a></summary>
</details>
<details>
        <summary><a href="#python">Python</a></summary>
</details>
<details>
        <summary><a href="#android">Android</a></summary>
</details>

<div id="electron" align="center">
        <h1>Electron</h1>
</div>

- ### Main.js File
```javascript
const {
    app,
    BrowserWindow
} = require('electron')


function createWindow() {
    const win = new BrowserWindow({
        width: 1228,
        height: 800,
        minWidth: 620,
        minHeight: 300,
        webPreferences: {
            webviewTag: true,
            // This is to zoom out in the app window
            zoomFactor: 0.60
        }
    })

    // and load the index.html of the app.
    win.loadFile('index.html')

    // Open the DevTools.
    // win.webContents.openDevTools()
}

// When app is ready
app.whenReady().then(() => {
    createWindow()

    app.on('activate', function () {
        // On macOS it's common to re-create a window in the app when the
        // dock icon is clicked and there are no other windows open.
        if (BrowserWindow.getAllWindows().length === 0) createWindow()
    })
})

// Quit when all windows are closed, except on macOS. There, it's common
// for applications and their menu bar to stay active until the user quits
// explicitly with Cmd + Q.
app.on('window-all-closed', function () {
    if (process.platform !== 'darwin') app.quit()
})
```

- ### Open Links In External Browser
```
$ npm install open
```
- Then, add the following to `main.js`
```javascript
const open = require('open')
```
- Then add this in the `createWindow` function
```javascript
    // This opens all links with `target="_blank"` attribute in external browser
    window.webContents.on('new-window', function (event, url) {
        event.preventDefault()
        open(url)
    })
```
- This will open links in tags like `<a href="https://google.com" target="_blank">Open Google</a>` in the users default browser

- ### Build And Package Electron Apps
- For MacOS
```
electron-packager . "App Name" --platform=darwin --arch=x64 --icon=path/to/icon.icns --ignore=builds
```
- For Windows
```
electron-packager . "App Name" --platform=win32 --arch=x64 --icon=path/to/icon.ico --ignore=builds
```
- For Linux
```
electron-packager . "App Name" --platform=linux --arch=x64 --icon=path/to/icon.png --ignore=builds
```

<div id="github" align="center">
        <h1>GitHub</h1>
</div>

- ### GitHub Downloads
```
$ curl -s https://api.github.com/repos/virejdasani/codebox/releases | egrep '"name"|"download_count"'
```

<div id="terminal" align="center">
        <h1>Terminal</h1>
</div>

- ### Colors In The Terminal
- Add this to Python code
```python
class text_color:
        black = '\033[30m'
        red = '\033[31m'
        green = '\033[32m'
        yellow = '\033[33m'
        blue = '\033[34m'
        magenta = '\033[35m'
        cyan = '\033[36m'
        white = '\033[37m'

# START MAIN
print text_color.yellow + "YAY"
```

<div id="vim" align="center">
        <h1>Vim</h1>
</div>

- ### Vim Commands
```
hjkl - for navigation -> k = kick UP
i - insert
a - same as i but insert to the right of char
capital i - insert at the beginning of line 
capital A - same as a but insert at the right of the line
dd - delete line
x - delete right
u - undo
:q! - quit and dont save
:! python3 main.py - run shell commands after :!
:line number - jump to that line number
v - start selecting
capital v - select whole line
y - copy/yank
p - paste
d - delete
r - replace

Search and Replace
:%s/searchWord/replaceWord/g
Add the g at the end to search the whole file (global)

To comment code =>
First select all code to comment out
Now, enter->
:norm i#
OR
:norm i//
etc. Remember to add a space after the comment char
```

<div id="python" align="center">
        <h1>Python</h1>
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
        <h1>Android</h1>
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
