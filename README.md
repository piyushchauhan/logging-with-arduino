# logging-with-arduino
Things that are needed to log variables from Arduino to txt or csv file

`arduino_code.ino`
```
void setup() {
  // Some initializations
  Serial.begin(9600);

}

void loop() {
  /*
   *  Some code here
   */
  Serial.println(value);
}
```

## Logging Using Python

### Writing to txt file
```
import serial
from datetime import datetime

sensor = "DH11" # temperature sensor
serial_port = '/dev/ttyACM0'
baud_rate = 9600
path = "%s_LOG_%s.txt" % (str(datetime.now()), sensor)
ser = serial.Serial(serial_port, baud_rate)
with open(path, 'w+') as f:
    while True:
        line = ser.readline()
        f.writelines([line.strip(), " t = %s \n " % (datetime.now())])
```
