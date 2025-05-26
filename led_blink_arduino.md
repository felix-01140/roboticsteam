# Simple Arduino LED Blink Program

Here’s a simple Arduino code to make an LED blink on and off at 1-second intervals. This is often the first program people write when learning Arduino.

---

### 🧠 **What It Does**

The code turns an LED on for one second, then off for one second, and repeats this forever.

---

### ✅ **What You Need**

* An Arduino board (like UNO)
* An LED
* A 220-ohm resistor
* Breadboard and jumper wires  
  *(Or you can use the built-in LED on pin 13 of most Arduino boards)*

---

### 💡 **Circuit Setup**

* **Long leg (anode)** of the LED to **digital pin 13**
* **Short leg (cathode)** to **GND** through a 220-ohm resistor  
  *(If using the built-in LED, no wiring is needed)*

---

### 🧾 **Arduino Code**

```cpp
// Set the pin number for the LED
int ledPin = 13; // Most Arduino boards have a built-in LED on pin 13

void setup() {
  // Set the LED pin as an output
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Turn the LED on (HIGH voltage)
  digitalWrite(ledPin, HIGH);
  delay(1000); // Wait for 1000 milliseconds (1 second)

  // Turn the LED off (LOW voltage)
  digitalWrite(ledPin, LOW);
  delay(1000); // Wait for 1000 milliseconds (1 second)
}
```

---

### 🧪 **How It Works**

* `setup()` runs once when the Arduino is powered or reset.
* `loop()` runs over and over.
* `digitalWrite(ledPin, HIGH)` sends power to the pin to turn the LED on.
* `delay(1000)` waits for 1 second.
* `digitalWrite(ledPin, LOW)` turns the LED off.
* `delay(1000)` waits again before repeating.

