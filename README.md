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

## **System Flowchart**
The flowchart outlines the logical flow of the vending machine, from coin insertion to item dispensing and change calculation.

<img src="Images/Vending_flow_chart.png" alt="System Flowchart" width="300">

---

## **System Hierarchy**
The hierarchy diagram provides an overview of the vending machine's modular design, including ROM, comparator, remainder logic, and state transitions.

<img src="Images/Vending_Hirearchy.png" alt="System Hierarchy" width="300">

---

## **Subsystems Explanation**
The following sections explain the design and function of each subsystem, starting from the bottom of the hierarchy and moving to the top.

---

### 1. **Coin Input and Balance Tracking**
At the base of the hierarchy, the system handles coin input and balance updates:
- The **Coin Input Circuit** manages the input of coins and dynamically updates the balance.
- The **Adder Circuit** calculates the total balance by summing the previous balance and the inserted coin value.

#### Coin Input Circuit:
<img src="Images/Vending_cinv.png" alt="Coin Input Circuit" width="300">

#### Adder Circuit:
<img src="Images/Vending_amount.png" alt="Adder Circuit" width="300">

---

### 2. **Price Selection**
The price selection system retrieves the price of the selected item from a ROM. This system ensures that the correct price is displayed for the item being purchased.

#### ROM Price Selector:
<img src="Images/Vending_ROM_price_selector.png" alt="ROM Price Selector" width="300">

#### ROM Content Table:
<img src="Images/Vending_ROM_content.png" alt="ROM Content Table" width="300">

---

### 3. **Comparator Logic**
The comparator determines if the balance matches or exceeds the selected item's price. This is essential for ensuring that items can only be dispensed when the required amount has been inserted.

#### XOR Logic for Comparison:
<img src="Images/Vending_axorb.png" alt="XOR Logic" width="300">

#### Comparator Logic:
<img src="Images/Vending_Comparator.png" alt="Comparator Logic" width="300">

---

### 4. **Remainder Calculation**
If the inserted balance exceeds the price of the selected item, the remainder logic calculates the amount to be returned as change.

#### Remainder Logic:
<img src="Images/Vending_Remainder.png" alt="Remainder Logic" width="300">

---

### 5. **Output Control**
The output control system manages feedback to the user, including:
- **LEDC:** Indicates when coins are required.
- **LEDS:** Signals item selection.
- **Motor Control:** Activates to dispense the selected item.

#### Output Control:
<img src="Images/Vending_Output.png" alt="Output Control" width="300">

---

### 6. **Full Adder and Advanced Logic**
The system incorporates advanced 4-bit logic for handling binary operations:
- **Full Adder Logic:** Facilitates bitwise addition for balance updates.
- **4-Bit Full Adder:** Supports multi-bit operations required in the vending machine.

#### Full Adder Logic:
<img src="Images/Vending_fa.png" alt="Full Adder Logic" width="300">

#### 4-Bit Full Adder:
<img src="Images/Vending_fa4.png" alt="4-Bit Full Adder" width="300">

---

### 7. **Next State Logic**
The next-state logic coordinates transitions between the vending machine's states:
- **Idle State**
- **Coin Input State**
- **Selection State**
- **Vending State**

#### Next State Logic:
<img src="Images/Vending_nxt.png" alt="Next State Logic" width="300">

---

### 8. **High-Level Integration**
The high-level logic combines the balance tracker, comparator, and output control into a unified system:
- **Right Balance Logic** ensures that the balance matches the item's price.
- **Advanced Combined System** integrates all subsystems into the final vending machine.

#### High-Level Right Balance Logic:
<img src="Images/Vending_Right_Balance_ro.png" alt="High-Level Right Balance Logic" width="300">

#### Advanced Combined System:
<img src="Images/Advanced_Vending_Combined.png" alt="Advanced Combined System" width="300">

---

### 9. **Specific Logic Nodes**
Certain logic nodes represent specific subsystems or decisions within the vending machine's operation:
- **Node N1:** Represents a critical decision in balance checking.
- **Node N2:** Handles state-based transitions for dispensing.

#### Node N1:
<img src="Images/Vending_n1.png" alt="Node N1" width="300">

#### Node N2:
<img src="Images/Vending_n2.png" alt="Node N2" width="300">

---

### 10. **Final System Overview**
The final hierarchical structure of the vending machine integrates all systems into a cohesive and functional design.

#### System Hierarchy Overview:
<img src="Images/Vending_ha.png" alt="System Hierarchy Overview" width="300">

---

## **Repository Structure**

