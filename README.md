from automata.fa.dfa import DFA

dfa_baaa = DFA(
    states={'q0', 'q1', 'q2', 'q_err'},
    input_symbols={'a', 'b'},
    transitions={
        'q0': {'b': 'q1', 'a': 'q_err'},
        'q1': {'a': 'q2', 'b': 'q1'},     # q1 se repite con 'b'
        'q2': {'a': 'q2', 'b': 'q_err'},  # q2 acepta más 'a'
        'q_err': {'a': 'q_err', 'b': 'q_err'}
    },
    initial_state='q0',
    final_states={'q2'}
)

# Cadenas válidas
validas = ['baaa', 'bbaaa', 'bbbbaaaa', 'baaaa', 'baaa']

# Cadenas inválidas
invalidas = ['aab', 'bba', 'ab', 'aaa', 'b']

print(" Cadenas válidas:")
for cadena in validas:
    print(f"{cadena} → {'Aceptada' if dfa_baaa.accepts_input(cadena) else 'Rechazada'}")

print("\n Cadenas inválidas:")
for cadena in invalidas:
    print(f"{cadena} → {'Aceptada' if dfa_baaa.accepts_input(cadena) else 'Rechazada'}")
