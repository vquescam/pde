Unidad Didáctica 1:
EJEMPLO 1
Programación Dirigida por Eventos
UAX. C O M

Unidad didáctica X: Ejercicio con solución X
Nombre de la asignatura
1. Enunciado
En este ejercicio práctico, desarrollaremos una aplicación Android con un enfoque en la
experiencia de usuario, siguiendo los Objetivos de Desarrollo Sostenible (ODS) de la Agenda
2030, específicamente el ODS 3: Salud y Bienestar. La aplicación ayudará a los usuarios a llevar
un registro de sus hábitos de salud, como el consumo de agua, el ejercicio diario y la calidad del
sueño.
Ejercicio 1: Registro de Hábitos Saludables
Introducción
El seguimiento de hábitos saludables es fundamental para mantener un estilo de vida
equilibrado. Con la proliferación de dispositivos móviles, es posible utilizar aplicaciones para
registrar y analizar nuestros hábitos diarios, lo que puede conducir a mejoras en la salud y el
bienestar. Este ejercicio se centra en desarrollar una aplicación básica que permita a los usuarios
registrar sus hábitos de consumo de agua, ejercicio y sueño.
Enunciado del Problema
Desarrollar una aplicación Android que permita a los usuarios:
1. Registrar el consumo diario de agua.
2. Registrar la cantidad de ejercicio realizado cada día.
3. Registrar las horas de sueño.
4. Visualizar un resumen diario de sus hábitos.
2. Solución
A continuación, se presenta una solución detallada para desarrollar la aplicación propuesta.
Paso 1: Configuración del Proyecto
1. Iniciar un nuevo proyecto en Android Studio con una "Actividad Vacía".
2. Configurar los archivos build.gradle para asegurarse de tener las dependencias
necesarias.
// build.gradle (Project level)
allprojects {
UAX. C O M
© Universidad Alfonso X el Sabio

Unidad didáctica X: Ejercicio con solución X
Nombre de la asignatura
repositories {
google()
mavenCentral()
}
}
// build.gradle (Module level)
dependencies {
implementation 'androidx.appcompat:appcompat:1.3.0'
implementation 'com.google.android.material:material:1.4.0'
implementation 'androidx.constraintlayout:constraintlayout:2.0.4'
// Dependencias adicionales si es necesario
}
Paso 2: Diseño de la Interfaz de Usuario
Crear un archivo XML para la actividad principal ( ) que incluya campos de
activity_main.xml
entrada para el consumo de agua, ejercicio y sueño, así como un botón para guardar los datos y
un TextView para mostrar el resumen diario.
<androidx.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">
<EditText
android:id="@+id/editTextWater"
android:layout_width="0dp"
android:layout_height="wrap_content"
android:hint="Consumo de agua (litros)"
android:inputType="numberDecimal"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toTopOf="parent" />
<EditText
android:id="@+id/editTextExercise"
android:layout_width="0dp"
android:layout_height="wrap_content"
android:hint="Ejercicio (minutos)"
android:inputType="number"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toBottomOf="@+id/editTextWater" />
<EditText
android:id="@+id/editTextSleep"
android:layout_width="0dp"
android:layout_height="wrap_content"
android:hint="Sueño (horas)"
android:inputType="numberDecimal"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toBottomOf="@+id/editTextExercise" />
UAX. C O M
© Universidad Alfonso X el Sabio

Unidad didáctica X: Ejercicio con solución X
Nombre de la asignatura
<Button
android:id="@+id/buttonSave"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Guardar"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toBottomOf="@+id/editTextSleep" />
<TextView
android:id="@+id/textViewSummary"
android:layout_width="0dp"
android:layout_height="wrap_content"
android:text="Resumen diario"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toBottomOf="@+id/buttonSave" />
</androidx.constraintlayout.widget.ConstraintLayout>
Paso 3: Implementación de la Actividad Principal
Implementar la lógica en para manejar la entrada de datos y mostrar el
MainActivity.java
resumen diario.
package com.example.healthtracker;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;
public class MainActivity extends AppCompatActivity {
private EditText editTextWater;
private EditText editTextExercise;
private EditText editTextSleep;
private TextView textViewSummary;
private Button buttonSave;
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);
editTextWater = findViewById(R.id.editTextWater);
editTextExercise = findViewById(R.id.editTextExercise);
editTextSleep = findViewById(R.id.editTextSleep);
textViewSummary = findViewById(R.id.textViewSummary);
buttonSave = findViewById(R.id.buttonSave);
UAX. C O M
© Universidad Alfonso X el Sabio

Unidad didáctica X: Ejercicio con solución X
Nombre de la asignatura
buttonSave.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View v) {
saveData();
}
});
}
private void saveData() {
String water = editTextWater.getText().toString();
String exercise = editTextExercise.getText().toString();
String sleep = editTextSleep.getText().toString();
if (water.isEmpty() || exercise.isEmpty() || sleep.isEmpty())
{
Toast.makeText(this, "Por favor, complete todos los
campos", Toast.LENGTH_SHORT).show();
} else {
String summary = "Consumo de agua: " + water + " litros\n"
+ "Ejercicio: " + exercise + " minutos\n"
+ "Sueño: " + sleep + " horas";
textViewSummary.setText(summary);
}
}
}
3. Conclusión
Este ejercicio práctico permite a los estudiantes aplicar conceptos de desarrollo de aplicaciones
Android para crear una herramienta útil que contribuye al ODS 3: Salud y Bienestar. A través de
esta actividad, los estudiantes desarrollan habilidades en la creación de interfaces de usuario
interactivas y el manejo de datos de entrada del usuario, fomentando así prácticas de vida
saludables.
UAX. C O M
© Universidad Alfonso X el Sabio

G R A C I A S
UAX.COM