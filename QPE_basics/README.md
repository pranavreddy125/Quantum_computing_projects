This project demonstrates phase kickback, a fundamental mechanism used in many quantum algorithms.

A control qubit is prepared in superposition, and a target qubit is prepared in an eigenstate of the operation applied by the oracle. When a controlled phase operation is applied, the phase is transferred (or “kicked back”) onto the control qubit rather than remaining on the target.

The example shows:
	•	preparation of a control qubit in superposition
	•	preparation of a target qubit as an eigenstate
	•	use of a controlled-Z gate to induce phase kickback
	•	conversion of phase information into a measurable result

Phase kickback is a core concept behind algorithms such as Bernstein–Vazirani, Quantum Phase Estimation, and related phase-based quantum algorithms.