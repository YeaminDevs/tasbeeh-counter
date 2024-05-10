<p align="center">
<p align="center">
  <a href="https://github.com/i-rin-eam">
    <img src="https://avatars.githubusercontent.com/u/154800878?s=400&u=5d18880cc28646190a19a971bfcdbc54644eab07&v=4" alt="Logo" width="100" height="100">
  </a> 
<h1 align='center'>Tasbeeh Counter with SharedPreferences</h1>
<h3 align='center'>
   Visit my youtube channel <a href="https://www.youtube.com/@LearnWithYeamin">Learn With Yeamin</a>
</h3>
</p>

## Step 1: Here is `activity_main.xml` code.
```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/counterTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="24sp"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="50dp"/>

    <Button
        android:id="@+id/addButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Add"
        android:layout_below="@id/counterTextView"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_alignParentStart="true"/>

    <Button
        android:id="@+id/subButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Subtract"
        android:layout_below="@id/counterTextView"
        android:layout_toEndOf="@id/addButton"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="8dp"/>

    <Button
        android:id="@+id/resetButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Reset"
        android:layout_below="@id/counterTextView"
        android:layout_toEndOf="@id/subButton"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="8dp"/>

</RelativeLayout>
```
## Step 2: Here is `MainActivity.java` code.
```java
package com.myeamin.uploadimage;

import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    TextView counterTextView;
    Button addButton;
    Button subButton;
    Button resetButton;
    int counter;
    SharedPreferences sharedPreferences;
    SharedPreferences.Editor editor;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        counterTextView = findViewById(R.id.counterTextView);
        addButton = findViewById(R.id.addButton);
        subButton = findViewById(R.id.subButton);
        resetButton = findViewById(R.id.resetButton);

        sharedPreferences = getSharedPreferences("" + getString(R.string.app_name), MODE_PRIVATE);
        editor = sharedPreferences.edit();

        counter = sharedPreferences.getInt("counter", 0);
        counterTextView.setText("" + counter);

        addButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                counter++;
                counterTextView.setText("" + counter);
                editor.putInt("counter", counter);
                editor.apply();
            }
        });

        subButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (counter > 0){
                    counter--;
                }
                counterTextView.setText("" + counter);
                editor.putInt("counter", counter);
                editor.apply();
            }
        });

        resetButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                counter = 0;
                counterTextView.setText("" + counter);
                editor.putInt("counter", counter);
                editor.apply();
            }
        });
    }
}
```
## Authors

**MD YEAMIN** - Android Software Developer <a href="https://www.youtube.com/@LearnWithYeamin">**(Learn With Yeamin)**</a> 

<h1 align="center">Thank You ❤️</h1>
