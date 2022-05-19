#define RED_LED 3		//red led pin
#define GREEN_LED 5		//green led pin
#define BLUE_LED 6		//blue led pin
#define BUTTON 2		//BUTTON pin
#define XP	A0			//X Potentiometer pin
#define YP	A1			//Y Potentiometer pin

char cur_mode = 'a';	//current mode flag, a=modeA, b=modeB
int x;					//x value
int y;					//y value



void setup()
{
  pinMode(RED_LED, OUTPUT);   //set red led pin as output
  pinMode(GREEN_LED, OUTPUT); //set green led pin as output
  pinMode(BLUE_LED, OUTPUT);  //set blue led pin as output
  pinMode(XP, INPUT);		  //set x Potentiometer as input
  pinMode(YP, INPUT);		  //set x Potentiometer as input
  
  pinMode(BUTTON, INPUT_PULLUP);  //set Button pin as pullup input
  //set Button as External Interrupt with change_mode function 
  attachInterrupt(digitalPinToInterrupt(BUTTON), change_mode, FALLING); 
  Serial.begin(9600);
  
  // TIMER 1 for interrupt frequency 4 Hz:
  cli(); // stop interrupts
  TCCR1A = 0; // set entire TCCR1A register to 0
  TCCR1B = 0; // same for TCCR1B
  TCNT1  = 0; // initialize counter value to 0
  // set compare match register for 4 Hz increments
  OCR1A = 62499; // = 16000000 / (64 * 4) - 1 (must be <65536)
  // turn on CTC mode
  TCCR1B |= (1 << WGM12);
  // Set CS12, CS11 and CS10 bits for 64 prescaler
  TCCR1B |= (0 << CS12) | (1 << CS11) | (1 << CS10);
  // enable timer compare interrupt
  TIMSK1 |= (1 << OCIE1A);
  sei(); // allow interrupts
}

void loop()
 //send the values of x and y to RGB_PWM (depends on the state)
 // max value of x and y is 1023, max of x/4 or y/4 is 255 (int) 
{
  if (cur_mode == 'a')
    RGB_PWM(y / 4 , x / 4 , 0); //y-> RED, x-> GREEN, b-> 0 value, onst
  else
    RGB_PWM((x + y )/ 8, x / 4, x / 4); // (x+y)/2 -> RED, x->GRENN, B->GREEN
}

void change_mode()
  //External Interrupt function ,it is changing the current mode
{
  if(cur_mode == 'a')
    cur_mode = 'b';
  else
    cur_mode = 'a';
}

ISR(TIMER1_COMPA_vect)
  //Internal Interrupt, sampales values of x and y
{
  x = analogRead(XP); 
  y = analogRead(YP);
}

void RGB_PWM(int r, int g, int b)
  //sends pwm for each led, serial plotter
{
  analogWrite(RED_LED, r);  //red
  analogWrite(GREEN_LED, g);//green
  analogWrite(BLUE_LED, b); //blue
  //serial plotter
  Serial.print(r);
  Serial.print(",");
  Serial.print(g);
  Serial.print(",");
  Serial.println(b);
}
