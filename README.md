# STM32-PWM-LED-Control-Using-Timers
PWM-based LED brightness control using STM32F446RE and TIM2 timer. Developed with STM32CubeMX and STM32CubeIDE to demonstrate PWM signal generation and duty cycle variation on embedded systems.

## Overview

This project implements PWM on the STM32F446RE microcontroller using the TIM2 timer.  
By continuously varying the duty cycle, the onboard LED brightness changes gradually from low to high intensity and back.

The project was developed using:

- STM32CubeMX
- STM32CubeIDE
- STM32 HAL Library

---

## Features

- PWM signal generation using TIM2
- LED brightness control through duty cycle variation
- Smooth fade-in and fade-out effect
- STM32 HAL-based implementation
- CubeMX peripheral configuration

---

## Hardware Requirements

- STM32 Nucleo-F446RE Development Board
- USB Type-A to Mini-B Cable

---

## Software Requirements

- STM32CubeIDE
- STM32CubeMX

---

## PWM Configuration

| Parameter | Value |
|------------|--------|
| Timer | TIM2 |
| PWM Channel | TIM2_CH1 |
| Prescaler (PSC) | 839 |
| Auto Reload Register (ARR) | 1000 |
| PWM Frequency | 100 Hz |
| Counter Mode | Up |

---

## Working Principle

Pulse Width Modulation (PWM) controls the average voltage delivered to the LED by adjusting the duty cycle of the signal.

### Duty Cycle Formula

```text
Duty Cycle (%) = (CCR / ARR) × 100
```

- Lower duty cycle → Dim LED
- Higher duty cycle → Bright LED

The program continuously updates the CCR value to generate the LED fading effect.

---

## Source Code

```c
HAL_TIM_PWM_Start(&htim2, TIM_CHANNEL_1);

while (1)
{
    int x;

    for(x = 0; x < 1000; x++)
    {
        __HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_1, x);
        HAL_Delay(1);
    }

    for(x = 1000; x > 0; x--)
    {
        __HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_1, x);
        HAL_Delay(1);
    }
}
```

---

## Build and Run

1. Open the project in STM32CubeIDE
2. Connect the STM32 board using USB
3. Build the project
4. Flash the firmware to the board
5. Run the program and observe the LED fading effect

---

## Expected Output

The onboard LED will:

- Gradually increase in brightness
- Reach maximum intensity
- Gradually decrease in brightness
- Repeat continuously

---

## Learning Outcomes

- Understanding STM32 timer peripherals
- PWM signal generation
- Duty cycle control
- STM32 HAL programming
- Embedded systems development workflow

---

## Author

**Ayush Jangra**  
ECE Student | Chitkara University
