# 2nd-Week-task-Electronics-
# On-off LED system code
int pinButton = 8;
int Relay = 2;
int stateRelay = LOW;
int stateButton;
int previous = LOW;
long time = 0;
long debounce = 100;


int stayON = 5000; //stay on for 5000 ms

void setup() {
  pinMode(pinButton, INPUT);
  pinMode(Relay, OUTPUT);
}

void loop() {
  stateButton = digitalRead(pinButton);  
  if(stateButton == HIGH && previous == LOW && millis() - time > debounce) {
    if(stateRelay == HIGH){
      digitalWrite(Relay, LOW);
    } else {

      
       digitalWrite(Relay, HIGH);
       delay(stayON);
       digitalWrite(Relay, LOW);
    }
    time = millis();
  }
  previous == stateButton;
}
# On-off LED System Code Explaination
First, connect pushbutton to pin 8 in the arduino.
then declare relay and assign it in pin 2 in the arduino
after that, intialize the case of relay as low case
then, declare the state of pushbutton
initialize the previous case as low case
declare time initially zero, debounce is 100
make the time of high state of the led is 5 second
make pin 8 ( pushbutton ) as an input, and pin 2 (Relay) as an output
if the pushbutton is pressed, and the previous case is low, and the time is subtracted from millisecond function is greater than debounce value, there is two cases:
firat case, if the relay state is high, the transistor signal is low, and the led is off
second case, tf the relay state is low, the transistor signal is high, and the led is on but after 5 seconds the transistor signal will be low and the led is off. 
