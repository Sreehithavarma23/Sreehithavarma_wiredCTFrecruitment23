# extraCt
`Embedded`

- I connected the hardware device to laptop via USB
- After opening arduino IDE
- Then after select the board as Arduino uno and COM port as it flashes com port6 USB then see your code to the ESP8266.
- Open the serial monitor at a baud rate of 115200. You should see the content of the file printed on the serial monitor,115200 as given in the description.
- We have to find code to extract data from a file stored in the spi flash of esp8266
- Now after connceting we get text now we need to extract the data by using c program to extract the flag.
```
#include <FS.h>  // Include the SPIFFS library

void setup() {
  Serial.begin(115200);
  Serial.println();

  // Initialize the SPIFFS file system
  if (!SPIFFS.begin()) {
    Serial.println("Failed to mount file system");
    return;
  }

  // Open the file for reading
  File file = SPIFFS.open("/myfile.txt", "r");
  if (!file) {
    Serial.println("Failed to open file for reading");
    return;
  }

  // Read and print the file's content
  while (file.available()) {
    Serial.write(file.read());
  }

  // Close the file
  file.close();
}

void loop() {
  // Your code here
}
```
- In this code we have to replace ` /myfile.txt` with the actual path to your file given there.
- Now with this you will get the flag and place the flag in given given format.
