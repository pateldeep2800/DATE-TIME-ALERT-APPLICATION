# DATE-TIME-ALERT-APPLICATION

TOOL-ANDROID STUDIO

LANGUAGE-ANDROID STUDIO

Activity_main.xml

    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:gravity="center"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:background="@color/black"
        tools:context=".MainActivity">
     <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Select Date"
        android:textSize="32dp"
        android:gravity="center"
        android:textColor="@color/white"
        android:id="@+id/sdate"
        />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Date Button"
        android:textSize="20dp"
        android:layout_marginTop="4dp"
        android:id="@+id/btndate"
        android:backgroundTint="#2196F3"/>
    <TextView
        android:layout_marginTop="10dp"
        android:layout_width="match_parent"
        android:textColor="@color/white"
        android:layout_height="wrap_content"
        android:text="Select Time"
        android:textSize="32dp"
        android:gravity="center"
        android:id="@+id/stime"
        />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Time Button"
        android:textSize="20dp"
        android:layout_marginTop="4dp"
        android:id="@+id/btntime"
        android:backgroundTint="#4CAF50"/>
    <TextView
        android:layout_marginTop="10dp"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textColor="@color/white"
        android:text="Alert Button"
        android:textSize="32dp"
        android:gravity="center"
        />
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Alert"
        android:layout_marginTop="4dp"
        android:textSize="25dp"
        android:id="@+id/btnalert"
        android:backgroundTint="#A4060C"/>
    </LinearLayout>

MainActivity.java

     package com.example.nexgen;
     import androidx.appcompat.app.AlertDialog;
     import androidx.appcompat.app.AppCompatActivity;
     import android.app.DatePickerDialog;
     import android.app.TimePickerDialog;
     import android.content.DialogInterface;
     import android.icu.util.Calendar;
     import android.os.Bundle;
     import android.view.View;
     import android.widget.Button;
     import android.widget.DatePicker;
     import android.widget.TextView;
     import android.widget.TimePicker;
     import java.text.SimpleDateFormat;
            public class MainActivity extends AppCompatActivity {
            TextView sdate,stime;
            Button btndate,btntime,btnalert;
            Calendar c = Calendar.getInstance();
            private SimpleDateFormat simpleDateFormat=new SimpleDateFormat("hh:mm a");
            int y=c.get(Calendar.YEAR);
            int m=c.get(Calendar.MONTH);
            int d=c.get(Calendar.DAY_OF_MONTH);
            int min=c.get(Calendar.MINUTE);
            int hour=c.get(Calendar.HOUR_OF_DAY);
            int ampm=c.get(Calendar.AM_PM);
        @Override
        protected void onCreate(Bundle savedInstanceState) {
                super.onCreate(savedInstanceState);
                setContentView(R.layout.activity_main);
                sdate=findViewById(R.id.sdate);
                btndate=findViewById(R.id.btndate);
                stime=findViewById(R.id.stime);
                btntime=findViewById(R.id.btntime);
                btnalert=findViewById(R.id.btnalert);
                btndate.setOnClickListener(new View.OnClickListener() {
                        @Override
                        public void onClick(View v) {
                                dateshow();
                        }
                });
                btntime.setOnClickListener(new View.OnClickListener() {
                        @Override
                        public void onClick(View v) {
                                showtime();
                        }
                });
                btnalert.setOnClickListener(new View.OnClickListener() {
                        @Override
                        public void onClick(View v) {
                                alert();
                        } }); }
        public void dateshow(){
                DatePickerDialog datePickerDialog=new DatePickerDialog(this,new DatePickerDialog.OnDateSetListener(){
                        @Override
                        public void onDateSet(android.widget.DatePicker view, int year, int month, int dayOfMonth) {
                                sdate.setText("Select date:"+(dayOfMonth)+"/"+(month+1)+"/"+year);
                        }
                },y,m,d);
                datePickerDialog.show();
        }
        public void showtime(){
                TimePickerDialog timePickerDialog=new TimePickerDialog(this, new TimePickerDialog.OnTimeSetListener() {
                        @Override
                        public void onTimeSet(TimePicker view, int hourOfDay, int minute) {
                                c.set(Calendar.HOUR_OF_DAY,hourOfDay);
                                c.set(Calendar.MINUTE, minute);
                                stime.setText("Time is:"+simpleDateFormat.format(c.getTime()));
                        }
                }, hour, min, false);
                timePickerDialog.show();
        }
        public void alert(){
    // AlertDialog.Builder alertbuilder=new AlertDialog.Builder(DatePicker.this);
                    AlertDialog.Builder alertbuilder=new AlertDialog.Builder(MainActivity.this);
                    alertbuilder.setTitle("Alert Warn");
                    alertbuilder.setMessage("You have click on the alert message");
                    alertbuilder.setPositiveButton("close", new DialogInterface.OnClickListener() {
                            @Override
                            public void onClick(DialogInterface dialog, int which) {
                            } });
                    AlertDialog alertDialog=alertbuilder.create();
                    alertDialog.show();}
                    }
