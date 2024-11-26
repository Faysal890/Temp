# Temp
1.
#include <avr/io.h>

int main(void) 
{
    DDRC = (1 << PC0); // DDRC = 0x01

    PORTC = (1 << PC0); // PORTC = 0x01

    while (1)
    {
       
    }
    return 0;
}


2.
#include<avr/io.h>
#include<util/delay.h>
int main() {
	DDRC = 0x01;
	while(1) {
		PORTC = 0x01;
		_delay_ms(100);
		
		PORTC = 0x00;
		_delay_ms(100);
		
	}
}

3, 4.
#  ifndef F_CPU
#  define F_CPU 1000000UL
#  endif
#include <avr/io.h>
#include <util/delay.h>

// Segment codes for displaying digits 0-9 (Common Cathode)
// a, b, c, d, e, f, g
uint8_t digit[10] = {
    0b00111111, // 0
    0b00000110, // 1
    0b01011011, // 2
    0b01001111, // 3
    0b01100110, // 4
    0b01101101, // 5
    0b01111101, // 6
    0b00000111, // 7
    0b01111111, // 8
    0b01101111  // 9
};

void fun() {
	for (int i = 0; i < 10; i++) {
            PORTD = digit[i];  // Output the segment code to PORTB
            _delay_ms(1000);   // Delay 1 second before showing the next digit
        }
}

int main(void) {
    // Configure PORTB as output for the 7-segment display
    DDRB = 0xFF; // All pins of PORTB as output
	DDRD = 0xFF;
    while (1) {
        for (int i = 0; i < 10; i++) {
            PORTB = digit[i];  // Output the segment code to PORTB
			fun();
            _delay_ms(1000);   // Delay 1 second before showing the next digit
        }
    }

    return 0;
}

5.
#include<LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
void setup() {
  lcd.begin(16, 2);
}
void loop() {
  lcd.clear();
  delay(500);
  lcd.setCursor(0, 0);
  lcd.print("Wellcome to ....");
  delay(200);
  lcd.setCursor(0, 1);
  lcd.print("Bangladehs");
  delay(20000);
}

6.
#include<Servo.h>
Servo myServo;
void setup() {
  myServo.attach(9);
}

void loop() {
  myServo.write(0);
  delay(500);
  myServo.write(90);
  delay(500);
  myServo.write(0);
  delay(1000);
  myServo.write(360);
  delay(1000);
}

