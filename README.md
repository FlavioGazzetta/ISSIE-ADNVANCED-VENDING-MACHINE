# Advanced ISSIE Vending Machine Project

This project demonstrates the design and implementation of an advanced vending machine using **ISSIE**, a digital circuit simulator. The project builds on basic vending machine principles, integrating custom logic circuits, state machines, and synchronous ROM to handle real-world vending scenarios like balance tracking, price fetching, and change return.

---

## **Project Overview**

The vending machine is designed to:
- Track inserted coins and calculate the balance.
- Fetch prices from a synchronous ROM.
- Match the balance with the price using comparator circuits.
- Provide accurate change when the balance exceeds the price.
- Integrate LED indicators and motor control for user feedback.

---

## **Key Features and Components**

### 1. **System Flowchart**
The flowchart outlines the logical flow of the vending machine, from coin insertion to item dispensing and change calculation.

<img src="Images/Vending_flow_chart.png" alt="System Flowchart" width="300">

---

### 2. **State Machine**
The machine operates using a Moore model with four primary states:
- **Idle State:** Awaiting user input.
- **Coin Input State:** Accepts coins and updates the balance.
- **Selection State:** Matches balance to price.
- **Vending State:** Dispenses the item and calculates the remainder.

<img src="Images/Vending_state.png" alt="State Machine Diagram" width="300">

---

### 3. **System Hierarchy**
This diagram shows the hierarchical structure of the vending machine, including ROM, comparator, remainder logic, and state transitions.

<img src="Images/Vending_Hirearchy.png" alt="System Hierarchy" width="300">

---

### 4. **Adder Circuit**
Used to calculate the total balance by summing the previous balance with the value of the inserted coin.

<img src="Images/Vending_amount.png" alt="Adder Circuit" width="300">

---

### 5. **Subtraction Logic**
This circuit computes the remainder (change) when the balance exceeds the price of the selected item.

<img src="Images/Vending_addsub.png" alt="Subtraction Logic" width="300">

---

### 6. **XOR Logic**
The XOR logic facilitates comparison between inputs, such as balance and price, by evaluating bitwise differences.

<img src="Images/Vending_axorb.png" alt="XOR Logic" width="300">

---

### 7. **Challenge Implementation**
The integration of subsystems into the vending machine to meet the project's specific challenges and objectives.

<img src="Images/Vending_Challenge.png" alt="Challenge Implementation" width="300">

---

### 8. **Coin Input Circuit**
Manages the input of coins and updates the balance dynamically.

<img src="Images/Vending_cinv.png" alt="Coin Input Circuit" width="300">

---

### 9. **Comparator Logic**
Determines whether the balance is greater than, less than, or equal to the price.

<img src="Images/Vending_Comparator.png" alt="Comparator Logic" width="300">

---

### 10. **Full Adder Logic**
The full adder facilitates bitwise addition within the balance tracking system.

<img src="Images/Vending_fa.png" alt="Full Adder Logic" width="300">

---

### 11. **4-Bit Full Adder**
This circuit is an expanded version of the full adder, used for 4-bit operations within the system.

<img src="Images/Vending_fa4.png" alt="4-Bit Full Adder" width="300">

---

### 12. **Price Selection Circuit**
The ROM price selector fetches prices for items based on the user's selection.

<img src="Images/Vending_ROM_price_selector.png" alt="Price Selection Circuit" width="300">

---

### 13. **ROM Content**
This table represents the contents of the ROM, mapping item numbers to their prices.

<img src="Images/Vending_ROM_content.png" alt="ROM Content" width="300">

---

### 14. **Remainder Logic**
Calculates the remainder to be returned as change after a transaction.

<img src="Images/Vending_Remainder.png" alt="Remainder Logic" width="300">

---

### 15. **Output Control**
Manages outputs such as LEDs (`LEDC` and `LEDS`) and the motor (`M`) for item dispensing.

<img src="Images/Vending_Output.png" alt="Output Control" width="300">

---

### 16. **Right Balance Logic**
Ensures the balance and price are matched accurately during transactions.

<img src="Images/Vending_Right_Balance.png" alt="Right Balance Logic" width="300">

---

### 17. **High-Level Right Balance Logic**
A high-level integration of the balance logic with comparator and remainder circuits.

<img src="Images/Vending_Right_Balance_ro.png" alt="High-Level Right Balance Logic" width="300">

---

### 18. **Next State Logic**
Handles state transitions based on current inputs, ensuring smooth progression through the machine's operation.

<img src="Images/Vending_nxt.png" alt="Next State Logic" width="300">

---

### 19. **Advanced Combined System**
An integrated view of all components, including coin input, ROM price fetching, and balance management.

<img src="Images/Advanced_Vending_Combined.png" alt="Advanced Combined System" width="300">

---

### 20. **Flow Node N1**
Represents a specific logic node within the vending machine's operation.

<img src="Images/Vending_n1.png" alt="Flow Node N1" width="300">

---

### 21. **Flow Node N2**
Another logic node highlighting interactions within the vending process.

<img src="Images/Vending_n2.png" alt="Flow Node N2" width="300">

---

### 22. **System Hierarchy Overview**
A complete hierarchical view of the vending machine system, showing all modules and subsystems.

<img src="Images/Vending_ha.png" alt="System Hierarchy Overview" width="300">

---

### 23. **Project Overview Chart**
A high-level chart summarizing the system's operation from start to finish.

<img src="Images/Vending_Hirearchy.png" alt="Project Overview Chart" width="300">

---

## **Repository Structure**

