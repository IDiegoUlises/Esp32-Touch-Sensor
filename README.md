# Esp32-Touch-Sensor

### Codigo copiado para obtener el umbral modificar
```c++
void setup() {
  Serial.begin(115200);
  delay(1000); // give me time to bring up serial monitor
  Serial.println("ESP32 Touch Test");
}

void loop() {
  Serial.println(touchRead(4));  // get value of Touch 0 pin = GPIO 4
  delay(1000);
}
```

### Codigo con el umbral copiado para modificar
```c++
// set pin numbers
const int touchPin = 4; 
const int ledPin = 16;

// change with your threshold value
const int threshold = 20;
// variable for storing the touch pin value 
int touchValue;

void setup(){
  Serial.begin(115200);
  delay(1000); // give me time to bring up serial monitor
  // initialize the LED pin as an output:
  pinMode (ledPin, OUTPUT);
}

void loop(){
  // read the state of the pushbutton value:
  touchValue = touchRead(touchPin);
  Serial.print(touchValue);
  // check if the touchValue is below the threshold
  // if it is, set ledPin to HIGH
  if(touchValue < threshold){
    // turn LED on
    digitalWrite(ledPin, HIGH);
    Serial.println(" - LED on");
  }
  else{
    // turn LED off
    digitalWrite(ledPin, LOW);
    Serial.println(" - LED off");
  }
  delay(500);
}
```

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
