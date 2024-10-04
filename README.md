package com.example.registrationformapp;
import android.os.Bundle;

import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity { 

EditText editTextName; 
EditText editTextEmail;
EditText editTextPassword;  
EditText editTextPassword2;  
Button Submit;  
@Override   
protected void onCreate(Bundle savedInstanceState) {  
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_main);  
editTextName = findViewById(R.id.editTextName);  
editTextEmail = findViewById(R.id.editTextEmail);   
editTextPassword = findViewById(R.id.editTextPassword);  
editTextPassword2 = findViewById(R.id.editTextPowHasło);  
Submit = findViewById(R.id.buttonSubmit);    
Submit.setOnClickListener(new View.OnClickListener() {  
@Override        
public void onClick(View view) {   
String name = editTextName.getText().toString().trim();   
String email = editTextEmail.getText().toString().trim(); 
String password = editTextPassword.getText().toString().trim();  
String password2 = editTextPassword2.getText().toString().trim(); 
if (name.isEmpty()) {          
Toast.makeText(MainActivity.this, "Proszę wprowadzić imię", Toast.LENGTH_SHORT).show();   
} else if (email.isEmpty()) {     
Toast.makeText(MainActivity.this, "Proszę wprowadzić adres email", Toast.LENGTH_SHORT).show();    
} else if (!android.util.Patterns.EMAIL_ADDRESS.matcher(email).matches()) {   
Toast.makeText(MainActivity.this, "Niepoprawny adres email", Toast.LENGTH_SHORT).show();  
} else if (password.length() < 6) {          
Toast.makeText(MainActivity.this, "Podane hasło jest za krótkie", Toast.LENGTH_SHORT).show();   
} else if (!password.equals(password2)) {        
Toast.makeText(MainActivity.this, "Podane hasła są różne", Toast.LENGTH_SHORT).show();      
} 
else {    
Toast.makeText(MainActivity.this, "Formularz przesłany poprawnie", Toast.LENGTH_SHORT).show();    
}        
}     
}); 
}
}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/editTextName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Imię"
        android:inputType="textPersonName"/>

    <EditText
        android:id="@+id/editTextEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Adres e-mail"
        android:inputType="textEmailAddress"/>

    <EditText
        android:id="@+id/editTextPassword"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Hasło"
        android:inputType="textPassword"/>

    <EditText
        android:id="@+id/editTextPowHasło"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Powtórz Hasło"
        android:inputType="textPassword"/>

    <Button
        android:id="@+id/buttonSubmit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Wyślij"/>






</LinearLayout>
