# ENERGY-CONSUMPTION-CALCULATOR-ANDROID-APPLICATION
To design and develop an Energy Consumption Calculator Android application using Android Studio that calculates electrical energy consumption in kilowatt-hours (kWh) 

# AIM
To design and develop an Energy Consumption Calculator Android application using Android Studio that calculates electrical energy consumption in kilowatt-hours (kWh) and estimates electricity charges based on the power rating of electrical appliances and their daily usage hours.

# SOFTWARE REQUIREMENTS
•	Android Studio
•	Java Programming Language
•	XML Layout Editor
•	Android Emulator or Android Mobile
•	Android SDK

# THEORY
Android Studio is an Integrated Development Environment (IDE) used to develop Android applications using Java and XML.
An Energy Consumption Calculator is an application used to estimate the electrical energy consumed by household electrical appliances. It helps users understand their electricity usage and calculate the approximate electricity cost.
The application uses the following Android UI components:
•	EditText: To enter appliance power rating, daily usage hours and number of days.
•	Button: To initiate the energy consumption calculation.
•	TextView: To display energy consumption and estimated electricity charges.
•	LinearLayout: To arrange the user interface components.
•	ScrollView: To enable scrolling through the application interface.
The electrical energy consumption is calculated using the formula:
Energy Consumption (kWh) = (Power Rating (W) × Usage Hours per Day × Number of Days) / 1000
The estimated electricity cost is calculated using:
Electricity Cost = Energy Consumption (kWh) × Cost per Unit
Java event-handling methods are used to process the input values and perform the energy consumption calculations.

# PROCEDURE
1.	Open Android Studio.
2.	Select New Project and choose Empty Views Activity.
3.	Enter the project name as EnergyConsumptionCalculator.
4.	Select Java as the programming language.
5.	Design the user interface using the XML Layout Editor.
6.	Add EditText fields to enter appliance power rating, daily usage hours, number of days and electricity tariff per unit.
7.	Add a Button to calculate energy consumption.
8.	Add TextViews to display energy consumption and estimated electricity cost.
9.	Open MainActivity.java and write the Java program to perform the calculations.
10.	Use setOnClickListener() to handle the Calculate button event.
11.	Convert the entered values into numerical data types.
12.	Calculate energy consumption using the appropriate mathematical formula.
13.	Calculate the estimated electricity cost based on the tariff per unit.
14.	Display the calculated energy consumption and electricity cost.
15.	Execute the application using an Android Emulator or physical Android device.
16.	Enter appliance details and verify the calculated results.

# ALGORITHM
1.	Start the application.
2.	Initialize the Android user interface components.
3.	Accept the appliance power rating in watts.
4.	Accept the daily usage hours.
5.	Accept the number of days.
6.	Accept the electricity tariff per unit.
7.	Click the Calculate button.
8.	Calculate energy consumption using the formula:
Energy = (Power × Usage Hours × Number of Days) / 1000
9.	Calculate electricity cost using:
Cost = Energy Consumption × Tariff per Unit
10.	Display the energy consumption in kWh.
11.	Display the estimated electricity cost.
12.	Stop.
# PROGRAM
XML
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fillViewport="true"
    android:padding="16dp"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <TextView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="24dp"
            android:text="@string/title_calculator"
            android:textAlignment="center"
            android:textSize="22sp"
            android:textStyle="bold" />

        <com.google.android.material.textfield.TextInputLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="12dp"
            android:hint="@string/hint_power">

            <com.google.android.material.textfield.TextInputEditText
                android:id="@+id/power"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:inputType="numberDecimal" />
        </com.google.android.material.textfield.TextInputLayout>

        <com.google.android.material.textfield.TextInputLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="12dp"
            android:hint="@string/hint_hours">

            <com.google.android.material.textfield.TextInputEditText
                android:id="@+id/hours"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:inputType="numberDecimal" />
        </com.google.android.material.textfield.TextInputLayout>

        <com.google.android.material.textfield.TextInputLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="12dp"
            android:hint="@string/hint_days">

            <com.google.android.material.textfield.TextInputEditText
                android:id="@+id/days"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:inputType="number" />
        </com.google.android.material.textfield.TextInputLayout>

        <com.google.android.material.textfield.TextInputLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="20dp"
            android:hint="@string/hint_rate">

            <com.google.android.material.textfield.TextInputEditText
                android:id="@+id/rate"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:inputType="numberDecimal" />
        </com.google.android.material.textfield.TextInputLayout>

        <Button
            android:id="@+id/calculate"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginBottom="24dp"
            android:text="@string/btn_calculate" />

        <TextView
            android:id="@+id/result"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:textAlignment="center"
            android:textSize="16sp"
            android:textStyle="bold"
            tools:text="Daily Consumption: 0.00 kWh\n\nMonthly Consumption: 0.00 units\n\nEstimated Electricity Cost: ₹0.00" />

    </LinearLayout>
</ScrollView>
# KT
package com.example.developingenergyconsumptioncalculatorapplication

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import java.util.Locale

class MainActivity : AppCompatActivity() {

    private lateinit var power: EditText
    private lateinit var hours: EditText
    private lateinit var days: EditText
    private lateinit var rate: EditText
    private lateinit var result: TextView
    private lateinit var calculate: Button

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        power = findViewById(R.id.power)
        hours = findViewById(R.id.hours)
        days = findViewById(R.id.days)
        rate = findViewById(R.id.rate)
        result = findViewById(R.id.result)
        calculate = findViewById(R.id.calculate)

        calculate.setOnClickListener {
            try {
                val powerStr = power.text.toString().trim()
                val hoursStr = hours.text.toString().trim()
                val daysStr = days.text.toString().trim()
                val rateStr = rate.text.toString().trim()

                if (powerStr.isEmpty() || hoursStr.isEmpty() || daysStr.isEmpty() || rateStr.isEmpty()) {
                    Toast.makeText(
                        this,
                        "Please fill in all fields correctly",
                        Toast.LENGTH_SHORT
                    ).show()
                    return@setOnClickListener
                }

                val p = powerStr.toDouble()
                val h = hoursStr.toDouble()
                val d = daysStr.toInt()
                val r = rateStr.toDouble()

                if (p <= 0 || h < 0 || h > 24 || d < 1 || d > 31 || r < 0) {
                    Toast.makeText(
                        this,
                        "Enter valid values",
                        Toast.LENGTH_SHORT
                    ).show()
                    return@setOnClickListener
                }

                val daily = (p * h) / 1000.0
                val monthly = daily * d
                val cost = monthly * r

                val output = String.format(
                    Locale.getDefault(),
                    "Daily Consumption: %.2f kWh\n\n" +
                            "Monthly Consumption: %.2f units\n\n" +
                            "Estimated Electricity Cost: ₹%.2f",
                    daily, monthly, cost
                )

                result.text = output
            } catch (_: NumberFormatException) {
                Toast.makeText(
                    this,
                    "Please fill in all fields correctly",
                    Toast.LENGTH_SHORT
                ).show()
            }
        }
    }
}


# EXPECTED OUTPUT
ENERGY CONSUMPTION CALCULATOR
<img width="1862" height="997" alt="Screenshot 2026-11-26 140244" src="https://github.com/user-attachments/assets/313e3e84-9154-45e4-a76a-a1725ede1187" />



# APPLICATION FEATURES

User-friendly graphical interface.

Accepts electrical appliance power ratings.

Calculates energy consumption in kWh.

Estimates electricity charges based on tariff per unit.

Supports different daily usage hours and billing periods.

Displays calculated energy consumption and estimated cost.

Helps users understand and monitor household electricity usage.

# RESULT

Thus, the Energy Consumption Calculator Android application was successfully designed and developed using Android Studio with Java and XML. The application calculates electrical energy consumption in kilowatt-hours and estimates electricity charges based on appliance power rating, usage duration and electricity tariff.

# CONCLUSION

The experiment provides practical knowledge of Android application development, XML-based user interface design, Java programming, event handling and implementation of electrical energy consumption calculations using Android Studio.
