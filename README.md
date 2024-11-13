 # Advanced Vending Machine Logic: Adding a Value Counting Feature

In this section, I wanted to dive deeper into the challenge by adding a feature that every vending machine has: **Counting Values**.

Initially, our Moore map looked like this:

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

