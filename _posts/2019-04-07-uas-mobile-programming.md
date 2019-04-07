---
layout: post
title: "UAS Mobile Programming"
description: "Aplikasi Pokemon Viewer menggunakan Android Studio."
date: 2019-04-07
tags: [Kuliah]
comments: true
share: true
---

### 1. Deskripsi

Aplikasi Pokemon Viewer

Aplikasi ini berfungsi untuk memberikan informasi/detail tentang pokemon yang di-input oleh user.
Input dapat berupa: Name, Type, atau Ability.

### 2. XML Text

##### activity_main.xml

Tampilan login:

```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="28dp"
        android:layout_marginEnd="303dp"
        android:layout_marginBottom="16dp"
        android:text="@string/username"
        android:textSize="18sp"
        app:layout_constraintBottom_toTopOf="@+id/txtUser"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/textView6"
        android:layout_width="wrap_content"
        android:layout_height="22dp"
        android:layout_marginStart="28dp"
        android:layout_marginEnd="305dp"
        android:layout_marginBottom="16dp"
        android:text="@string/password"
        android:textSize="18sp"
        app:layout_constraintBottom_toTopOf="@+id/txtPass"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/txtUser"
        android:layout_width="352dp"
        android:layout_height="wrap_content"
        android:layout_marginTop="64dp"
        android:autofillHints=""
        android:ems="10"
        android:inputType="textPersonName"
        app:layout_constraintTop_toBottomOf="@+id/imageView"
        tools:layout_editor_absoluteX="29dp" />

    <EditText
        android:id="@+id/txtPass"
        android:layout_width="353dp"
        android:layout_height="wrap_content"
        android:layout_marginTop="56dp"
        android:autofillHints=""
        android:ems="10"
        android:inputType="textPassword"
        app:layout_constraintTop_toBottomOf="@+id/txtUser"
        tools:layout_editor_absoluteX="28dp" />

    <Button
        android:id="@+id/btnLogin"
        android:layout_width="100dp"
        android:layout_height="88dp"
        android:layout_marginStart="52dp"
        android:layout_marginTop="24dp"
        android:text="@string/login"
        android:textSize="24sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/txtPass" />

    <Button
        android:id="@+id/btnClose"
        android:layout_width="100dp"
        android:layout_height="88dp"
        android:layout_marginTop="24dp"
        android:layout_marginEnd="52dp"
        android:onClick="keluar"
        android:text="@string/close"
        android:textSize="24sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/txtPass" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="233dp"
        android:layout_height="53dp"
        android:layout_marginStart="42dp"
        android:layout_marginEnd="42dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:srcCompat="@drawable/pokeviewer"
        tools:layout_editor_absoluteY="38dp" />
</android.support.constraint.ConstraintLayout>
```

##### activity_menu.xml

Tampilan utama setelah sukses login.

```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".Menu">

    <ImageView
        android:id="@+id/imageView2"
        android:layout_width="244dp"
        android:layout_height="48dp"
        android:layout_marginTop="8dp"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/pokeviewer"
        tools:layout_editor_absoluteX="83dp" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:text="Search"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintTop_toBottomOf="@+id/imageView2"
        tools:layout_editor_absoluteX="53dp" />

    <EditText
        android:id="@+id/txtSearch"
        android:layout_width="305dp"
        android:layout_height="42dp"
        android:layout_marginTop="8dp"
        android:ems="10"
        android:hint="Name/Type/Ability"
        android:inputType="textPersonName"
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@+id/textView"
        tools:layout_editor_absoluteX="47dp" />

    <android.support.constraint.ConstraintLayout
        android:id="@+id/rb_search"
        android:layout_width="303dp"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:orientation="horizontal"
        app:layout_constraintTop_toBottomOf="@+id/txtSearch"
        tools:layout_editor_absoluteX="47dp">

        <RadioButton
            android:id="@+id/rb_name"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginBottom="65dp"
            android:checked="true"
            android:onClick="checkButton"
            android:text="Name"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintStart_toStartOf="@+id/rb_type" />

        <RadioButton
            android:id="@+id/rb_type"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:onClick="checkButton"
            android:text="Type"
            app:layout_constraintStart_toStartOf="@+id/rb_ability"
            app:layout_constraintTop_toBottomOf="@+id/rb_name" />

        <RadioButton
            android:id="@+id/rb_ability"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="8dp"
            android:layout_marginLeft="8dp"
            android:onClick="checkButton"
            android:text="Ability"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/rb_type" />

    </android.support.constraint.ConstraintLayout>

    <Button
        android:id="@+id/btnCatch"
        android:layout_width="131dp"
        android:layout_height="43dp"
        android:layout_marginTop="8dp"
        android:text="Submit"
        android:textSize="14sp"
        app:layout_constraintTop_toBottomOf="@+id/rb_search"
        tools:layout_editor_absoluteX="53dp" />

    <ListView
        android:id="@+id/poke"
        android:layout_width="311dp"
        android:layout_height="194dp"
        android:layout_marginTop="8dp"
        app:layout_constraintTop_toBottomOf="@+id/btnCatch"
        tools:layout_editor_absoluteX="47dp" />
</android.support.constraint.ConstraintLayout>
```

### 3. XML Graphic

##### activity_main.xml

![activity_main.xml](http://blog.ki2naiver.id/images/uas/xml1.png "activity_main.xml")

##### activity_menu.xml

![activity_menu.xml](http://blog.ki2naiver.id/images/uas/xml2.png "activity_menu.xml")

### 4. Source Code (Java)

##### MainActivity.java

```java
package id.ki2naiver.faridl_nur_prastya_161011400304;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private String[][] dataUser = {
            {"ADMIN","ADMIN","Administrator"},
            {"user1","password1","Nama User 1"},
            {"user2","password2","Nama User 2"}
    };
    private EditText txtUser, txtPass;
    private final int SUCCESS=1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        txtUser = (EditText) findViewById(R.id.txtUser);
        txtPass = (EditText) findViewById(R.id.txtPass);

        Button btnLogin = findViewById(R.id.btnLogin);
        Button btnClose = findViewById(R.id.btnClose);

        btnClose.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                finish();
            }
        });

        btnLogin.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                int i = 1;
                boolean success = false;

                while ((i < dataUser.length) && (!success)) {
                    if ((txtUser.getText().toString().equals(dataUser[i][0])) && (txtPass.getText().toString().equals(dataUser[i][1]))) {
                        success = true;
                    } else {
                        i++;
                    }
                }

//                Intent intent;
//                if (success) {
//                    intent = new Intent(this, Menu.class);
//                    intent.putExtra("namaUser", dataUser[i][2]);
//                    startActivityForResult(intent,SUCCESS);
//                } else {
//                    intent = new Intent(this, MainActivity.class);
//                    finish();
//                }
//                startActivity(intent);
            }


        });

    }
    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        switch (requestCode) {
            case SUCCESS:
                txtUser.setText("");
                txtPass.setText("");
                break;
        }
    }
}


```

##### Menu.java

```java
package id.ki2naiver.faridl_nur_prastya_161011400304;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.util.JsonToken;
import android.widget.ArrayAdapter;
import android.widget.ListView;

import java.util.ArrayList;
import java.util.List;

public class Menu extends AppCompatActivity {

    public class NextEvolution
    {
        public String num;
        public String name;
    }

    public class PrevEvolution
    {
        public String num;
        public String name;
    }

    public class Pokemon
    {
        public int id;
        public String num;
        public String name;
        public String img;
        public List<String> type;
        public String height;
        public String weight;
        public String candy;
        public int candy_count;
        public String egg;
        public double spawn_chance;
        public double avg_spawns;
        public String spawn_time;
        //            public List<string> multipliers;
        public List<String> weaknesses;
        public List<NextEvolution> next_evolution;
        public List<PrevEvolution> prev_evolution;
    }

    ListView poke;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_menu);

        poke = (ListView) findViewById(R.id.poke);


        ArrayList<String> arrayList = new ArrayList<>();

        arrayList.add("Name: Bulbasaur");
        arrayList.add("Type: Poison, Grass");
        arrayList.add("Ability: Chlorophyll, Overgrow");
        arrayList.add("Name: Bulbasaur");

        ArrayAdapter arrayAdapter = new ArrayAdapter(this,android.R.layout.simple_list_item_1,arrayList);

        poke.setAdapter(arrayAdapter);

    }
}

```

### 5. Screenshot (Emulator)

##### Tampilan Login

![Tampilan Login](http://blog.ki2naiver.id/images/uas/login.png "Tampilan Login")

##### Tampilan setelah sukses login

![Menu Utama](http://blog.ki2naiver.id/images/uas/menu1.png "Menu Utama")

##### Tampilan hasil setelah memasukkan input dan klik submit

![Pokemon](http://blog.ki2naiver.id/images/uas/menu2.png "Pokemon")

Sekian, Terima Kasih!

- Faridl
