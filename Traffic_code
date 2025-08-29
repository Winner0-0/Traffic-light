const int pin_led_rojo = 13;
const int pin_led_amarillo = 12;
const int pin_led_verde = 11;
const int pin_boton = 2;

int estadoBoton = 0; //para almacenar el estado del boton, 0 = no presionado, 1 = presionado
bool semaforoActivo = false; //para controlar si la sequencia del semaforo esta activa
unsigned long tiempoInicioSequencia; //para guardar cuando empezon la sequencia del semaforo
unsigned long tiempoActual; // guarda el tiempo actual
void setup() {
  pinMode(pin_led_rojo, OUTPUT);
  pinMode(pin_led_amarillo, OUTPUT);
  pinMode(pin_led_verde, OUTPUT);
  pinMode(pin_boton, INPUT);
//Output (acts on it)
//Input (reads if it's acted on)

  Serial.begin(9600);
  Serial.println("Traffic system ready!");
  digitalWrite(pin_led_rojo, HIGH); // enciende el LED rojo (HIGH = higher end (5V))
  digitalWrite(pin_led_amarillo, LOW); // apaga el LED amarillo (LOW = lower end (0V))
  digitalWrite(pin_led_verde, LOW);
  
}

void loop() {
  tiempoActual = millis(); // lee y guarda el tiempo actual desde arduino en millisegundos
  estadoBoton = digitalRead(pin_boton); //lee el estado del pin del boton HIGH = presionado, LOW = no p.
  //secuencia para si el boton es presionado y la sequencia no esta activa
  if (estadoBoton == HIGH && semaforoActivo = false){
    Serial.println("Boton presionado. Iniciando sequencia...")
    semaforoActivo = true; //marca que la sequencia del semaforo esta activa
    tiempoInicioSequencia = tiempoActual; //guarda el timepo ene el que se presiono el boton

    Serial.println(" 10 segundos adicionales en rojo...");
    digitalWrite(pin_led_rojo, HIGH);
    digitalWrite(pin_led_amarillo, LOW);
    digitalWrite(pin_led_verde, LOW); 
  }
    // Lógica de la secuencia del semáforo si está activa
  if (semaforoActivo) {
    // Calculamos el tiempo transcurrido desde el inicio de la secuencia
    unsigned long tiempoTranscurrido = tiempoActual - tiempoInicioSecuencia;

    // FASE 1: Rojo/red por 10 segundos adicionales
    if (tiempoTranscurrido >= 0 && tiempoTranscurrido < 10000) { 
      // Ya estamos en rojo, solo aseguramos que los otros estén apagados
      digitalWrite(pin_led_rojo, HIGH);
      digitalWrite(pin_led_amarillo, LOW);
      digitalWrite(pin_led_verde, LOW);
      Serial.print("Rojo... Tiempo restante para amarillo: ");
      Serial.print((10000 - tiempoTranscurrido) / 1000); // Convierte a segundos
      Serial.println(" segundos");
    }
    // FASE 2: Amarillo/yellow por 10 segundos
    else if (tiempoTranscurrido >= 10000 && tiempoTranscurrido < 20000) { // De 10 a 20 segundos
      digitalWrite(pin_led_rojo, LOW);
      digitalWrite(pin_led_amarillo, HIGH); // Enciende el amarillo
      digitalWrite(pin_led_verde, LOW);
      Serial.print("Amarillo... Tiempo restante para verde: ");
      Serial.print((20000 - tiempoTranscurrido) / 1000);
      Serial.println(" segundos");
    }
    // FASE 3: Verde/green por 30 segundos
    else if (tiempoTranscurrido >= 20000 && tiempoTranscurrido < 50000) { // De 20 a 50 segundos (20+30=50)
      digitalWrite(pin_led_rojo, LOW);
      digitalWrite(pin_led_amarillo, LOW);
      digitalWrite(pin_led_verde, HIGH); // Enciende el verde
      Serial.print("Verde... Tiempo restante para rojo: ");
      Serial.print((50000 - tiempoTranscurrido) / 1000);
      Serial.println(" segundos");
    }
    // FASE 4: Go back to red and restart
    else if (tiempoTranscurrido >= 50000) {
      Serial.println("Fin de la secuencia. Volviendo a Rojo.");
      digitalWrite(pin_led_rojo, HIGH);
      digitalWrite(pin_led_amarillo, LOW);
      digitalWrite(pin_led_verde, LOW);
      semaforoActivo = false; 
    }
  }

  delay(100); 


}
