# IoT-Based Home Health Monitoring System

This project is a home-based health monitoring prototype that uses an *ESP32 microcontroller* and sensors to collect real-time environmental data such as temperature , heart rate and oxygen saturation. The data is displayed on a web dashboard using [lovable.app](https://lovable.app), providing an easy-to-use interface for remote patient monitoring


## Key Features

- *ESP32 Microcontroller* for Wi-Fi connectivity
- *DHT22 Sensor* to monitor temperature and humidity
- MAX30102 sensor to monitor haert rate and oxygen saturation
- - *Web Dashboard* built with [lovable.app](https://alice-guardian-angel-system.lovable.app/)
- Real-time data collection, transmission and visualization
-simulation tested on [wokwi] an online simulator(https://wokwi.com/projects/428308235390013441)
**Note**wokwi and lovable app are not connected.wokwi was
  used for simulation, while lovable.app was used to build
  the actual web dashboard for dispalying rea-time data
  from the ESP32 device.

## Dashboard Screenshots

### Real-Time Monitoring View
![Dashboard 1](screenshot%201.jpg)

### Sensor Data Visualization
![Dashboard 2](screenshot%202.jpg)

### Dashboard Overview
![Dashboard 3](screenshot%203.jpg)

## Demo Video

Watch a live demo of the project:  
*[Click to view demo](https://drive.google.com/file/d/10aoKEo7vGxX4DBWdYWNZWmmFUdVB6ad0/view?usp=drive_link)*


## Project Report

Download the full project report here:  
[*Download IoT Project Report (PDF)*](IoT%20PROJECT%20REPORT.pdf)


REFERENCES FOR THE REPORT

Royal Philips. (n.d.). Community Life Centers: Reinventing Primary Healthcare. https://www.philips.com/a-w/about/community-life-centers.html

Afyarekod. (n.d.). Transforming Digital Health Across Africa.  https://afyarekod.com

Intel. (n.d.). Smart Health Initiative: Improving Patient Care with Technology. Retrieved  from https://www.intel.com/content/www/us/en/healthcare-it/smart-health-initiative.html 
World Health Organization. (2022). Digital Health. Retrieved from https://www.who.int/health-topics/digital-health 

Rghioui, A., & Oumnad, A. (2018). Remote health monitoring using IoT: Review and challenges. Journal of Telecommunication, Electronic and Computer Engineering (JTEC), 10(1-6), 143–146. Retrieved from https://www.researchgate.net/publication/328082049 

### Code Snippet: ESP32 Sensor Reading with Simulated Vitals

```cpp
#include "DHT.h"
#define DHTPIN 5
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
  randomSeed(analogRead(0)); // For generating random values
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  int heartRate = random(60, 100);         // Simulated heart rate in BPM
  int spo2 = random(95, 100);              // Simulated SpO₂ percentage

  if (!isnan(temperature) && !isnan(humidity)) {
    Serial.print("Temp: ");
    Serial.print(temperature);
    Serial.print("°C, Humidity: ");
    Serial.print(humidity);
    Serial.print("%, Heart Rate: ");
    Serial.print(heartRate);
    Serial.print(" BPM, SpO2: ");
    Serial.print(spo2);
    Serial.println("%");
  }

  delay(2000);
}


