---
layout: post
title: "UTS Mobile Programming"
description: "Aplikasi To-Do List menggunakan Android Studio."
date: 2019-03-24
tags: [Kuliah]
comments: true
share: true
---

### 1. Deskripsi

Aplikasi To-Do List / Perencanaan Kegiatan

Aplikasi ini berfungsi untuk menyimpan suatu kegiatan atau hal yang ingin dilakukan oleh pengguna.
List kegiatan dapat ditandai berdasarkan prioritas:
- 1 (Penting) = Merah
- 2 (Sedang) = Orange
- 3 (Biasa) = Kuning

### 2. XML Text

##### activity_main.xml
Tampilan utama saat aplikasi dijalankan sekaligus menampilkan list kegiatan yang sudah ditambahkan.
```xml
<?xml version="1.0" encoding="utf-8"?>

<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <android.support.v7.widget.RecyclerView
        android:id="@+id/recyclerViewTasks"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:paddingBottom="8dp"/>

    <android.support.design.widget.FloatingActionButton
        android:id="@+id/fab"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="bottom|end"
        android:layout_margin="@dimen/fab_margin"
        app:srcCompat="@android:drawable/ic_input_add"
        android:tint="@android:color/white"/>

</FrameLayout>
```

##### activity_add_task.xml
Tampilan saat menambahkan task baru.
```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingEnd="@dimen/activity_horizontal_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingStart="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin">

    <EditText
        android:id="@+id/editTextTaskDescription"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:gravity="start"
        android:hint="@string/masukkan_deskripsi"
        android:paddingBottom="@dimen/activity_horizontal_margin"
        android:inputType="" />

    <TextView
        style="@style/TextAppearance.AppCompat.Medium"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="start"
        android:layout_marginTop="8dp"
        android:layout_marginBottom="8dp"
        android:text="@string/prioritas"
        android:textColor="@android:color/primary_text_light" />

    <FrameLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginBottom="@dimen/activity_vertical_margin">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_gravity="center"
            android:weightSum="3">

            <Button
                style="?android:attr/buttonBarButtonStyle"
                android:textColor="@android:color/transparent"
                android:id="@+id/buttonP1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:background="@color/materialRed"
                android:text="@string/penting"
                android:layout_weight="1"
                android:onClick="onPrioritySelected"/>

            <Button
                android:id="@+id/buttonP2"
                style="?android:attr/buttonBarButtonStyle"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:background="@color/materialOrange"
                android:textColor="@android:color/transparent"
                android:text="@string/sedang"
                android:layout_weight="1"
                android:onClick="onPrioritySelected"/>

            <Button
                style="?android:attr/buttonBarButtonStyle"
                android:textColor="@android:color/transparent"
                android:id="@+id/buttonP3"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:background="@color/materialYellow"
                android:text="@string/biasa"
                android:layout_weight="1"
                android:onClick="onPrioritySelected"/>

        </LinearLayout>

        <RadioGroup
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_gravity="center"
            android:weightSum="3">

            <RadioButton
                android:id="@+id/radButton1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:onClick="onPrioritySelected"
                android:text="@string/penting"
                android:theme="@style/WhiteRadioButton" />

            <RadioButton
                android:id="@+id/radButton2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:onClick="onPrioritySelected"
                android:text="@string/sedang"
                android:theme="@style/WhiteRadioButton" />

            <RadioButton
                android:id="@+id/radButton3"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:onClick="onPrioritySelected"
                android:text="@string/biasa"
                android:theme="@style/WhiteRadioButton" />

        </RadioGroup>

    </FrameLayout>

    <Button
        android:id="@+id/addButton"
        style="@style/TextAppearance.AppCompat.Large"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:background="@color/colorPrimary"
        android:onClick="onClickAddTask"
        android:text="@string/tambahkan"
        android:textColor="@android:color/primary_text_dark" />

</LinearLayout>
```

### 3. XML Graphic

##### activity_main.xml
![activity_main.xml](http://blog.ki2naiver.id/images/uts/activity_main.png "activity_main.xml")

##### activity_add_task.xml
![activity_add_task.xml](http://blog.ki2naiver.id/images/uts/activity_add_task.png "activity_add_task.xml")

### Source Code (Java)

##### MainActivity.java
```java
/*
* Copyright (C) 2016 The Android Open Source Project
*
* Licensed under the Apache License, Version 2.0 (the "License");
* you may not use this file except in compliance with the License.
* You may obtain a copy of the License at
*
*      http://www.apache.org/licenses/LICENSE-2.0
*
* Unless required by applicable law or agreed to in writing, software
* distributed under the License is distributed on an "AS IS" BASIS,
* WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
* See the License for the specific language governing permissions and
* limitations under the License.
*/

package com.example.todolist;

import android.content.Intent;
import android.database.Cursor;
import android.net.Uri;
import android.os.Bundle;
import android.support.design.widget.FloatingActionButton;
import android.support.v4.app.LoaderManager;
import android.support.v4.content.AsyncTaskLoader;
import android.support.v4.content.Loader;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.LinearLayoutManager;
import android.support.v7.widget.RecyclerView;
import android.support.v7.widget.helper.ItemTouchHelper;
import android.util.Log;
import android.view.View;

import com.example.todolist.R;
import com.example.todolist.data.TaskContract;


public class MainActivity extends AppCompatActivity implements
        LoaderManager.LoaderCallbacks<Cursor> {


    private static final String TAG = MainActivity.class.getSimpleName();
    private static final int TASK_LOADER_ID = 0;

    private CustomCursorAdapter mAdapter;
    RecyclerView mRecyclerView;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mRecyclerView = (RecyclerView) findViewById(R.id.recyclerViewTasks);

        mRecyclerView.setLayoutManager(new LinearLayoutManager(this));

        mAdapter = new CustomCursorAdapter(this);
        mRecyclerView.setAdapter(mAdapter);

        new ItemTouchHelper(new ItemTouchHelper.SimpleCallback(0, ItemTouchHelper.LEFT | ItemTouchHelper.RIGHT) {
            @Override
            public boolean onMove(RecyclerView recyclerView, RecyclerView.ViewHolder viewHolder, RecyclerView.ViewHolder target) {
                return false;
            }

            @Override
            public void onSwiped(RecyclerView.ViewHolder viewHolder, int swipeDir) {

                int id = (int) viewHolder.itemView.getTag();

                String stringId = Integer.toString(id);
                Uri uri = TaskContract.TaskEntry.CONTENT_URI;
                uri = uri.buildUpon().appendPath(stringId).build();

                getContentResolver().delete(uri, null, null);

                getSupportLoaderManager().restartLoader(TASK_LOADER_ID, null, MainActivity.this);

            }
        }).attachToRecyclerView(mRecyclerView);


        FloatingActionButton fabButton = (FloatingActionButton) findViewById(R.id.fab);

        fabButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                Intent addTaskIntent = new Intent(MainActivity.this, AddTaskActivity.class);
                startActivity(addTaskIntent);
            }
        });

        getSupportLoaderManager().initLoader(TASK_LOADER_ID, null, this);
    }


    @Override
    protected void onResume() {
        super.onResume();

        getSupportLoaderManager().restartLoader(TASK_LOADER_ID, null, this);
    }


    @Override
    public Loader<Cursor> onCreateLoader(int id, final Bundle loaderArgs) {

        return new AsyncTaskLoader<Cursor>(this) {

            Cursor mTaskData = null;

            @Override
            protected void onStartLoading() {
                if (mTaskData != null) {

                    deliverResult(mTaskData);
                } else {

                    forceLoad();
                }
            }

            @Override
            public Cursor loadInBackground() {

                try {
                    return getContentResolver().query(TaskContract.TaskEntry.CONTENT_URI,
                            null,
                            null,
                            null,
                            TaskContract.TaskEntry.COLUMN_PRIORITY);

                } catch (Exception e) {
                    Log.e(TAG, "Failed to asynchronously load data.");
                    e.printStackTrace();
                    return null;
                }
            }

            public void deliverResult(Cursor data) {
                mTaskData = data;
                super.deliverResult(data);
            }
        };

    }


    @Override
    public void onLoadFinished(Loader<Cursor> loader, Cursor data) {

        mAdapter.swapCursor(data);
    }


    @Override
    public void onLoaderReset(Loader<Cursor> loader) {
            mAdapter.swapCursor(null);
        }

}

```

##### AddTaskActivity.java
```java
/*
* Copyright (C) 2016 The Android Open Source Project
*
* Licensed under the Apache License, Version 2.0 (the "License");
* you may not use this file except in compliance with the License.
* You may obtain a copy of the License at
*
*      http://www.apache.org/licenses/LICENSE-2.0
*
* Unless required by applicable law or agreed to in writing, software
* distributed under the License is distributed on an "AS IS" BASIS,
* WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
* See the License for the specific language governing permissions and
* limitations under the License.
*/

package com.example.todolist;

import android.content.ContentValues;
import android.net.Uri;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.View;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.Toast;

import com.example.todolist.R;
import com.example.todolist.data.TaskContract;


public class AddTaskActivity extends AppCompatActivity {

    private int mPriority;


    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_add_task);

        ((RadioButton) findViewById(R.id.radButton1)).setChecked(true);
        mPriority = 1;
    }


    public void onClickAddTask(View view) {

        String input = ((EditText) findViewById(R.id.editTextTaskDescription)).getText().toString();
        if (input.length() == 0) {
            return;
        }

        ContentValues contentValues = new ContentValues();

        contentValues.put(TaskContract.TaskEntry.COLUMN_DESCRIPTION, input);
        contentValues.put(TaskContract.TaskEntry.COLUMN_PRIORITY, mPriority);

        Uri uri = getContentResolver().insert(TaskContract.TaskEntry.CONTENT_URI, contentValues);

        if(uri != null) {
            Toast.makeText(getBaseContext(), uri.toString(), Toast.LENGTH_LONG).show();
        }

        finish();

    }


    public void onPrioritySelected(View view) {
        if (((RadioButton) findViewById(R.id.radButton1)).isChecked()) {
            mPriority = 1;
        } else if (((RadioButton) findViewById(R.id.radButton2)).isChecked()) {
            mPriority = 2;
        } else if (((RadioButton) findViewById(R.id.radButton3)).isChecked()) {
            mPriority = 3;
        }
    }
}
```

### 4. Screenshot (Emulator)

##### Tampilan awal
![Tampilan Awal](http://blog.ki2naiver.id/images/uts/main.png "Tampilan Awal")

##### Tampilan saat menambahkan task baru
![Tambah Task](http://blog.ki2naiver.id/images/uts/add_task.png "Tambah Task")

##### Tampilan saat task sudah berhasil ditambahkan
![Task Ditambah](http://blog.ki2naiver.id/images/uts/added.png "Task Ditambah")

Sekian, Terima Kasih!
- Faridl