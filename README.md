[![Build Status](https://travis-ci.com/AznStevy/Heart-Rate-Monitor.svg?branch=master)](https://travis-ci.com/AznStevy/Heart-Rate-Monitor)


## Project Summary
The Internet of Things (IoT) is one of the most promising technologies for the near future. Healthcare will receive great benefits with the evolution of this technology.  This project presents a demonstration for the review of techniques based on IoT for healthcare and is intended for fitness enthusiasts for remote health monitoring. Also, this project aims to serve as an example of the technological advances made so far, analyzing the challenges to be overcome and provides an approach for future trends.  The presented results aim to serve as a source of information for healthcare/fitness enthusiast, technology specialists, and the general population to improve the Internet of Health Things. The vision for this project was to design and develop a device that could serve as a central data relay server for wearable sensors. The device was intended to be a low-power, and low-cost alternative to keep users informed for aid in remote health monitoring. The project is called FitHub.

# FitHub - Heart Rate Moinitor
Wearable devices can monitor and record real-time information about one’s physiological condition and motion activities. These wearable sensors can measure physiological signs such as heart rate, body temperature and motion detection. Continuous monitoring of physiological signals could help to detect and diagnose several cardiovascular, neurological, and pulmonary diseases at their early onset. The wearable health monitoring systems are usually equipped with a variety of electronic sensors, actuators, wireless communication modules and signal processing units.  The measurements obtained by the sensors connected in a wireless Body Sensor Network, are transmitted to a nearby processing node using a suitable communication protocol, preferably a low-power and short-range wireless medium, for example, Bluetooth. The processing node, which could be a smartphone, computer, again for this project the node gateway will be the raspberry pi, which will also run advanced processing, analysis, and decision algorithms and may also store and display the results to the user by communicating with the cloud Azure IoT hub. It transmits the measured data over the internet to the healthcare personnel, thus functioning as the gateway to remote healthcare facilities.
## Abstract
Wearable devices can monitor and record real-time information about one’s physiological condition and motion activities. These wearable sensors can measure physiological signs such as heart rate, body temperature and motion detection. Continuous monitoring of physiological signals could help to detect and diagnose several cardiovascular, neurological, and pulmonary diseases at their early onset. The wearable health monitoring systems are usually equipped with a variety of electronic sensors, actuators, wireless communication modules and signal processing units.  The measurements obtained by the sensors connected in a wireless Body Sensor Network, are transmitted to a nearby processing node using a suitable communication protocol, preferably a low-power and short-range wireless medium, for example, Bluetooth. The processing node, which could be a smartphone, computer, again for this project the node gateway will be the raspberry pi, which will also run advanced processing, analysis, and decision algorithms and may also store and display the results to the user by communicating with the cloud Azure IoT hub. It transmits the measured data over the internet to the healthcare personnel, thus functioning as the gateway to remote healthcare facilities.


## Hardware Requirements
Raspberry Pi, 8gb MicroSD, Breadboard & Jumper Cables, Any Optical Heart-Rate Sensor

## Basic Hardware Setup 
*Note LEDS are not connected
![Example Figure](https://photos.google.com/u/1/photo/AF1QipOVMqtamhDdvKR4Jrwgt2dzza1e8tPZ3plCBRk)



## User-Level Requirements
The intended device is meant to be low-cost, low-powered, the device should be easy-to-use and user friendly. Users should be able to view their inormation on the Azure web application.

### Code Example 
This is code that acts as a heart rate analyzer (rather than a monitor). It can determine heartbeats based on two different algorithms: Thresholding and Wavelet transform + Thresholding. I've found the Wavelet method to work the best. The goal here was for anyone to write their own detection method and be able to use it with the `HeartRateMonitor` class.

```python
from detection_algorithm import Wavelet
from heart_rate_monitor import HeartRateMonitor

def main():
    # if you wanted to specify a width for mean hr,
    # use the time_interval kwarg. e.g. time_interval=(.13, .16)
    # The Wavelet analyzer can be swapped with Threshold
    heart_rate_monitor = HeartRateMonitor(
        filename="tests/test_data/test_data1.csv",
        analyzer=Wavelet)

    if heart_rate_monitor is None:
        return

    # if you do not wish to write the heart rate properties, use to_json()
    metrics = heart_rate_monitor.to_json()
    heart_rate_monitor.write_json()

if __name__ == "__main__":
    main()
```


## Plotting
If you wish to get a plot of the analysis, use the `plot_graph` method on the analyzer e.g. `heart_rate_monitor.analyzer.plot_graph()`.

### Example
Using `heart_rate_monitor.analyzer.plot_graph()` on a Wavelet analyzer would give you a plot similar to the one below.
![Example Figure](https://i.imgur.com/vvmEqRl.png)

