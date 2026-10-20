# Arquitectura del proyecto

## Nota de compatibilidad

`reglesIA.md` menciona HTML/CSS/JS y Chart.js, pero esta practica concreta resuelve `exercici1.ipynb`, un notebook de analisis de datos. Por tanto, introducir una aplicacion web o Chart.js no encaja con el enunciado. La arquitectura correcta para este proyecto usa Python, pandas, numpy, matplotlib y Jupyter.

## Estructura

```text
pra╠Çctica 1/
├── exercici1.ipynb
├── exercici2.ipynb
├── README.md
├── reglesIA.md
├── spec.md
├── architecture.md
├── tasks.md
└── data/
    ├── pad_dimensions.csv
    ├── poblacio_lloc_naix/
    ├── edat_lloc_naix/
    └── domicilis_estructura/
```

## Responsabilidad de los ficheros

- `exercici1.ipynb`: implementacion, resultados, graficos y respuestas del ejercicio.
- `exercici2.ipynb`: ejercicio posterior de prediccion; queda fuera del alcance actual.
- `README.md`: contexto, instalacion y entrega.
- `reglesIA.md`: reglas de uso del asistente.
- `spec.md`: requisitos funcionales y criterios de aceptacion.
- `architecture.md`: estructura, responsabilidades y decisiones tecnicas.
- `tasks.md`: trabajo dividido en tareas pequenas y verificables.
- `data/`: entradas originales; no se modifican desde el notebook.

## Organizacion por ejercicios del notebook

La implementacion sigue el mismo orden que las Partes 1-6 de `exercici1.ipynb`. Cada parte general contiene sus subapartados y produce las variables que necesita la parte siguiente.

Dentro de cada parte se distingue el estado del notebook:

- Las celdas **✅** son ejemplos ya resueltos. Se ejecutan para preparar datos y sirven como referencia.
- Las celdas **🔧** son los puntos de implementacion que deben resolverse.

Por tanto, la arquitectura no duplica la logica de las celdas ✅; las usa como entradas para las tareas 🔧.

### Parte 1 — Exploracio inicial: un sol any

El subapartado 1.1 ✅ carga 2026 como ejemplo. Los subapartados 1.2 y 1.4 🔧 inspeccionan columnas, nulos, `..` y codigos. El subapartado 1.3 ✅ deja preparado el diccionario de `LLOC_NAIX`.

### Parte 2 — Neteja i transformacio

Los subapartados 2.1-2.5 implementan la funcion comun de limpieza, agregan por ciudad, unen etiquetas, crean la tabla pivot y documentan la calidad de los datos. Su salida principal es `df_net` y `df_ciutat`.

### Parte 3 — Serie temporal 1997-2026

Los subapartados 3.1-3.4 aplican la limpieza a los 30 ficheros, revisan consistencia, construyen `serie_lloc` y crean la visualizacion de cuatro grupos de origen.

### Parte 4 — Estructura dels domicilis

El subapartado 4.2 ✅ deja preparado el diccionario de tipos de domicilio. Los subapartados 4.1 y 4.3-4.5 🔧 cargan, agregan, visualizan y calculan los indicadores de convivencia.

### Parte 5 — Edat mitjana per lloc de naixement

Los subapartados 5.1 y 5.2 ✅ cargan edad y consultan `EDAT_Q`. Los subapartados 5.3-5.5 🔧 completan `MIDPOINTS`, calculan medias ponderadas y presentan la interpretacion demografica.

### Parte 6 — Sintesi i comunicacio

Los subapartados 6.1-6.3 convierten los resultados en un informe, un grafico final justificado y una pregunta abierta.

## Flujo de datos

```text
CSV originales
    |
    v
Carga con pandas
    |
    v
Inspeccion de tipos, nulos y valores enmascarados
    |
    v
netejar_poblacio(path)
    |
    +--> df_ciutat --> pivot 2026
    |
    +--> df_serie --> serie_lloc --> serie temporal
    |
    +--> domicilios --> distribucion y KPIs
    |
    +--> edades + MIDPOINTS --> edad media ponderada
    |
    v
Graficos e interpretacion critica
```

## Componentes y contratos

### Configuracion

Define imports y rutas relativas: `BASE`, `PATH_POBLACIO`, `PATH_EDAT`, `PATH_DOMICILIS` y `PATH_DIMS`.

### Diccionario de dimensiones

`dims` contiene los codigos y sus descripciones. De el se derivan `lloc_naix_dict` y `tipus_dict`. Las etiquetas se anaden despues de agregar datos, evitando duplicaciones innecesarias.

### Funcion de limpieza

`netejar_poblacio(path)` es la unica entrada comun para los CSV de poblacion. Debe devolver un DataFrame con `Valor` numerico, `Any` entero o equivalente y solo `LLOC_NAIX` 1-6. Los `..` se convierten en `NaN`; no se imputan sin justificarlo.

### Agregaciones

- Poblacion 2026: `groupby(["Any", "LLOC_NAIX", "SEXE"])`.
- Serie por origen: `groupby(["Any", "LLOC_NAIX"])` despues de sumar ambos sexos.
- Mundo: agrupacion de codigos 4, 5 y 6.
- Domicilios: `groupby("TIPUS_DOMICILI")` y porcentaje sobre el total.
- Edad: suma de `midpoint * Valor` dividida por la suma de `Valor`, excluyendo el codigo 21.

## Decisiones de visualizacion

- Lineas para tendencias temporales.
- Barras horizontales para domicilios, porque las etiquetas son largas.
- Barras verticales para comparar edades medias.
- Colores coherentes entre graficos y etiquetas descriptivas, nunca solo codigos numericos.
- Guardar las figuras solicitadas con `bbox_inches="tight"`.

## Validacion

Antes de pasar a la siguiente tarea, reiniciar el kernel y ejecutar las celdas relacionadas. Comprobar que:

- se localizaron 30 ficheros de poblacion;
- los anos van de 1997 a 2026;
- la agregacion de 2026 produce 12 combinaciones de lugar y sexo;
- `MIDPOINTS` contiene 21 valores numericos y un `None` para el codigo 21;
- los porcentajes usan el total correcto;
- las conclusiones no confunden correlacion con causalidad.
