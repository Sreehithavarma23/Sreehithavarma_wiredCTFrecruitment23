# 70ugh_n07_70UgH

- when I went through the description and searched about it I got to know about arduino device connections
- Then I opened the attachment given in description and in that attachment i got a code like this
```
-   char signalAlpha = digitalRead(2) ? '1' : '0';
char signalBeta = digitalRead(3) ? '1' : '0';
char signalGamma = digitalRead(4) ? '0' : '1';
char signalDelta = digitalRead(5) ? '1' : '0';
  

if (signalAlpha == (two + '0')) {
if (!(signalBeta == '1')) {
if (0^(signalGamma == '0')) {
if (signalDelta == '0') {

digitalWrite(enigmaKey, HIGH);
```
  
- Now i have hardware device and four wires
- In that view attachment it has  digital signals from four different pins as (2,3,4,5)
- By using the digitalRead() function given in code the result of each digitalRead() call is being converted into either '1' or '0'
- in that I figured out that  1 is high and 0 is low
- if its 0 then it has to be connected to Gnd and if it 1 which is high then it has to be connected to voltage
- From that code given  signalAlpha digitalRead(2) value gives 1
- From signalBeta digitalRead(3) value it shows that value !1 is not equal to 1 which means 0
- From signalGamma digitalRead(4) value the third condition checks if the result of the XOR operation between 0 and the boolean expression signalGamma == '0' is true this checks if signalGamma is equal to '1' now third condition is equal to 1
- From signalDelta digitlRead(5) value it shows that the value is equals to 0
- After connecting these pins accordingly and connecting the device to laptop i found the flag and kept that flag in given format
