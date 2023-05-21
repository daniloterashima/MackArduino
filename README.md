# MackArduino
# i)         Uma breve descrição do funcionamento e uso para quem quiser reproduzir.
###. Meu objetivo neste artigo é trazer a forma mais simples de automação utilizando Arduíno, que permitirá o reconhecimento de oscilações de ruído para acionar leds automaticamente.
# ii)       O software desenvolvido e a documentação de código.
###//DANILO MASSANORI TERASHIMA DA SILVA
//MACKENZIE - 21015775
//ANALISE E DESENVOLVIMENTO DE SISTEMAS


int sensorPin = 14;     // Pino do sensor de palmas (conecte ao pino digital 2)
int ledPin = 17;       // Pino do LED (conecte ao pino digital 13)
int contadorPalmas = 0;
int palmaAnterior = 0;

void setup() {
  pinMode(ledPin, OUTPUT);        // Define o pino do LED como saída
  pinMode(sensorPin, INPUT);      // Define o pino do sensor como entrada
  Serial.begin(9600);             // Inicializa a comunicação serial (opcional)
}

void loop() {
  int palmaAtual = digitalRead(sensorPin);  // Lê o valor do sensor de palmas
  
  if (palmaAtual == HIGH && palmaAnterior == LOW) {
    // Palma detectada
    contadorPalmas++;
    delay(1000);  // Aguarda um curto intervalo para evitar detecção de múltiplas palmas
    
    if (contadorPalmas == 1) {
      digitalWrite(ledPin, HIGH);  // Acende o LED
      Serial.println("Luz acesa"); // Imprime no monitor serial (opcional)
    } else if (contadorPalmas == 2) {
      digitalWrite(ledPin, LOW);   // Apaga o LED
      Serial.println("Luz apagada"); // Imprime no monitor serial (opcional)
      contadorPalmas = 0;           // Reinicia o contador de palmas
    }
  }
  
  palmaAnterior = palmaAtual;   // Atualiza o valor anterior do sensor
}


# iii)      A descrição do hardware utilizado (plataformas de desenvolvimento, sensores, atuadores, impressão 3D de peças, medidas de peças e caixas etc.)
## Hardware
##Placa Wifi Esp32 Doit Devkit Esp32-wroom-32, Sensor de SOM, Mini Protoboard 170 pontos, 20 Jumpers, Bateria 9 volts, Clip bateria, Resistores 10k, Leds verdes e vermelhos 
## iv)      A documentação das interfaces, protocolos e módulos de comunicação.
Utilização do Protocolo MQQT com o broker HiveMQ.
