
# Ex.No:1 To create a employee details fields and to display the employee details using Firebase Database in Android Studio.


## AIM:

To create and display the employee details using Firebase Database in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as HelloWorld and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display the employee details in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the DatabaseTable using the firebasedatabase”.
Developed by: ROHITH HARIHARAN M
Registeration Number : 212223220087
*/
```
## Main activity.java:
```
package com.example.employeemanagement; 

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;

public class MainActivity extends AppCompatActivity {

    EditText name, age, salary;
    Button addBtn, updateBtn, deleteBtn;

    DatabaseReference databaseReference;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Connect XML components
        name = findViewById(R.id.name);
        age = findViewById(R.id.age);
        salary = findViewById(R.id.salary);

        addBtn = findViewById(R.id.addBtn);
        updateBtn = findViewById(R.id.updateBtn);
        deleteBtn = findViewById(R.id.deleteBtn);


        // Firebase Database reference
        databaseReference = FirebaseDatabase.getInstance()
                .getReference("Employees");


        // ADD EMPLOYEE
        addBtn.setOnClickListener(view -> {

            String id = databaseReference.push().getKey();

            String empName = name.getText().toString();
            int empAge = Integer.parseInt(age.getText().toString());
            double empSalary = Double.parseDouble(salary.getText().toString());

            Employee employee = new Employee(
                    id,
                    empName,
                    empAge,
                    empSalary
            );

            databaseReference.child(id).setValue(employee);

            Toast.makeText(MainActivity.this,
                    "Employee Added Successfully",
                    Toast.LENGTH_SHORT).show();

            clearFields();
        });


        // UPDATE EMPLOYEE (basic structure)
        updateBtn.setOnClickListener(view -> {

            Toast.makeText(MainActivity.this,
                    "Update feature will be added next",
                    Toast.LENGTH_SHORT).show();

        });


        // DELETE EMPLOYEE (basic structure)
        deleteBtn.setOnClickListener(view -> {

            Toast.makeText(MainActivity.this,
                    "Delete feature will be added next",
                    Toast.LENGTH_SHORT).show();

        });

    }


    // Clear input boxes
    private void clearFields() {

        name.setText("");
        age.setText("");
        salary.setText("");

    }
}
```
## activity main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <EditText
        android:id="@+id/name"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Employee Name"/>

    <EditText
        android:id="@+id/age"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Employee Age"
        android:inputType="number"/>

    <EditText
        android:id="@+id/salary"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Employee Salary"
        android:inputType="numberDecimal"/>

    <Button
        android:id="@+id/addBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Add Employee"/>

    <Button
        android:id="@+id/updateBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Update Employee"/>

    <Button
        android:id="@+id/deleteBtn"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Delete Employee"/>

</LinearLayout>
```

## OUTPUT

<img width="1917" height="1020" alt="Screenshot 2026-08-03 234449" src="https://github.com/user-attachments/assets/7d895c12-31ed-4858-8eea-40c2d775459a" />

<img width="1917" height="1013" alt="Screenshot 2026-08-03 234539" src="https://github.com/user-attachments/assets/ff324a24-43d2-4ae9-aab5-0b661bf9a071" />






## RESULT
Thus a Simple Android Application create a firebase database and to display the employee details using Firbase Real Time Database in Android Studio is developed and executed successfully.
