# ISSIE Advanced Vending Machine Project

Welcome to the **ISSIE Advanced Vending Machine Project** repository! This project goes beyond the conventional vending machine system, incorporating advanced digital logic to create a user-friendly, feature-rich design. Utilizing a 4-bit architecture, this vending machine can dynamically handle item selection, coin input, price calculation, and change returns, making it a versatile tool for learning and experimentation.

---

## **Project Features**

### Key Outputs:
1. **Change (Give Back):**
   - Displays the amount of change to be returned after a purchase.
2. **Motor Control (M):**
   - Activates the motor to dispense the selected item when the sufficient amount is reached. Turns off after the change is dispensed and the system is reset.
3. **Price Display:**
   - Retrieves and shows the price of the selected item from a Read-Only Memory (ROM) module.
4. **Current Balance:**
   - Updates and shows the cumulative value of inserted coins.
5. **LED Indicators:**
   - **LEDS:** Guides item selection, turning off once an item is chosen.
   - **LEDC:** Prompts coin insertion, turning off when sufficient balance is reached.

### Key Inputs:
1. **Food Select:**
   - Used to choose the desired item from the vending machine.
2. **Coin Value:**
   - Represents the value of coins inserted into the machine.
3. **Buy Command:**
   - Triggers the purchase process once sufficient funds are available.
4. **Reset Command (V):**
   - Resets the vending machine to its initial state for the next transaction.

---

## **Implementation Overview**

### **Initial Design**
The original state machine was a basic 4-state Moore machine, which transitioned between:
1. **No Coin, No Selection**: Initial idle state.
2. **Coin Inserted, No Selection**: Awaiting item selection.
3. **Coin Inserted, Item Selected**: Ready to dispense.
4. **Vending**: Dispensing the item.

### **Enhancements**
To mimic the functionality of a real-world vending machine:
- A **synchronous ROM module** was introduced to store item prices. Selecting an item retrieves its price from the ROM.
- A **comparator circuit** checks whether the inserted balance meets or exceeds the price of the selected item.
- A **remainder logic circuit** calculates and outputs the change if the inserted balance exceeds the item price.

### **Custom Circuits**
1. **Comparator:**
   - Designed using XOR gates, multiplexers, and demultiplexers to compare the balance with the price.
2. **Adder/Subtractor Logic:**
   - Modified to perform continuous subtraction for change calculation.
3. **Balance Tracker:**
   - Tracks cumulative coin input using registers and a 4-bit adder.

---

## **Simulation Steps**

### Example: Purchasing an Item
1. **Item Selection:**
   - Select an item (e.g., price = 5).
2. **Coin Input:**
   - Insert coins in steps (e.g., insert 3, then 2 to reach 5).
3. **Purchase:**
   - Trigger the `Buy` input once the balance matches or exceeds the price.
4. **Change Dispense:**
   - The machine returns the remainder (if any) and resets the balance.

### Step-by-Step Simulation:
- **Initial State:** 
  - Select item **0001** (price = 5 coins).
  - Insert coins sequentially (3 → 2).
  - Balance is now sufficient; motor activates, and remainder (if any) is displayed.
- **Testing Other Scenarios:**
  - Insert excess coins to verify remainder logic.
  - Change item selection mid-process to validate dynamic ROM updates.
  - Reset the system and test all outputs (LEDS, LEDC, M, etc.).

---

## **Project Architecture**

The vending machine integrates the following:
- **Synchronous ROM**: Stores item prices.
- **Comparator**: Verifies if the balance meets the item price.
- **Remainder Circuit**: Calculates change to be dispensed.
- **State Machine**: Coordinates all operations, ensuring proper transitions between states.

The final design seamlessly integrates the advanced logic into the state machine, allowing for realistic vending machine behavior.

---

## **Key Features in Final Design**
- **Dynamic Price Display:** Automatically updates based on item selection.
- **Real-Time Balance Updates:** Tracks and displays the total amount inserted.
- **Accurate Change Calculation:** Returns the correct remainder when balance exceeds the price.
- **Error Handling:** Prevents simultaneous coin insertion and item selection during a transaction.
- **Reset Functionality:** Resets the machine to its initial state after every purchase.

---

## **Simulation and Testing**

Step-by-step simulations were performed to validate all functionalities, including:
1. Coin insertion and balance tracking.
2. Correct price retrieval from ROM.
3. Proper match and remainder calculations.
4. Transitioning between states during and after a purchase.

The logic circuits and state machine performed flawlessly under all test scenarios.

---

## **Usage**

This project serves as:
1. An educational tool for learning digital logic design and state machines.
2. A starting point for advanced projects involving coin-operated machines or dynamic input/output handling.

---

## **Contributing**

Contributions are welcome! Feel free to fork the repository, implement improvements, and submit a pull request.

---

## **Acknowledgments**

- Special thanks to **Michael Li** for valuable guidance.
- Inspired by the practical applications of digital logic in everyday devices.

---
