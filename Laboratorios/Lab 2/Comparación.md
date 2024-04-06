## Generación de señales

Carácterísticas y comparación:
# Primera señal
Frecuencia= 1KHz
Forma= sinusoidal
Vpp=5V, offset= 0V

<p align="center">
  <img src="https://github.com/kimberlytc/ISB_trial/blob/25331a60df9f427585972f7dfff6044a9a5f0a26/Hardware/sinusoidal.jpeg">
</p>


## Código Arduino
```
const int analogPin = A0; // Define la constante analogPin como el pin A0, 
//que será utilizado para leer la señal analógica.

unsigned long lastMsg = 0; //almacenar el tiempo en milisegundos del último mensaje enviado.
float F=1;                      // 1 hz
double Fs = 10*F;               // 10 hz
double Ts_ms = (1/Fs)*1000;     //  100 ms  

void setup() {
  Serial.begin(9600); //Inicia la comunicación serial
  while (!Serial);
  //Serial.println("R1:,R2:,");
  pinMode(analogPin, INPUT);
}

void loop() {

  unsigned long now = millis();

  if (now - lastMsg > Ts_ms) {
    
    lastMsg = now;

    int r1 = analogRead(analogPin);

    Serial.print("Señal1:");
    Serial.println(r1);

  }

}

```
