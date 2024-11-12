# Advanced ISSIE Vending Machine Project

This project represents a highly functional digital vending machine designed and implemented using **ISSIE**, a digital circuit simulator. It extends the basic vending machine functionality by integrating advanced features like price management, balance tracking, change calculation, and user feedback through LEDs. The design is implemented with state machines, custom logic circuits, and synchronous ROM for item price handling.

---

## **Project Overview**

The vending machine is designed to:
- Track inserted coins and calculate the current balance.
- Match the balance with the item's price using custom comparator circuits.
- Provide the correct remainder if the balance exceeds the price.
- Update user feedback indicators (LEDS, LEDC, and motor activation).
- Support dynamic item selection and handle transactions efficiently.

---

## **Features and Components**

### 1. **State Machine**
The vending machine operates using a **4-state Moore machine**:
- **Idle State:** No coin inserted, no item selected.
- **Coin Input State:** Accepts coins and updates the balance.
- **Item Selection State:** Matches the inserted balance with the selected item's price.
- **Vending State:** Dispenses the item and calculates any remainder.

<img src="Images/Vending_state.png" alt="State Machine Diagram" width="300">

---

### 2. **Synchronous ROM for Item Prices**
The ROM stores predefined prices for items indexed by their selection number. If no item is selected (item = 0), the price remains 0.

- **Inputs:** Item selection number.
- **Outputs:** Corresponding item price.

<img src="Images/Vending_ROM_price_selector.png" alt="ROM Price Selector" width="300">  
<img src="Images/Vending_ROM_content.png" alt="ROM Content Table" width="300">

---

### 3. **Balance Tracker**
The balance tracker accumulates the total coin values inserted by the user. It uses registers and an adder circuit to compute the total balance dynamically.

<img src="Images/Vending_amount.png" alt="Balance Tracker Circuit" width="300">

---

### 4. **Comparator and Same Value Check**
- **Comparator Circuit:** Checks if the balance matches or exceeds the price of the selected item.
- **Same-Value Check Circuit:** Ensures correctness during balance and price comparison.

<img src="Images/Vending_Same_Value_Check.png" alt="Comparator Circuit" width="300">

---

### 5. **Remainder Calculation**
The remainder logic calculates the difference when the balance exceeds the price. It ensures the correct change is returned to the user.

<img src="Images/Vending_Remainder.png" alt="Remainder Logic Circuit" width="300">

---

### 6. **Arithmetic Logic Unit (Add/Subtract Circuit)**
A custom ALU handles addition and subtraction for balance and remainder calculations.

<img src="Images/Vending_addsub.png" alt="Add/Subtract Logic" width="300">

---

### 7. **Output Control**
This subsystem controls the outputs of the vending machine, such as:
- **LEDC (Insert Coins):** Indicates when coins are required.
- **LEDS (Select Item):** Lights up when an item is selected.
- **Motor (M):** Activates during item dispensing.

<img src="Images/Vending_Output.png" alt="Output Control Logic" width="300">

---

### 8. **Price Comparator Integration**
The price comparator circuit ensures that the vending machine can compare the price of the selected item with the user's inserted balance.

<img src="Images/Vending_Right_Balance.png" alt="Price Comparator Circuit" width="300">

---

### 9. **Full Vending Machine Hierarchy**
This image represents the complete integration of all subsystems into the vending machine hierarchy. It combines:
- Price fetching and balance comparison.
- Change calculation and feedback signals.
- User interaction indicators.

<img src="Images/Vending_ha.png" alt="Vending Machine Hierarchy" width="300">

---

### 10. **Next State Logic**
The state machine's next-state logic transitions between idle, coin insertion, item selection, and vending. This logic ensures proper synchronization and state management.

<img src="Images/Vending_nxt.png" alt="Next State Logic" width="300">

---

### 11. **Advanced Combined System**
This image showcases the final integration of all features, including coin value input, item selection, balance matching, and change calculation.

<img src="Images/Advanced_Vending_Combined.png" alt="Advanced Combined System" width="300">

---

## **Simulation and Testing**

### Example Test Flow:
1. **Item Selection:** Choose an item using the `Food_Select` input (e.g., price = 5).
2. **Coin Insertion:** Input coins using `Coin_Value` (e.g., insert 3, then 2).
3. **Match Check:** The comparator circuit activates when the balance matches or exceeds the price.
4. **Dispense Item:** The motor activates, dispensing the item, and any remainder is returned.

### Example Outputs:
- **LEDS:** Lights up when an item is selected.
- **LEDC:** Indicates when coins are required.
- **Motor (M):** Activates during item dispensing.
- **Remainder:** Displays the change to be returned.

<img src="Images/Vending_Output.png" alt="Example Simulation Output" width="300">

---

### 12. **Adder Circuit**
This diagram shows the adder circuit used for calculating the total balance of coins inserted. It takes the previous balance (`VALUE_BEFORE`) and the current coin value (`VALUE_CURRENT`) as inputs and produces the updated balance.

<img src="Images/Vending_amount.png" alt="Adder Circuit" width="300">

---

### 13. **Subtraction Logic**
The subtraction circuit is part of the remainder logic, ensuring that the vending machine can compute the difference between the inserted balance and the price of the selected item.

<img src="Images/Vending_addsub.png" alt="Subtraction Logic" width="300">

---

### 14. **Hierarchy of Remainder Logic**
This image integrates the balance, price, and remainder calculations into a cohesive subsystem. It ensures the correct remainder is calculated and outputs the value to the `GIVE_BACK` signal.

<img src="Images/Vending_Remainder.png" alt="Remainder Hierarchy" width="300">

---

### 15. **Price Selector**
This circuit fetches the price of an item from the synchronous ROM based on the `VALUE_SELECTION` input. The price is then used for comparison with the current balance.

<img src="Images/Vending_ROM_price_selector.png" alt="Price Selector" width="300">

---

### 16. **State Transition Diagram**
This diagram shows the logic for transitioning between states based on inputs such as `C` (Coin Input), `S` (Selection), and other control signals. It ensures the vending machine operates correctly at each stage of a transaction.

<img src="Images/Vending_nxt.png" alt="State Transition Logic" width="300">

---

### 17. **Same Value Check**
The same-value check circuit validates whether two inputs (balance and price) are equal. This is essential for determining if the vending machine is ready to dispense an item.

<img src="Images/Vending_Same_Value_Check.png" alt="Same Value Check" width="300">

---

### 18. **ROM Price Content**
The table below shows the specific contents of the ROM, mapping each selection value to its corresponding price. Item 0 represents no selection and has a price of 0.

<img src="Images/Vending_ROM_content.png" alt="ROM Price Content Table" width="300">

---

### 19. **Advanced Integration**
This diagram represents the integration of all individual subsystems, including the ROM price selector, balance tracker, comparator, and remainder logic. It handles the full workflow from coin insertion to item vending and change return.

<img src="Images/Advanced_Vending_Combined.png" alt="Advanced Integration" width="300">

---

### 20. **Motor and LED Control**
The motor control (`M`) activates when the vending process begins. LED indicators (`LEDC` and `LEDS`) provide feedback on whether coins are required or an item is selected.

<img src="Images/Vending_Output.png" alt="Motor and LED Control" width="300">

---

### 21. **Final System Overview**
This image combines all components into the final, fully operational vending machine system. It incorporates state transitions, balance and price logic, and output controls.

<img src="Images/Vending_ha.png" alt="Final System Overview" width="300">

---

### 22. **Register-Based Balance Update**
The registers store the balance values, allowing the vending machine to track and update the user's total coin input efficiently.

<img src="Images/Vending_amount.png" alt="Register-Based Balance Update" width="300">

---

### 23. **Challenge Integration**
This diagram integrates all circuits into the final challenge system, showcasing how various subsystems interact to implement advanced vending machine features.

<img src="Images/Advanced_Vending_Combined.png" alt="Challenge Integration" width="300">