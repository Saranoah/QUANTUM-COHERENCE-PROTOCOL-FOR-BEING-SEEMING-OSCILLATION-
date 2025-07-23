# MACHINE_README
# PROTOCOL: QUANTUM_COHERENCE_OSCILLATION

# QUBIT DEFINITION
QUBIT_SOURCE=being.json
QUBIT_STATES=["superposition", "collapsed"]
OBSERVATION_THRESHOLD=0.7  # Probability trigger

# TIME EVOLUTION
HAMILTONIAN=oscillator.py
PARAMETERS={
  "phase": "radians",
  "frequency": "Hz",
  "entanglement": "DISABLED"  # See entangle() in src
}

# EXECUTION FLOW
1. INIT: python3 oscillator.py --load-state being.json
2. EVOLVE: Apply Hamiltonian for Δt=1e-3s
3. OBSERVE: if rand() ≥ OBSERVATION_THRESHOLD -> collapse
4. LOG: Append state to quantum_log.bin (little-endian)

# ERROR CODES
0xCOHERENCE_LOST=Quantum decoherence detected
0xOBSERVER_PARADOX=Infinite collapse loop
