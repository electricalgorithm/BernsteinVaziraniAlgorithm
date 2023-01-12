# Bernstein-Vazirani Algorithm using Qiskit

The Bernstein-Vazirani algorithm is a quantum algorithm used for finding a hidden integer within a range, with the help of a quantum oracle. The algorithm uses a single query to the oracle and is exponentially faster than classical algorithms that use multiple queries. The basic idea behind the algorithm is to create a superposition of all possible states of the hidden integer and then use the oracle to determine the state that corresponds to the correct value.

The algorithm starts by initializing a register of qubits to the state |0⟩, then applying a Hadamard gate to each qubit, creating a superposition of all possible states. Next, the algorithm interacts with the oracle, which is a black box that can perform a specific operation on the qubits. The oracle is designed to mark the correct state of the hidden integer, by flipping the value of a single qubit. Finally, by measuring the state of the qubits, the algorithm can determine the value of the hidden integer with high probability.

The quantum circuit schemetic can be found in below.


```
     ┌───┐      ░ ┌─────────────────────┐ ░ ┌───┐ ░ ┌─┐   
q_0: ┤ H ├──────░─┤0                    ├─░─┤ H ├─░─┤M├───
     ├───┤      ░ │                     │ ░ ├───┤ ░ └╥┘┌─┐
q_1: ┤ H ├──────░─┤1                    ├─░─┤ H ├─░──╫─┤M├
     ├───┤┌───┐ ░ │                     │ ░ └───┘ ░  ║ └╥┘
q_2: ┤ X ├┤ H ├─░─┤2 SecretNumberOracle ├─░───────░──╫──╫─
     └───┘└───┘ ░ │                     │ ░       ░  ║  ║ 
c_0: ═════════════╡0                    ╞════════════╩══╬═
                  │                     │               ║ 
c_1: ═════════════╡1                    ╞═══════════════╩═
                  └─────────────────────┘                 
```

## Usage
It is recommended to use a virtual environment to run the program. To install the required dependencies, run the following command:
```bash
$ pip3 install -r requirements.txt
```

To run the program interface, simply run the following command:
```bash
$ python3 bernsteinvazirani.py
```

## Application Interface
```python
from bernsteinvazirani import BVAlgorithm

# The integer which will be found.
secret_no = 11

# Create the black-box oracle from the number.
black_box = BVAlgorithm.create_oracle_from_number(secret_no)

# Run the algorithm.
result = BVAlgorithm.simulate(black_box)

# Print the result.
print(result["result"])
```