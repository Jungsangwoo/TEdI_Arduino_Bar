1. Arduino Uno/Leonardo
2. [Linear Motor](http://mechasolution.com/shop/goods/goods_view.php?goodsno=542287&category=131019002004) 15,400원
3. [Motor Driver](http://mechasolution.com/shop/goods/goods_view.php?goodsno=1544&category=131014) 1,870원
4. [MF Cable,30cm/MF](http://mechasolution.com/shop/goods/goods_view.php?goodsno=540335&category=137003016) 880원 
5. [9V Battery X2](http://mechasolution.com/shop/goods/goods_view.php?goodsno=539736&category=135001) 1,210원
6. [9V Battery Holder](http://mechasolution.com/shop/goods/goods_view.php?goodsno=330441&category=135002) 990원
7. [9V Battery Holder(JACK)](http://mechasolution.com/shop/goods/goods_view.php?goodsno=71506&category=135002) 1,320원 
8. 우드락
9. [BreadBoard](http://mechasolution.com/shop/goods/goods_view.php?goodsno=5869&category=134001) 1,430원
10. [스탠밴드](http://storefarm.naver.com/good09/products/370709244?NaPm=ct%3Dj7lrwaf4%7Cci%3D97a0d116fc75c8e068c5fe4d5cfffd738140c80c%7Ctr%3Dsls%7Csn%3D165729%7Chk%3D0a06d6ddae89906e3ffed7beecac117afd4a42f2)



<제품명 및 코딩>

제품명:L12-50-100-12-P(리니어 모터)



int speedPin = 3; // H-bridge enable pin for speed control 
int motor1APin = 6; // H-bridge leg 1 
int motor2APin = 7; // H-bridge leg 2 
int ledPin = 13; // status LED
int positionfeed = 0;
int speed_value_motor1; // value for motor speed 
int dir = 1; //1 pos stoke, 0 is neg stroke
int targetpos = 700;
void setup() { 
 
 // set digital i/o pins as outputs: 
 pinMode(speedPin, OUTPUT); 
 pinMode(motor1APin, OUTPUT); 
 pinMode(motor2APin, OUTPUT); 
 pinMode(ledPin, OUTPUT); 
 Serial.begin(9600);
 
} 
 
void loop() { 
  positionfeed = analogRead(A0);
  digitalWrite(ledPin, HIGH); // status LED is always on 
  int error = targetpos - positionfeed;
  
  if(error > 5 && dir == 1)
 { 
 digitalWrite(motor1APin, LOW); // set leg 1 of the H-bridge low 
 digitalWrite(motor2APin, HIGH); // set leg 2 of the H-bridge high 
 }
 else if (error < -5 && dir == 0)
 {
 digitalWrite(motor1APin, HIGH); // set leg 1 of the H-bridge low 
 digitalWrite(motor2APin, LOW); // set leg 2 of the H-bridge high 
 }
 else 
 {
  digitalWrite(motor1APin, LOW);
  digitalWrite(motor2APin, LOW);
 }
   speed_value_motor1 = 100; // half speed 
 analogWrite(speedPin, speed_value_motor1); // output speed as 
} 