# IoT-Based Home Health Monitoring System

This project is a home-based health monitoring prototype that uses an *ESP32 microcontroller* and sensors to collect real-time environmental data such as temperature , heart rate and oygen saturation. The data is displayed on a web dashboard using [lovable.app](https://lovable.app), providing an easy-to-use interface for remote patient monitoring


## Key Features

- *ESP32 Microcontroller* for Wi-Fi connectivity
- *DHT22 Sensor* to monitor temperature and humidity
- MAX30102 sensor to monitor haert rate and oxygen saturation
- *Web Dashboard* built with [lovable.app](https://lovable.app)
- Real-time data collection,transmission and visualization
- Buzzer alert for abnormal readings (optional)

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

### Code Snippet: ESP32 Sensor Reading

```cpp
#include "DHT.h"
#define DHTPIN 15
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  dht.begin();
}

void loop() {
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();

  if (!isnan(temperature) && !isnan(humidity)) {
    Serial.print("Temp: ");
    Serial.print(temperature);
    Serial.print("°C, Humidity: ");
    Serial.println(humidity);
  }

  

## Project Report

You can download the full project report here:  
[Download IoT Project Report](IoT%20PROJECT%20REPORT.docx)

## Project Structure
├── README.md ├── IoT PROJECT REPORT.docx ├── screenshot 1.jpg ├── screenshot 2.jpg ├── screenshot 3.jpg 

---

Feel free to fork, improve, or use this project for educational purposes.


