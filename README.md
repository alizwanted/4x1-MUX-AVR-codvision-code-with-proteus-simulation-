//  4x1-MUX-AVR-codvision-code-with-proteus-simulation-
// create a 4 to 1 multiplexer using avr microchips and codevision C language 

#include <mega32.h>  //define your micro

void main(void)
{
char data;
DDRD=0x08;    // set port d as input 0b00001000    D.3 is output led
PORTD=0x07;   // turn on pullup resistors   0b

DDRB=0x00;  // set port b as input 0b00000000
PORTB=0x0f; // // turn on pullup resistors

while (1)
      {
       PORTD.3=0;   // if the while phrase is not established the led is off
           while(PIND.2==0)  // if the enable pin is logical 0
           {
            data=PIND;   //reading D port state
            data&=0x03;    // we need just D.0 and D.1 state so we AND it with 0b00000011

            switch(data)
                {
                 case 0:   // if we selected s1=0 & s2=0 ===>>>  selected pin will be B.0
                 PORTD.3=PINB.0;
                 break;

                 case 1:
                 PORTD.3=PINB.1;
                 break;

                 case 2:
                 PORTD.3=PINB.2;
                 break;

                 case 3:
                 PORTD.3=PINB.3;
                 break;
                } // end of switch


           }// end of while


      }   // end of while(1)
}
