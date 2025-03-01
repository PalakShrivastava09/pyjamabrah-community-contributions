---
# Change the Date below
date: "2025-03-01"

# Add the title of the Post here
title: "Call by Value vs. Call by Reference – Explained Simply"

# replace the "sample/cover.png" with path to a 16:9 image
# this image will be shown in SEO optimization and when
# you share the post on social media.
thumbnail: "/posts/call_by_value_call_by_reference/CallByValueCallByReferenceCover.PNG"

# Add your GitHub handle here
author: "PalakShrivastava09"

# Add tags as suitable for the topic
tags:
  - "C"
  - "Call by value"
  - "Call by reference"
  - "Programming"

# If it fits a certain category of topics, add that
categories:
  - "Programming"
  - "C"

# If this is a Series of posts, Add the name of the series
series:
  - ""
---

Understanding fundamental programming concepts is crucial for writing efficient and bug-free code. In this article, we’ll explore Call by Value and Call by Reference with relatable examples, real-world embedded system use cases, and key differences to help you apply them effectively.


# 📖 The Story of Notes Sharing
Imagine you and your friend are preparing for an exam:

**Call by Value** 📄 → You photocopy your notes and give them to your friend. If you update your original notes, your friend’s copy remains unchanged.

**Call by Reference** 🔗 → You create notes in Google Docs and share the link. If you edit the document, your friend sees the changes instantly.

This is the key difference between **Call by Value** and **Call by Reference** in programming.

## 💻 What Happens in Code?
In programming, functions can receive data in two ways:

**1 ⃣ Call by Value – "Making Copies"**

A function gets `a copy` of the variable. Any changes inside the function `don’t affect the original`.

```c
#include <stdio.h>

void changeValue(int num) {
    num = 10; // Changing the copy
}

int main() {
    int a = 5;
    changeValue(a);
    printf("Value of a: %d\n", a); // Still 5
    return 0;
}
```
🔹 `Pros`:
✔ Safe (original data remains unchanged)✔ No accidental modifications

🔸 `Cons`:❌ Uses more memory (extra copies)❌ Slower for large data structures

📌 `Use Case`: When you want to `keep data safe`, like sending configuration settings without modifying the original.

**2️⃣ Call by Reference – "Sharing the Same Data"**

A function gets the `memory address` of a variable. Any changes inside the function `affect the original`.

```c
#include <stdio.h>

void changeValue(int *num) {
    *num = 10; // Modifying the original value
}

int main() {
    int a = 5;
    changeValue(&a);
    printf("Value of a: %d\n", a); // Now it's 10
    return 0;
}
```
🔹 `Pros`:✔ Memory efficient (no extra copies)✔ Faster (especially for large data)

🔸 `Cons`:❌ Risky (changes can be accidental)❌ Harder to debug

📌 `Use Case`: When modifying large structures (like `sensor data` in embedded systems) or updating values directly (e.g., `hardware registers`).

##📊 Key Differences at a Glance

| `Feature` | `Call by value` | `Call by reference` |
|:-|:-|:-|
|`Memory Usage` | Large, active | None (Fully Open-Source) |
|`Performance`  | Niche (ISP-focused) | Comcast, Charter, etc. |
|`Data Safety`  | Growing | Backed by prpl Foundation |
|`Best For`  | Growing | Backed by prpl Foundation |

##🏭 Real-World Embedded System Examples

**1️⃣ Reading Sensor Data**
Imagine you have a `temperature sensor` connected to your microcontroller:

```c
#include <stdio.h>

// Declare getSensorData() before use
float getSensorData();  

void readTemperature(float *temp) {
    *temp = getSensorData(); // Directly updating the original variable
}

// Define getSensorData()
float getSensorData() {
    return 25.5; // Simulated sensor data
}

int main() {
    float temperature;
    readTemperature(&temperature);
    printf("Current Temperature: %.2f°C\n", temperature);
    return 0;
}
```

📌 `Why Call by Reference?` The function updates the variable `directly`, avoiding extra copies and ensuring real-time sensor data is available.

**2️⃣ Updating Motor Speed in an Embedded System**
A `motor controller` needs to adjust its speed dynamically based on sensor input:

```c
#include <stdio.h>

void updateMotorSpeed(int *speed) {
    *speed += 10; // Increase speed by 10
}

int main() {
    int motorSpeed = 50;
    updateMotorSpeed(&motorSpeed);
    printf("Updated Motor Speed: %d\n", motorSpeed); // Now it's 60
    return 0;
}
```

📌 `Why Call by Reference?` Directly modifying the motor speed ensures the controller is always working with the latest value without unnecessary copies.

##🎯 When to Use What?

✔ `Call by Value` → Use for small values like int, char, and constants. (e.g., sending a fixed baud rate to UART)
✔ `Call by Reference` → Use for large structs, `modifying hardware registers`, or real-time updates.

##🎉 Conclusion

Both methods are important in software development. `Call by Value` keeps data safe, while `Call by Reference` improves efficiency. Understanding their differences helps you `write optimized and bug-free code`. 🚀

Next time you share your notes, remember – you're either `copying` (Call by Value) or `sharing a link` (Call by Reference)!