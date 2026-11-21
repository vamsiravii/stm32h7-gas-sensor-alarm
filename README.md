# Analog Gas Sensor Alarm on STM32H723

A small STM32 project that reads an analog gas sensor and switches an LED on when the reading crosses a threshold.

## What it does

- **ADC1, channel 10 (pin PC0)** reads the sensor's analog output in continuous mode at 12-bit resolution (values 0 to 4095).
- Every 500 ms the main loop reads the latest value.
- If the reading is above **2000**, the LED on **PB0** turns on. Otherwise it turns off.

The latest reading is kept in the global variable `gas`, so you can watch it in STM32CubeIDE's *Live Expressions* during a debug session.

## Hardware and tools

- MCU: STM32H723ZG
- Sensor: any gas sensor with an analog voltage output, connected to PC0 (within the ADC's input range)
- LED: on PB0
- Toolchain: STM32CubeIDE (`gas sensor.ioc` holds the CubeMX configuration)

## Notes

- The threshold of 2000 is a fixed constant in `Core/Src/main.c`. It is not calibrated to a particular gas or concentration.
- This is a simple threshold demo, not a calibrated measurement or a safety device.
