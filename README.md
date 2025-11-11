# P6
// Include Stepper library 
#include <Stepper.h> 
// Define number of steps per revolution (depends on motor; commonly 200) 
const int stepsPerRevolution = 200; 
// Create stepper motor object with 4 control pins connected to L293D 
// (IN1 = 8, IN2 = 9, IN3 = 10, IN4 = 11) 
Stepper myStepper(stepsPerRevolution, 8, 10, 9, 11); 
void setup() {
myStepper.setSpeed(60); // You can vary this to control speed (e.g., 30, 
100) 
// Initialize serial monitor 
Serial.begin(9600); 
Serial.println("Stepper Motor Control Start"); 
}
void loop() { 
// Rotate clockwise 1 full revolution 
Serial.println("Clockwise rotation"); 
myStepper.step(stepsPerRevolution); // 200 steps for 1 revolution 
delay(1000);
// Rotate counterclockwise 1 full revolution 
Serial.println("Counterclockwise rotation"); 
myStepper.step(-stepsPerRevolution); // negative for opposite direction 
delay(1000); 
// Change speed 
myStepper.setSpeed(120); // Increase speed to 120 RPM 
Serial.println("Faster clockwise rotation"); 
myStepper.step(stepsPerRevolution); 
delay(1000);
// Slow down speed 
myStepper.setSpeed(30); // Decrease speed to 30 RPM
Serial.println("Slower counterclockwise rotation"); 
myStepper.step(-stepsPerRevolution); 
delay(1000); 
}
