# Construindo um sensor ultrassonico com o HC-SR04 e arduino uno no tinkercad
Exercício roteirizado no Portas de hardware e comunicação em C no 5º Periodo de CC da Estácio. Consulte o funcionamento pratico em Sensor Ultrassonico com o HC-SR04 e Arudino Uno - Simulação no TinkerCad

<img width="1920" height="836" alt="image" src="https://github.com/user-attachments/assets/b298fdc0-76d6-44b5-baa7-ea764b66c39f" />

Na imagem acima, o Arduino Uno R3 foi conectado junto ao sensor HC-SR04 para exemplificar o comportamento de um sensor ultrassonico.
Foi conectado os pinos VCC no pino Power de 5V do Arduino para alimentação, o pino TRIG como saida do pino digital 7 do arduino, ECHO no pino 8 para entrada e o GND no GND power.

| Arduino | HC-SR04 |
| :------ | :------ |
| 5V      | VCC     |
| 7       | TRIG    |
| 8       | ECHO    |
| GND     | GND     |

Para o funcionamento, foi usado o seguinte codigo (fornecido pela faculdade):
````C
// Define os pinos trigPin e echoPin do HC-SR04 nos pinos digitais 7 e 8 respectivamente do arduino
const int trigPin = 7;
const int echoPin = 8;

// Define a velocidade do som 
#define SOUND_SPEED 0.034

// Definido as variaveis de duração, distancia em centimetros e em polegadas (Inch)
long duration;
float distanceCm;
float distanceInch;

// Função principal do arduino, executada no start
void setup(){
    // Define o baund rate (velocidade em bits) 
	Serial.begin(115200); 
    // Define as variaveis de pin do Uno como saida e entrada
  	pinMode(trigPin, OUTPUT);
    pinMode(echoPin, INPUT); 
}

// Função que roda em loop
void loop(){
    // Envia o sinal baixo para o trigPin e espera dois microsegundos
	digitalWrite(trigPin, LOW);
  	delayMicroseconds(2);

    // Envia o sinal alto para o trigPin e espera dez microsegundos
  	digitalWrite(trigPin, HIGH);
  	delayMicroseconds(10);

    // Define o valor da duração em pulsos do pino de entrada para alto e depois define a distancia em centimetros multiplicando a duração pela velocidade do som divido por 2, imprime no console e espera por 1000 milisegundos
  	duration = pulseIn(echoPin, HIGH);
  	distanceCm = duration * SOUND_SPEED/2;
  	
 	Serial.print("Distancia (em): ");
  	Serial.println(distanceCm);
  
  	delay(1000);
}
````
- Pra que caralhos existe o Serial.begin() e quais valores ele pode receber?

