# Install and Use Guide

This guide explains how to set up and use the project.

## Installation Steps

1. **Fork and Download the Repository**  
   - Fork this GitHub repository to your account.
   - Clone the forked repository to your local machine using the command:
     ```bash
     git clone https://github.com/your-username/repository-name.git
     ```
   - Navigate to the cloned repository directory and create a folder:
     ```
     ISSIE_Vending_dgm/Vending_Machine_ISSIE
     ```
   - Move all project files into this folder.

2. **Install ISSIE**  
   - Download ISSIE software from [ISSIE v5.2.1 Release](https://github.com/tomcl/issie/releases/tag/v5.2.1).  
   - Follow the installation instructions provided on the ISSIE repository page.

3. **Open the Project in ISSIE**  
   - Launch ISSIE on your system.  
   - Select **Open Project** from the ISSIE interface.  
   - Navigate to the folder where you downloaded the repository.  
   - Open the file:
     ```
     Vending_Machine.dprj
     ```

## Usage

- Once the project is loaded in ISSIE, you can simulate and modify the Vending Machine design according to your needs.

## Contributing

- For questions or to contribute to the project, raise an issue or submit a pull request.


---
---


### **About the project**
This project was split into 2 parts, initially I made the challenge section of the project, then added a whole knew level of complexity to further extend and apply my knowledge for this project.


## **Challenge Part**

# DECA Part 2 Section 2 - Vending Machine State Machine

This document provides a detailed description of the procedure and results for focusing on the design and simulation of a simple vending machine state machine.

## **Procedure**

# **1. Moore State Machine Map Analysis**
The lab session began by analysing a **Moore state machine**. The state machine consisted of a 2-bit state value, broken into:
- **I1** and **I2**: Representing the bits of the current state.
- **N1** and **N2**: Representing the bits of the next state.

To simplify the state transitions, **Karnaugh maps** were used for `N1` and `N2`. These maps helped derive the Boolean equations needed for implementing the state machine.

---

## **2. Karnaugh Maps**
The derived Karnaugh maps for `N1` and `N2` provided simplified Boolean expressions for each output bit of the next state. The solutions for these maps were as follows:

- **For N1**: (Insert Boolean Expression Here)
- **For N2**: (Insert Boolean Expression Here)

---

## **3. Logic Implementation in ISSIE**

- **Bit Splitting**:
  To simplify the design process, the **I1** and **I2** inputs were split into separate bits on an ISSIE sheet. This was an optional step but made the overall design more modular and easier to debug.

- **Design of `N1` and `N2` Circuits**:
  Two separate sheets were created in ISSIE, one for `N1` and one for `N2`. These sheets implemented the Boolean equations derived from the Karnaugh maps. Truth tables were used to verify the correctness of the designs.

---

# **4. Combining `N1` and `N2` into `nxt`**

The outputs from `N1` and `N2` were combined into a single sheet called `nxt`. This represented the next-state logic for the state machine. The design was verified with a truth table to ensure proper transitions.

---

# **5. State Machine Integration**

The `nxt` logic was integrated into a larger **State Machine** sheet. The following components were included:
- Input state bits (**I1**, **I2**).
- `nxt` logic circuit for transitioning states.
- Output state bits (**N1**, **N2**).

The state machine was tested using a step simulation to ensure proper state transitions.

---

# **Output Logic for the basic Vending Machine**

# **1. Truth Table for Outputs**
The vending machine outputs included:
- **LED-S**: Indicates "Start."
- **LED-C**: Indicates "Coin Inserted."
- **M**: Activates the motor to dispense the product.

A truth table was provided to define the outputs for each state:
- **Start (00)**: Initialize.
- **W/Sel (10)**: Waiting for a selection.
- **W/Coin (01)**: Waiting for coin insertion.
- **VEND (11)**: Dispense the product.

# **2. D-Multiplexer Design**
A **D-multiplexer** was implemented to select the correct output signal (LED-S, LED-C, or M) based on the current state.

# **3. Simulation**
The output circuit was tested with a truth table, and the results matched the expected behavior:
- **Start (00)**: LED-S activated.
- **W/Sel (10)**: LED-C activated.
- **W/Coin (01)**: Motor not activated.
- **VEND (11)**: Motor activated.

Finally, the output logic was integrated into the state machine and verified through step simulations.

---

# **Adding Vending Detection**

# **Objective**
To modify the state machine to:
- Stay in **VEND (11)** state while the vending machine is dispensing (`V = 0`).
- Transition back to **Start (00)** after vending is complete (`V = 1`).

# **Approach**
1. The output from the `nxt` logic was passed through a **D-multiplexer**.
2. Two **multiplexers** were added:
   - One controlled by `V` to decide whether to stay in state `11` or transition.
   - One controlled by `M` to ensure state transitions occur only when vending is complete.

# **Simulation**
The logic circuit was verified through step simulations:
- The vending machine remained in state `11` while `V = 0`.
- It transitioned back to state `00` when `V = 1`.
- The behavior matched the truth table, with the rows highlighted in red indicating the impact of `V`.

---

### **Truth Table Summary**
Key values:
- **Start (00):** Initial state.
- **W/Sel (10):** Waiting for a selection.
- **W/Coin (01):** Waiting for coin insertion.
- **VEND (11):** Dispensing the product.

| Q0 | Q1 | C | S | V | N  | M | LED-S | LED-C |
|----|----|---|---|---|----|---|-------|-------|
| 0  | 0  | 0 | 0 | 0 | 00 | 0 | 1     | 1     |
| 0  | 0  | 0 | 0 | 1 | 00 | 0 | 1     | 1     |
| 0  | 0  | 0 | 1 | 0 | 01 | 0 | 1     | 1     |
| 1  | 1  | 1 | 1 | 0 | 11 | 1 | 0     | 0     |
| 1  | 1  | 1 | 1 | 1 | 00 | 1 | 0     | 0     |

(Continue with the full truth table if necessary.)

---

### **Conclusion**

The vending machine state machine was successfully designed, implemented, and verified. The additional challenge to include vending detection using the `V` input was completed, ensuring the machine behaved as expected in all scenarios.

This project demonstrates:
- The use of Karnaugh maps for Boolean simplifications.
- Modular design in ISSIE for state machines and output logic.
- Step-by-step simulations for verifying logic circuits.

![Moore Map Initial State](Images/Vending_flow_chart.png)

Now, what I wanted to make was a system that checks whether or not the right amount of money has been input into the machine.

When facing the challenge of part two, section 2, we decided that this was something we could and wanted to improve. We started with a vending machine with four simple states: without a coin or selection, in a starting position, or already vending. But what if we made this more like a conventional vending machine? 

The decision was to implement a **money feature**. This feature was structured so that the user wouldn't simply input a coin, but instead reach a certain value based on the item's price. We used DECA Lecture Five, where we learned to use a **ROM**. In our ROM, we stored specific values corresponding to the price of an item based on its item number.

## Creating a Synchronous ROM

The first step was creating a synchronous ROM:

![ROM Design](image.png)

### ROM Content

The ROM contained the following:

- The price for item `0` was `0`, as selecting `0` implies no item has been selected yet.

## Adding a Comparator

Next, we integrated the ROM with a **comparator** (custom-made) to check whether the chosen value from the ROM was equal to or smaller than the balance:

![Comparator Logic](image.png)

## Remainder Logic Circuit

We prepared a remainder logic circuit. It calculates the remaining balance by subtracting the price (from the ROM) from the input balance:

![Remainder Logic Circuit](image.png)

### Custom Comparator Design

Since no comparator was available on ISSIE, we built one ourselves. The comparator logic used XOR gates and multiplexers:

1. XOR gates compare bits of A and B.
2. Bits were grouped into pairs using `bus selects` and `merge wires`.
3. A multiplexer determined the output using these grouped values.
4. A D-multiplexer determined whether `A > B` or `A < B`.

![Custom Comparator](image.png)

Another important aspect was utilizing the **Add/Sub Logic Circuit** (from a previous section) with the subtraction input always set high, ensuring subtraction operations.

## Coin Balance Calculation

We then designed a circuit to track the total money input into the vending machine. This used:
- **Registers**
- A **4-bit adder** (from ISSIE)
- Current and previous balance as inputs.

![Balance Calculation Circuit](image.png)

## Full System Integration

We combined all components:
- Input `V_C` was passed through the balance logic circuit to calculate the new current balance.
- The balance fed into the remainder circuit and the comparator.
- A multiplexer and registers updated the balance and determined if the price was met.

### Fixing Initial State Issues

Initially, the system output `match = 1` (true) for a zero balance. This was fixed using constants and registers to ensure `match = 0` until the first clock rising edge.

### Final Circuit Design

The integrated circuit looked like this:

![Final Circuit](image.png)

## Step Simulation Results

We used step simulations to verify the vending machine logic.

### Example Simulation

#### Initial State:
- Selected item: `Price = 5`
- Clock tick updated.

#### Adding Coins:
1. Added 3 coins → Balance: `3` (remainder = `0` as `3 < 5`).
2. Added 2 more coins → Balance: `5`, `match = 1` (true).
3. Added 1 coin → Balance resets to `0`, and the remainder outputs `1`.

#### Changing Items:
1. Changed ROM to item `2`, `V_C = 3`.
2. Updated clock tick, adding `7` coins.
3. Verified `Balance > Price`, with correct remainder.

After minor modifications (e.g., adding state machine inputs/outputs), step simulation results remained consistent.

## Combining with the State Machine

The enhanced logic circuit was integrated with the state machine:

### Outputs:
1. `LEDC`, `LEDS`, `M` – Previous state machine outputs.
2. `Current_Balance` – Total coins input.
3. `Price` – Shows item price from the ROM.
4. `Remainder` – Current remainder.
5. `Give_Back` – Amount refunded one clock tick after balance meets the price.

### Inputs:
1. `Food_Select` – Selects an item.
2. `Coin_Value` – Specifies coin value.

![State Machine Integration](image.png)

### Step Simulation Results:
1. Selected item `0001` (`Price = 5`).
2. Input `4` coins, then `3` more → Balance: `7`.
3. Selected "Buy" → Balance reset to `0`, `Give_Back = 2`.
4. Verified adding money and changing items during simulation worked correctly.

### Final Testing:
Tested remaining edge cases:
- Adding money before selecting an item.
- Ensuring the state transitions correctly.

With these features, the vending machine behaves more like a real-world system, including tracking money, providing change, and handling item selection efficiently.

