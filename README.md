# AndSes5Ass4
MainActivity.java
package me.rk.andses5ass4;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity implements View.OnClickListener{
    private Button mloginButton;
    private EditText medittext;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mloginButton=(Button) findViewById(R.id.loginbutton);
        mloginButton.setOnClickListener(this);

        medittext=(EditText) findViewById(R.id.editview);
    }

    @Override
    public void onClick(View v) {
        Intent intent =new Intent(MainActivity.this, SecondActivity.class);
        String q= medittext.getText().toString();

        if(!(q.equals(null)||(q.equals("")))) {
            Bundle bundle = new Bundle();
            bundle.putString("name", "Welcome " + q);

            intent.putExtras(bundle);
            startActivity(intent);
        }else{
            Toast.makeText(MainActivity.this, "Username cannot be empty !!!", Toast.LENGTH_SHORT).show();
        }
    }
}

SecondActivity.java
package me.rk.andses5ass4;

import android.app.Activity;
import android.os.Bundle;
import android.test.suitebuilder.TestMethod;
import android.widget.TextView;

/**
 * Created by airodyra on 6/25/2016.
 */
public class SecondActivity extends Activity {
    private TextView mdataTextView;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.second_layout);

        Bundle bundle=getIntent().getExtras();
        String name=bundle.getString("name");

        mdataTextView=(TextView) findViewById(R.id.textview);

        mdataTextView.setText(name);

    }
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="me.rk.andses5ass4.MainActivity"
    android:background="@android:color/holo_orange_light">

    <Button
        android:id="@+id/loginbutton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Login"
        android:layout_centerInParent="true"/>

    <EditText
        android:id="@+id/editview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="Enter Username to login"
        android:padding="10dp"
        android:layout_above="@id/loginbutton"
        android:layout_centerHorizontal="true"/>
</RelativeLayout>

second_layout.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:textSize="25dp"/>

</RelativeLayout>
