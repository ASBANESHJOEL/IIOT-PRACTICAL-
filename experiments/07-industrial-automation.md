# Experiment 7: Industrial Automation

## Aim
Control electrical loads using a relay module and a microcontroller.

## Components discussed
- Microcontroller
- 4-channel relay module
- Motors or other demonstration loads

## Working principle
The controller sets relay input pins to switch the relay channels. A relay provides electrically controlled switching between its control side and load contacts.

## Procedure outline
1. Identify the relay module's supply, input, and contact terminals.
2. Connect controller outputs to the relay inputs.
3. Connect only suitable low-voltage demonstration loads unless supervised and equipped for higher voltages.
4. Run a test sequence to switch channels.
5. Verify whether the module is active HIGH or active LOW.

## Key points
- Some relay boards are active LOW: a LOW input energizes the relay. Confirm the specific board.
- GPIO pins cannot directly power motors.
- Use appropriate motor drivers, flyback protection, and rated supplies where required.
- Never handle exposed mains wiring.

## Viva
**What is a relay?** An electrically operated switch.
**What does active LOW mean?** The input is activated by a logic LOW level.
**Why use a driver?** Loads may require more current/voltage than a GPIO can provide.
