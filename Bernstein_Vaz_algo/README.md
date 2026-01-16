This project implements the Bernstein–Vazirani (BV) algorithm using Qiskit, with a focus on applying the algorithm’s proof and theory directly to circuit-level code.

The Bernstein–Vazirani problem involves finding a hidden binary string. An oracle computes a function based on the dot product of the input string and the hidden string. Classically, determining the full hidden string requires querying the oracle once per bit. The quantum algorithm recovers the entire string in a single query using phase kickback.

⸻

Core Idea

The algorithm uses phase kickback to encode information about the hidden string into the phases of a quantum superposition. This phase information is then decoded using Hadamard gates.

Key ideas demonstrated in this project:
	•	phase kickback
	•	oracle-based computation
	•	quantum speedup (one query instead of many)
	•	translating mathematical reasoning into gate-level logic

⸻

Circuit Structure

Registers
	•	Input qubits: one qubit for each bit of the secret string
	•	Phase qubit (ancilla): used by the oracle to write phase information
	•	Classical register: used to measure and recover the secret string

⸻

Phase Qubit Preparation

The phase qubit is prepared so that it is an eigenstate of the X gate. This is required for phase kickback to occur.

Preparation steps:
	1.	Start in the zero state
	2.	Apply an X gate to move to the one state
	3.	Apply a Hadamard gate to move into the minus state

Phase kickback only works when the target qubit is in an eigenstate of the operation applied by the oracle.

⸻

Oracle Construction

The oracle is implemented using controlled-NOT gates.

For each bit of the secret string:
	•	If the secret bit is 1, a controlled-NOT is applied from the corresponding input qubit to the phase qubit
	•	If the secret bit is 0, no gate is applied

This causes the phase of the input superposition to flip depending on the hidden string, effectively encoding the secret into the phase.

⸻

Decoding the Secret String

After the oracle:
	•	Hadamard gates are applied to all input qubits
	•	The phase qubit is not measured
	•	Measuring the input qubits directly reveals the hidden string

Qiskit reports measurement results in little-endian order, so the measured bitstring appears reversed compared to the original secret.

⸻

Why the Algorithm Works
	•	The oracle applies a phase flip based on the hidden string
	•	Interference caused by the final Hadamard gates cancels all incorrect states
	•	Only the state corresponding to the secret string remains

The result is deterministic in the ideal case and demonstrates a real quantum advantage: one quantum query replaces multiple classical queries.

⸻

Notes and Extensions
	•	The Bernstein–Vazirani algorithm can also be implemented using controlled-Z style phase operations
	•	This approach does not require an explicit ancilla qubit
	•	The CZ-based version closely relates to other phase-based algorithms and phase kickback demonstrations

⸻

Purpose of This Project

This project is intended to:
	•	build intuition for why the Bernstein–Vazirani algorithm works
	•	connect theory and proof ideas directly to circuit construction
	•	understand phase kickback as a reusable quantum primitive

It serves as a conceptual bridge between introductory quantum circuits and more advanced phase-based algorithms such as Quantum Phase Estimation.