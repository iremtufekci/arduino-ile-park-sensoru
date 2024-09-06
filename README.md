# arduino-ile-park-sensoru
#define ecopin 6
#define trigpin 7
#define buzzerpin 8
int maximumRange=50;
int minimumRange=0;
void setup() {
  // put your setup code here, to run once:
  pinMode(trigpin,OUTPUT);
  pinMode(ecopin,INPUT);
  pinMode(buzzerpin,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
int olcum=mesafe(maximumRange,minimumRange);
melodi(olcum*10);

}
int mesafe(int max,int min){
  long duration,distance;
  digitalWrite(trigpin,LOW);
  delayMicroseconds(2);
  digitalWrite(trigpin,HIGH);
  delayMicroseconds(10);
  digitalWrite(trigpin,LOW);

  duration = pulseIn(ecopin,HIGH);
  distance =duration/58.2;
  delay(50);
  if(distance>=max || distance<=min)
  return 0;
  return distance;

}
int melodi(int dly){
tone(buzzerpin,441);
delay(dly);
noTone(buzzerpin);
delay(dly);




}
