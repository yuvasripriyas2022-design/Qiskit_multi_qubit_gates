# 🧠 Multi-Qubit Gate Operations (Qiskit)

### 🎯 Objective
To explore the behavior of multi-qubit gates such as `CNOT`, `CZ`, and `SWAP`.  
This experiment demonstrates how entanglement and qubit interactions change the measurement outcomes in a 2-qubit system.

---

### 🧩 Program
**File:** `Qiskit_multi_qubit_gates.ipynb`

```python
from qiskit import QuantumCircuit, transpile
from qiskit_aer import AerSimulator

# Initialize simulator
sim = AerSimulator()

# Create a 2-qubit circuit
qc = QuantumCircuit(2, 2)

# --- Apply multi-qubit gates ---
qc.h(0)        # Hadamard on qubit 0
qc.cx(0, 1)    # CNOT with control 0 and target 1
qc.cz(0, 1)    # Controlled-Z
qc.swap(0, 1)  # Swap qubit 0 and 1

# Measure all qubits
qc.measure_all()

# Display circuit
print("Quantum Circuit:")
print(qc.draw())

# Run simulation
compiled = transpile(qc, sim)
result = sim.run(compiled, shots=1024).result()

# Display results
counts = result.get_counts()
print("\nMeasurement Counts:", counts)
```

---

### 🧠 Concept Recap

| Gate | Symbol | Function |
|------|--------|----------|
| `H` | Hadamard | Creates superposition on a qubit |
| `CX` | CNOT | Flips target qubit if control is |1⟩ |
| `CZ` | Controlled-Z | Adds phase π to target if control is |1⟩ |
| `SWAP` | SWAP | Exchanges the states of two qubits |

---

### 🧭 Procedure
1. Create a 2-qubit quantum circuit with 2 classical bits.  
2. Apply gates in the sequence: `H → CNOT → CZ → SWAP`.  
3. Measure all qubits and simulate using **AerSimulator** with 1024 shots.  
4. Observe and record the output probabilities.  
5. Modify the circuit (gate order, targets) and analyze changes.

---

### 🧩 Tasks

1. **Control/Target Variation**  
   - Change the control and target qubits in `CNOT` and `CZ`.  
   - Run simulation and note the changes in counts.

2. **Gate Removal**  
   - Remove one multi-qubit gate (e.g., `SWAP`) and observe the effect on output.

3. **Add Another Hadamard**  
   - Apply a Hadamard gate to the second qubit before the CNOT.  
   - Compare results with the original circuit.
