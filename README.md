# My-Project
It is a project done on the platform android using android studio


**Pic One**

package com.mbtechnologies.pickone;

import android.app.AlertDialog;
import android.app.Dialog;
import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.TextView;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {
    ListView listView;
    ArrayList<String> stringArray;
    ArrayAdapter<String> modeAdapter;
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        listView = new ListView(this);
        stringArray=new ArrayList<String>();
        stringArray.add("1");
        stringArray.add("2");
        stringArray.add("3");

        modeAdapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, android.R.id.text1, stringArray);


        listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {

            public void onItemClick(AdapterView<?> parent, View view, int position,long id) {
                TextView listText = (TextView) view.findViewById(R.id.result);
                String text = stringArray.get(position);
                Intent i = new Intent(getApplicationContext(), Dice.class);
                i.putExtra("selected-item", text);
                startActivity(i);
            }
        } );


    }

    public void onImgButton1Click(View v){
        Intent intent = new Intent(getApplicationContext(), OptionPicker.class);
        startActivity(intent);
    }
    public void onImgButton2Click(View v){
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("How many dice do you need");

        String[] stringArray = new String[] {"1","2","3"};
        ArrayAdapter<String> modeAdapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, android.R.id.text1, stringArray);
        listView.setAdapter(modeAdapter);

        builder.setView(listView);
        final Dialog dialog = builder.create();

        dialog.show();


    }

    public void onImgButton3Click(View v){
        Intent t=new Intent(getApplicationContext(),Toss.class);
        startActivity(t);
    }

    }

<ImageButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/optionbutton"
        android:src="@drawable/optionicon"
        android:onClick="onImgButton1Click"
        android:layout_alignParentTop="true"
        android:layout_centerHorizontal="true" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:text="option Picker"
        android:id="@+id/option"
        android:layout_below="@+id/optionbutton"
        android:layout_centerHorizontal="true" />

    <ImageButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/imageButton2"
        android:src="@drawable/diceicon"
        android:onClick="onImgButton2Click"
        android:layout_below="@+id/option"
        android:layout_alignRight="@+id/optionbutton"
        android:layout_alignEnd="@+id/optionbutton" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:text="Dice"
        android:id="@+id/dice"
        android:layout_below="@+id/imageButton2"
        android:layout_centerHorizontal="true" />

    <ImageButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/imageButton"
        android:src="@drawable/tossicon1"
        android:layout_below="@+id/dice"
        android:layout_alignLeft="@+id/optionbutton"
        android:layout_alignStart="@+id/optionbutton" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:text="Toss"
        android:id="@+id/toss"
        android:layout_below="@+id/imageButton"
        android:layout_centerHorizontal="true" />

**OptionPicker**
    <EditText
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:id="@+id/editText"
        android:layout_marginTop="54dp"
        android:hint="Enter your option and press  &apos;+&apos; "
        android:layout_alignParentRight="true"
        android:layout_alignParentEnd="true"
        android:textColor="#eb070707"
        android:textColorHint="#e58dff72" />
    <Button
        style="?android:attr/buttonStyleSmall"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="+"
        android:id="@+id/button"
        android:layout_gravity="center_horizontal"
        android:onClick="onButtonClick"
        android:layout_marginTop="46dp"
        android:layout_below="@+id/editText"
        android:layout_centerHorizontal="true"
        android:textColor="#fe010101" />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Continue"
        android:id="@+id/button2"
        android:onClick="onButton2Click"
        android:layout_centerVertical="true"
        android:layout_toLeftOf="@+id/button"
        android:layout_toStartOf="@+id/button"
        android:textColor="#fe010101" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Reset Options"
        android:id="@+id/button3"
        android:layout_alignTop="@+id/button2"
        android:layout_toRightOf="@+id/button"
        android:layout_toEndOf="@+id/button"
        android:onClick="onButton3Click"
        android:textColor="#fe010101" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:text="Let&apos;s go with"
        android:id="@+id/textView"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="54dp"
        android:textColor="#0f0f0f" />

package com.mbtechnologies.optionchooser;

import android.graphics.Color;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import java.util.Random;



public class MainActivity extends AppCompatActivity {
    EditText txt1;
   TextView t1;
    private static final Random rand = new Random();
    String a[] =new String[10];

       @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_option_picker);
        txt1 =(EditText)findViewById(R.id.editText);
        t1=(TextView)findViewById(R.id.textView);
    }
    int count=-1;
   public void onButtonClick(View v) {
count++;

       int s=txt1.getText().length();
               if(s==0){
    t1.setText("Enter a value");
                   t1.setTextColor(Color.RED);
                   --count;
               }
        else if(count<10) {
           a[count] = txt1.getText().toString();
      txt1.setText("");

       }
       else{
           t1.setText("limit is exceed");
                   t1.setTextColor(Color.RED);
                   --count;
       }

   }


public void onButton2Click(View v){
      if(count==-1){
      t1.setText("please enter your options");
  t1.setTextColor(Color.RED);
  }
      else {
          t1.setText("Let's go with");
          t1.setTextColor(Color.BLACK);
          String str = a[rand.nextInt(count+1)];
          t1.setText(str);
      t1.setTextColor(Color.MAGENTA);
  }
  }

public void onButton3Click (View v){
   count=-1;
    a = new String[a.length];
    t1.setText("Let's go with");
    t1.setTextColor(Color.BLACK);
    }
}


**Dice**

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;

import java.util.Random;

public class Dice extends AppCompatActivity {
    int n;
    TextView show1;
    private static final Random rand1 = new Random();
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_dice);
        Intent in = getIntent();
        TextView result1 = (TextView) findViewById(R.id.result);
        show1 = (TextView) findViewById(R.id.show);
        String item = in.getStringExtra("selected-item");
        result1.setText("you selected "+ item);
        n=Integer.parseInt(item);
    }

    public void onRollClick(View v){
        int m = rand1.nextInt(n*6);
        show1.setText("Go with "+(m+1));
    }




}


<Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Roll"
        android:id="@+id/button4"
        android:layout_centerVertical="true"
        android:layout_centerHorizontal="true"
        android:onClick="onRollClick" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:id="@+id/show"
        android:layout_above="@+id/button4"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="65dp"
        android:textStyle="bold"
        android:textSize="20sp" />

    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:id="@+id/result"
        android:layout_alignRight="@+id/button4"
        android:layout_alignEnd="@+id/button4"
        android:layout_alignParentTop="true"
        android:layout_alignLeft="@+id/button4"
        android:layout_alignStart="@+id/button4" />


**Toss**

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.ImageView;

import java.util.Random;

public class Toss extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_toss);
    }
public void OnTossClick(View v){
    int n=2;
   ImageView View=(ImageView) findViewById(R.id.imageView);
    Random rand = new Random();
    int rndInt = rand.nextInt(n) + 1;
    String imgName = "img" + rndInt;
    int id = getResources().getIdentifier(imgName, "drawable", getPackageName());
    View.setImageResource(id);

}

  }


<Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/Toss"
        android:id="@+id/button5"
        android:onClick="OnTossClick"
        android:layout_alignParentTop="true"
        android:layout_centerHorizontal="true" />

    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/imageView"
        android:src="@drawable/tosss"
        android:layout_centerVertical="true"
        android:layout_centerHorizontal="true" />



**Truth or Dare**

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.widget.ImageView;

import java.util.Random;


public class TruthOrDare extends Activity {
    private static final Random rand2 = new Random();
    int n=360;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_truth_or_dare);


    }
             public void onTurnClick(View v){
                 ImageView img =(ImageView)findViewById(R.id.imageView2);
                 int m = rand2.nextInt((n+10));
                 img.setRotation(m);

             }

}


<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" android:layout_width="match_parent"
    android:layout_height="match_parent" android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    android:paddingBottom="@dimen/activity_vertical_margin"
    tools:context="com.mbtechnologies.pickone.TruthOrDare">


    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/imageView2"
        android:src="@drawable/arrow"
        android:layout_alignParentTop="true"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="101dp" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/Turn"
        android:id="@+id/button6"
        android:onClick="onTurnClick"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="129dp" />
</RelativeLayout>


