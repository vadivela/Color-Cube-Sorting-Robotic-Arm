# Color-Cube Sorting System with Robotic Arm

This project demonstrates an autonomous color-cube sorting system, featuring a 4DOF robotic arm synchronized with a conveyor belt. Aided by a color detection module and robust processing unit, the system efficiently classifies and sorts cubes based on their color in real-time.

<p align="center">
  <a href="https://youtu.be/x4tu3nL01OI?si=GthjDjz5y5HyYdao" target="_blank">
    <img src="Demo.gif" alt="Sorting Process Visualization" width="600"/>
  </a>
</p>

## Key Features
- **Automated Sorting**: Combines sensors and actuators for efficient sorting.
- **Real-Time Classification**: Uses a trained neural network for accurate color detection.
- **Scalable Design**: Can adapt to different cube sizes and color categories.
- **Multiprocessing Capabilities**: Parallel operations using a Propeller-based system.

## Hardware Components
- **NEMA 17 Stepper Motor**: Drives the conveyor belt with precise control.
- **A4988 Stepper Driver**: Ensures smooth stepper operation.
- **TCS34725 Color Sensor**: Delivers consistent and reliable color readings.
- **MG996R Servo Motors**: Powers the robotic arm joints for flexibility.
- **HC-SR04 Ultrasonic Module**: Detects cubes approaching the robotic arm.
- **Propeller Activity Board**: Orchestrates control logic and multiprocessing.
- **12V DC Power Supply**: Provides stable power to all components.

## System Workflow
1. **Cube Detection**: The ultrasonic sensor identifies the presence of cubes at the conveyor's end.
2. **Color Identification**: The color sensor captures RGB data, processed through a trained neural network for classification.
3. **Conveyor Control**: Halts when a cube reaches the pickup point.
4. **Sorting Mechanism**: The robotic arm picks and places cubes into respective bins based on color.
5. **Continuous Tracking**: A cog monitors conveyor movement, ensuring seamless operation and preventing overlaps.

## Neural Network for Color Classification
The RGB outputs from the color sensor are fed into a lightweight neural network trained using TensorFlow. The network comprises:
- **Input Layer**: Accepts normalized RGB values.
- **Hidden Layer**: Processes the data to identify patterns.
- **Output Layer**: Outputs probabilities for each cube type (Red, Green, Blue, or No Cube).

To reduce computational load, the trained model is implemented directly on the Propeller board, using softmax regression for real-time predictions.

## Parallel Processing with Propeller
The Propeller board enables multitasking by dedicating individual cogs for specific operations:
- **Cog 0**: System initialization and coordination.
- **Cog 1**: Ultrasonic sensor data acquisition.
- **Cog 2**: Color sensor processing and classification.
- **Cog 3**: Robotic arm control for sorting.
- **Cog 4**: Conveyor belt control.
- **Cog 5**: Monitoring conveyor travel distance.

## Enhancements for Precision
- **Controlled Lighting**: A shield around the sensor minimizes ambient light interference.
- **Mode Filtering**: Ensures stable classification by analyzing multiple consecutive outputs.
- **Cube Gap Management**: Tracks conveyor distance to detect closely spaced cubes of the same color.

## Results
The system demonstrated high accuracy and reliability during testing, achieving near-perfect sorting of cubes across varied scenarios. It highlights potential for industrial applications requiring efficient object sorting.
