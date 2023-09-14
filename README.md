# Esp32 Touch Sensor

### Touch Pins Disponibles
| Touch | Pins | 
|  :---: | :---  |          
| T0 | GPIO 4 |
| T1 | GPIO 36(Solo disponible en la version de 36 pins) |
| T2 | GPIO 2 |
| T3 | GPIO 15|
| T4 | GPIO 13|
| T5 | GPIO 12 |
| T6 | GPIO 14 |
| T7 | GPIO 27 |
| T8 | GPIO 33 |
| T9 | GPIO 32 |

### Codigo para obtener el umbral 
```c++
void setup()
{
  //Inicia el puerto serial
  Serial.begin(115200);
}

void loop()
{
  //Obtiene el valor del sensor touch
  int sensor = touchRead(T0);

  //Imprime el valor del sensor
  Serial.println(sensor);

  //Retardo
  delay(500);
}
```

### Codigo que con un umbral controla un led
```c++
//Pins del led
int led = 2;

//Valor del umbral
int umbral = 20;

void setup()
{
  //Inicia el puerto serial
  Serial.begin(115200);

  //Declara el pin como salida
  pinMode(led, OUTPUT);

  //Los pins del sensor touch no deben inicializarse
  //porque ya estan listos para usar
}

void loop()
{
  //Obtiene el valor del sensor touch
  int sensor = touchRead(T0);

  //Imprime el valor del sensor
  Serial.println(sensor);

  //Si el valor del sensor es menor que el umbral
  if (sensor < umbral)
  {
    digitalWrite(led, HIGH); //Enciende el led
    Serial.println("Led Encendido"); //Imprime en el puerto serial
  }

  //En caso que el sensor es mayor que el umbral
  else
  {
    digitalWrite(led, LOW); //Apaga el led
    Serial.println("Led Apagado"); //Imprime en el puerto serial
  }

  //Retardo
  delay(500);
}
```

![](https://github.com/IDiegoUlises/Esp32-Touch-Sensor/blob/main/Imagenes/GIF-230913_234400.gif)
