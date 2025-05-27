# 🗑️ Smart Bin Using Arduino

Welcome to the **Smart Bin Project!**  
This smart dustbin opens its lid automatically when you bring your hand close and tells you how full the bin is using colored lights.

---

## 🎯 Project Goal

To build a bin that:
- **Opens the lid** when someone comes close (hands-free).
- **Shows how full the bin is** using Red, Yellow, and Green LEDs.

This project helps promote hygiene and smart living!

---

## 🧰 Materials Needed

| Item | Quantity | Purpose |
|------|----------|---------|
| Arduino Uno or Nano | 1 | The brain of the project |
| Ultrasonic Sensor (HC-SR04) | 2 | Detects hand and trash level |
| Servo Motor (SG90) | 1 | Opens and closes the lid |
| Breadboard | 1 | Easy wiring |
| Jumper Wires | Several | Connect components |
| LEDs (Red, Yellow, Green) | 1 each | Show bin level |
| Resistors (220Ω) | 3 | Protect LEDs |
| Buzzer (Optional) | 1 | Beeps when bin is full |
| 9V Battery with connector or USB | 1 | Powers the Arduino |
| Plastic bin with lid | 1 | The actual trash can |
| Cardboard or Sticks | Some | Helps mount parts |

---

## 🔌 Wiring Instructions

**Ultrasonic Sensor 1 (Hand Detection)**  
- VCC → 5V  
- GND → GND  
- TRIG → D9  
- ECHO → D8  

**Ultrasonic Sensor 2 (Bin Level)**  
- VCC → 5V  
- GND → GND  
- TRIG → D7  
- ECHO → D6  

**Servo Motor**  
- VCC → 5V  
- GND → GND  
- Signal → D3  

**LEDs**  
- Red → D10  
- Yellow → D11  
- Green → D12  
- Connect through resistors to GND

**Buzzer (Optional)**  
- + → D4  
- - → GND

---

## 🧠 How It Works

1. **Hand Detected** → Lid opens using a servo motor.
2. **Trash Level Detected**:
   - **Green LED**: Bin is empty  
   - **Yellow LED**: Bin is half full  
   - **Red LED**: Bin is full  
   - Optional: Buzzer beeps if full.

---

## 📟 Code

The code is written in Arduino C++ and uses the `Servo.h` library.  
You can upload it using the Arduino IDE.

> ⚠️ Don't forget to install the Servo library if not already available!
> 

### 🧾 **Arduino Code**

```cpp
#include <Servo.h>

Servo lidServo;

const int trigPinHand = 9;
const int echoPinHand = 8;

const int trigPinLevel = 7;
const int echoPinLevel = 6;

const int redLED = 10;
const int yellowLED = 11;
const int greenLED = 12;

long duration, distance;

void setup() {
  Serial.begin(9600);
  lidServo.attach(3);
  pinMode(trigPinHand, OUTPUT);
  pinMode(echoPinHand, INPUT);
  pinMode(trigPinLevel, OUTPUT);
  pinMode(echoPinLevel, INPUT);
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}

void loop() {
  // Hand detection
  digitalWrite(trigPinHand, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPinHand, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPinHand, LOW);
  duration = pulseIn(echoPinHand, HIGH);
  distance = duration * 0.034 / 2;

  if (distance < 15) {
    lidServo.write(90); // Open
    delay(3000);
    lidServo.write(0); // Close
  }

  // Bin level check
  digitalWrite(trigPinLevel, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPinLevel, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPinLevel, LOW);
  duration = pulseIn(echoPinLevel, HIGH);
  distance = duration * 0.034 / 2;

  if (distance < 5) {
    digitalWrite(redLED, HIGH);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, LOW);
  } else if (distance >= 5 && distance < 15) {
    digitalWrite(redLED, LOW);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(greenLED, LOW);
  } else {
    digitalWrite(redLED, LOW);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, HIGH);
  }

  delay(500);
}

```

---

### 🧪 **How It Works**

---

## 🧾 Presentation Ideas

- Show how it opens automatically.
- Show how it uses lights to show the bin's level.
- Explain how smart bins help cities and homes stay clean.

---

## 📷 Images and Diagrams

photos or wiring diagrams to help others build it easily.

---![2f07f589-4912-448a-b13f-5a69ca1cb567](https://github.com/user-attachments/assets/0bb085c2-01c1-4780-9588-a7f6be36eb85)


## 🙋 Made by Students

This is a simple school project at FHA built by kids using Arduino to make smart and useful technology.

---

## 📃 License

This project is free to use and modify for educational purposes.

