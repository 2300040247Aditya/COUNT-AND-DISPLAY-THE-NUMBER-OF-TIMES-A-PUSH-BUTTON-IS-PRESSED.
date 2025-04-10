# COUNT-AND-DISPLAY-THE-NUMBER-OF-TIMES-A-PUSH-BUTTON-IS-PRESSED.
const int buttonPin = 2;    
int buttonState;            
int lastButtonState = LOW; 
unsigned long lastDebounceTime = 0;  
unsigned long debounceDelay = 50;    

int counter = 0;            

void setup() {
  pinMode(buttonPin, INPUT);
  Serial.begin(9600);
  Serial.println("Push Button Counter Initialized");
}

void loop() {
  int reading = digitalRead(buttonPin);

  
  if (reading != lastButtonState) {
    lastDebounceTime = millis(); 
  }

  if ((millis() - lastDebounceTime) > debounceDelay) {
   
    if (reading != buttonState) {
      buttonState = reading;

      if (buttonState == HIGH) {
        counter++;
        Serial.print("Button Pressed! Count: ");
        Serial.println(counter);
      }
    }
  }

  lastButtonState = reading;
}

Push Button Counter Initialized
Button Pressed! Count: 1
Button Pressed! Count: 2
Button Pressed! Count: 3


![count and display](https://github.com/user-attachments/assets/db927a25-2534-499c-bcbd-788fd98f3803)

