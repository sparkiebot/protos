# Sparkie Protocol Buffer Definitions

This repository contains Protocol Buffer (protobuf) message definitions for Sparkie's embedded board communication system. These `.proto` files define the structured data format used for communication between different components of the Sparkie robotics platform.

## Overview

The protocol definitions are organized into modular files, each handling specific sensor data or control commands:

### Core Files
- **`base.proto`** - Main message wrapper and communication protocol
- **`imu.proto`** - Inertial Measurement Unit (IMU) data (accelerometer, gyroscope, magnetometer)
- **`motors.proto`** - Motor control commands and status feedback
- **`servo.proto`** - Servo motor angle control
- **`ultrasonic.proto`** - Ultrasonic distance sensor data
- **`ledstrip.proto`** - LED strip control and effects
- **`aht.proto`** - AHT temperature and humidity sensor data
- **`airq.proto`** - Air quality sensor data (eCO2 and TVOC)

### Message Structure

The main communication is handled through the `Message` structure in `base.proto`, which uses a `oneof` field to contain different types of sensor data or commands. Messages are wrapped in `MessagePacket` containers that can hold multiple messages for efficient batch communication.

### Key Features

- **Unified Communication Protocol**: All sensor data and commands use the same message wrapper with topic IDs and timestamps
- **Ping-Pong Mechanism**: Built-in connectivity testing and latency measurement
- **Modular Design**: Each sensor/actuator type has its own dedicated proto file
- **Timestamped Messages**: All messages include timestamp information for synchronization

## Requirements

**This implementation requires [nanopb](https://github.com/nanopb/nanopb)** - a lightweight Protocol Buffers implementation designed for embedded systems with limited resources.

## Supported Hardware

These protocol definitions are specifically designed for Sparkie's embedded board and support the following sensors and actuators:

- IMU sensors (3-axis accelerometer, gyroscope, magnetometer)
- Ultrasonic distance sensors
- AHT temperature/humidity sensors
- Air quality sensors (eCO2/TVOC)
- Motor control systems with encoder feedback
- Servo motors
- LED strip controllers