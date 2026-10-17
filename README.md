# Inteligencia Artificial · Prácticas (UB)

Prácticas de la asignatura **Inteligencia Artificial** del Grado en Ingeniería Informática de la **Universitat de Barcelona** (Facultat de Matemàtiques i Informàtica), curso 2025–26.

Todas las prácticas comparten un mismo simulador de **finales de ajedrez** (rey + torre contra rey) sobre el que se implementan distintas familias de algoritmos de IA: búsqueda, juegos adversarios y aprendizaje por refuerzo.

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)

---

## Contenido

| Práctica | Tema | Algoritmos | Carpeta |
|---|---|---|---|
| **P2** | Juegos adversarios | Minimax con heurística, poda alfa-beta, expectimax | [`practica2-jocs-adversaris/`](practica2-jocs-adversaris) |
| **P3** | Aprendizaje por refuerzo | Q-learning (grid world y ajedrez), *drunken sailor* | [`practica3-reinforcement-learning/`](practica3-reinforcement-learning) |

```
IA/
├── practica2-jocs-adversaris/
│   ├── aichess.py          # Agente: minimax, heurística, detección de jaque mate
│   ├── chess.py            # Dinámica de la partida
│   ├── board.py            # Tablero y estados
│   └── piece.py            # Piezas y movimientos legales
├── practica3-reinforcement-learning/
│   ├── ejercicio1_qlearning_grid.ipynb   # Q-learning en un grid 3×4
│   ├── chess-qlearning/
│   │   ├── aichess.py      # DFS/BFS + Q-learning aplicado a dar mate con rey y torre
│   │   ├── auxiliary_P3.py # Utilidades de serialización de estados
│   │   ├── chess.py · board.py · piece.py
│   └── docs/
│       └── enunciado_practica3.pdf
├── requirements.txt
└── README.md
```

## El simulador

Cuatro clases jerárquicas:

- **`Piece`**: tipos de pieza y sus movimientos.
- **`Board`**: el tablero 8×8, el estado de cada color y la generación de estados sucesores.
- **`Chess`**: la dinámica de la partida, que también se puede jugar entre dos personas ejecutando `chess.py`.
- **`Aichess`**: la capa donde se implementan los algoritmos de IA que analizan y modifican la partida.

Un estado es una lista de piezas `[fila, columna, tipo]`, por ejemplo `[[7, 0, 2], [7, 5, 6]]` para la torre y el rey blancos.

---

## P2 · Juegos adversarios

Las dos partes juegan entre sí: blancas (rey + torre) contra negras (rey + torre), y cada color tiene su propia profundidad de búsqueda.

- **Detección de jaque y jaque mate** para los dos colores (`isWatchedBk`, `allBkMovementsWatched`, `isBlackInCheckMate`…).
- **Heurística** (`heuristica`): valora la posición según el material (torre capturada ±50), la distancia entre reyes, si el rey rival está empujado hacia el borde o la esquina, y un bonus o penalización por jaque.
- **Minimax** (`minimaxGame`, `_minimax`) con profundidad configurable para cada color.
- **Poda alfa-beta** (`_minimax_alphaBeta`): la recursión con poda ya está escrita, pero falta conectarla a `alphaBetaPoda`.
- **Expectimax** (`expectimax`), con utilidades estadísticas (`mean`, `standard_deviation`, `calculateValue`): la función principal aún está por completar.

```bash
cd practica2-jocs-adversaris
python aichess.py        # partida minimax con profundidad 4 vs 4
```

## P3 · Aprendizaje por refuerzo (Q-learning)

### Ejercicio 1: grid world 3×4

En el notebook [`ejercicio1_qlearning_grid.ipynb`](practica3-reinforcement-learning/ejercicio1_qlearning_grid.ipynb) el agente aprende a ir de la salida `[2,0]` a la meta `[0,3]` esquivando un obstáculo, con `α = 0.1`, `γ = 0.95` y `ε = 0.8`.

| Variante | Recompensas | Convergencia | Camino aprendido |
|---|---|---|---|
| **1.a** | −1 por paso, +100 en la meta | ~531 épocas | `[2,0] → [2,1] → [2,2] → [2,3] → [1,3] → [0,3]` |
| **1.b** | Recompensas graduadas según la distancia | ~664 épocas | `[2,0] → [1,0] → [0,0] → [0,1] → [0,2] → [0,3]` |
| **1.c** | *Drunken sailor*: acción aleatoria con probabilidad `p` | ~662 épocas (`p = 0.01`) | El mismo que 1.b |

Media de 10 ejecuciones: con `p = 0.1`, el agente "borracho" tarda **un 7,5 % más** en converger que el sobrio (712 frente a 662 épocas).

El notebook imprime la Q-table inicial, dos intermedias y la final de cada variante, tal como pide el enunciado.

### Ejercicio 2: Q-learning en ajedrez

En `chess-qlearning/aichess.py` las blancas (rey + torre) aprenden a dar **jaque mate** al rey negro mediante Q-learning:

- El estado se serializa como una cadena (`stateToString` / `stringToState`) y sirve de clave de la Q-table.
- La política es ε-greedy (`choose_action`), con un parámetro opcional de *drunkenness* que añade ruido a las acciones.
- `trainQL` entrena el agente y `reconstructPathQL` extrae la secuencia de jugadas hasta el mate.
- El fichero también incluye **DFS** y **BFS** como referencia.

```bash
cd practica3-reinforcement-learning/chess-qlearning
python aichess.py        # menú interactivo: entrenar (normal o drunken) y reconstruir el camino
```

---

## Instalación

```bash
git clone https://github.com/Joanfmir/IA.git
cd IA
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

## Autores

- **Joan Fernández Mir** · [@Joanfmir](https://github.com/Joanfmir)
- **Rodolfo Romeo Hernández Villarreal** · [@Rodo1204](https://github.com/Rodo1204)

Simulador y enunciados: profesorado de IA de la UB (Ignasi Cos, Polyxeni Gkontra).
