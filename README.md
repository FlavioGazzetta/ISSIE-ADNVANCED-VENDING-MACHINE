
# ISSIE Vending Machine Project

Welcome to the ISSIE Vending Machine Project repository! This project encapsulates the design and implementation of a unique vending machine system, using a 4-bit architecture for all operations. The vending machine integrates a custom digital logic design to handle various inputs and outputs, providing a user-friendly interface and an efficient vending process.

## Features

- **Give Back (Output):** Displays the change due to the customer.
- **M (Motor Output):** Indicates when the motor is on, activating after a purchase is made with sufficient funds. It remains on until a specific input is triggered, and a clock cycle passes.
- **Price (Output):** Shows the price of the selected item, pulled from a Read-Only Memory (ROM) that stores item prices.
- **Current Balance (Output):** Displays the total amount of money inserted into the vending machine. It updates the balance with every clock cycle based on the inserted amount.
- **LEDS (Output):** Represents the LEDs that prompt the user to select an item. They remain on until an item is selected and the clock cycle is updated.
- **LEDC (Output):** Represents the LEDs prompting the insertion of money. They stay on until an item is successfully purchased.
- **Buy (Input):** Should be kept at 0 until sufficient funds are inserted. Setting this high and updating the clock cycle after having enough money triggers the purchase process.
- **Food Select (Input):** Allows the selection of items for purchase. It interacts with a ROM to display the price of the selected item after a clock tick.
- **Coin Value (Input):** Indicates the amount of money being inserted into the vending machine. It's added to the current balance with every clock cycle.
- **V (Input):** Transitions the machine from the motor being on to off in the next clock cycle and resets the machine to its initial state (except the previously selected item remains chosen).

## Getting Started

To get started with the ISSIE Vending Machine Project, clone this repository to your local machine using the following command:

```
git clone https://github.com/FlavioGazzetta/ISSIE-ADNVANCED-VENDING-MACHINE.git
```

### Prerequisites

- A basic understanding of digital logic and circuits.

### Installation

Follow these steps to set up the project environment:

1. Install the required digital design simulation software, if not already installed.
2. Load the project files into your software.
3. Follow the software's instructions to simulate or deploy the vending machine logic onto a suitable FPGA or another digital platform.

## Usage

This project can be used as an educational tool for understanding digital systems design, specifically focusing on vending machine logic. It's also an excellent reference for projects requiring the handling of various inputs and outputs, coin operation, and dynamic state management.

## Contributing

We welcome contributions to the ISSIE Vending Machine Project! If you have suggestions for improvements or new features, feel free to fork the repository and submit a pull request.

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.

## Acknowledgments

- A special thanks to my lab partner Michael Li for his help and contribution to this project.
- Inspired by the real-world applications of digital logic in everyday devices.
