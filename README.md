# Hydroponix [WIP]
An IoT automated plant propagation system built with Python on the Raspberry Pi Zero W with InfluxDB, Flask, Bootstrap 4, requests, psutil, Adafruit_DHT, picamera and more.


### Usage:
```
Usage: python3 main.py <snapshotIntervalInSecs>
```
```python3
python3 main.py 3600 # Sends 1 data snapshot per hour  
```
```python3
python3 main.py      # Sends 1 data snapshot every 2 hours (default interval)  
```

### Currently implemented:
- All electronic components are properly coordinated. The soil moisture sensor can be successfully read, the water pump can be flicked on and off via the relay, the humidity and ambient temperature can be acquired reliably
- Flask web app interface is able to fetch data from sensors, display camera module output and allow remote control over the water pump
- Enable/disable auto-watering and force water functionality working, using psutil to start, stop and manage processes
- Currently able to send HTTP post requests to timz.dev/Hydroponix at regular intervals
- Automated HTTP POST requests are able to capture camera output and send image files with humidity and temperature readings to timz.dev/Hydroponix
- Data snapshots are stored inside an instance of InfluxDB which is running locally

### Work in progress and planned features:
- Be able to pull average sensor readings each hour from the database
- Use data visualisation libraries on sensor data
- Use threading's Timer object to delegate LCD writing

### Bugs:
- Humidity/temperature sensor is unable to successfully get both readings on every single call to the Adafruit_DHT.read function. The current workaround is to use a recursive function and recall until success. Could alternatively just take the average of the most recent 5 readings, for example
- Need to fix the paths to have a designated camera output folder and manage local dependencies (LCDDriver)

### Components:
5V submersible brushless DC pump, soil moisture sensor, 5V electromechanical relay module, humidity and temperature sensor (DHT22), USB 3.0 breakout boards, LCD1602 16x2 with I2C backpack, HC-SR501 passive infrared motion sensor

### Pump Specifications:
- Qiaoran QR50A
- Brushless (longer working life and lower noise level compared to brushed motors)
- Input: DC, 5V, 2.4W
- Max liquid temperature: 100 degrees celcius
- Water height max: 200cm
