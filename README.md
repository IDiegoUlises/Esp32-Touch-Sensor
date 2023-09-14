# Esp32-Touch-Sensor

### Codigo que obtiene el valor del sensor touch
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

### Codigo que ya obtenido el valor del sensor touch prende y apaga un led
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
```
