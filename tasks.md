# Tareas de `exercici1.ipynb`

Cada tarea se implementa, revisa y marca como `[x]` antes de comenzar la siguiente. La persona desarrolladora debe poder explicar, modificar, depurar y mantener el codigo resultante.

Las celdas ✅ no son tareas pendientes: son ejemplos resueltos que se ejecutan como guia. Las tareas de esta lista corresponden unicamente a las celdas 🔧.

## Parte 1 — Exploracio inicial: un sol any (2026)

### 1.1 Càrrega del fitxer

- ✅ Ejemplo resuelto: ejecutar la carga existente y consultar forma y primeras filas si hace falta.

### 1.2 Inspeccio basica

- [x] **1.2.a** Mostrar columnas y tipos.
- [x] **1.2.b** Contar nulos por columna.
- [ ] **1.2.c** Contar `..` y calcular porcentaje.
- [ ] **1.2.d** Listar valores unicos de `LLOC_NAIX`.

### 1.3 Diccionari de codis

- ✅ Ejemplo resuelto: ejecutar las celdas existentes que cargan `pad_dimensions.csv` y filtran `LLOC_NAIX`.

### 1.4 Comprensio dels codis

- [ ] **1.4.a** Identificar y explicar los codigos agregados 1-6.
- [ ] **1.4.b** Calcular la poblacion total de 2026.
- [ ] **1.4.c** Escribir la hipotesis sobre la diferencia oficial.

## Parte 2 — Neteja i transformacio

### 2.1 Funcio de neteja

- [ ] Implementar `netejar_poblacio(path)`.
- [ ] Probarla con el fichero de 2026.

### 2.2 Agregacio a nivell de ciutat

- [ ] Crear `df_ciutat` con `groupby`.
- [ ] Verificar las 12 filas esperadas.

### 2.3 Unio amb el diccionari

- [ ] Unir etiquetas mediante `merge`.

### 2.4 Taula resum

- [ ] Crear la tabla pivot por lugar y sexo.
- [ ] Incluir el total general.

### 2.5 Reflexio sobre la qualitat

- [ ] Explicar el tratamiento de `..` y `NaN`.
- [ ] Explicar el posible sesgo.

## Parte 3 — Serie temporal 1997-2026

### 3.1 Carrega de tots els anys

- [ ] Localizar los CSV con `glob`.
- [ ] Confirmar que hay 30 ficheros.
- [ ] Concatenar los resultados en `df_serie`.

### 3.2 Consistencia entre anys

- [ ] **3.2.a** Revisar filas por ano y explicar diferencias.
- [ ] **3.2.b** Calcular y graficar la poblacion total anual.

### 3.3 Agregacio per lloc de naixement

- [ ] Crear `serie_lloc` con las cuatro columnas requeridas.

### 3.4 Visualitzacio de la serie

- [ ] Crear las cuatro lineas y agrupar codigos 4-6.
- [ ] Anadir etiquetas finales, anotacion, titulo y leyenda.
- [ ] Guardar `grafic_serie.png`.

## Parte 4 — Estructura dels domicilis (2026)

### 4.1 Carrega i exploracio

- [ ] Inspeccionar forma, tipos, nulos y codigos.

### 4.2 Diccionari de `TIPUS_DOMICILI`

- ✅ Ejemplo resuelto: ejecutar la celda existente para obtener las etiquetas.

### 4.3 Agregacio i unio

- [ ] Agregar por codigo, unir etiquetas y ordenar.

### 4.4 Visualitzacio de domicilis

- [ ] Crear barras horizontales de los 12 tipos.
- [ ] Anadir porcentajes y colores por categoria.

### 4.5 Indicadors clau

- [ ] Calcular unipersonales.
- [ ] Calcular domicilios con menores, codigos 9-12.
- [ ] Comparar mujeres y hombres solos de 65 o mas anos.
- [ ] Calcular e interpretar la ratio.

## Parte 5 — Edat mitjana per lloc de naixement (2026)

### 5.1 Estructura del dataset

- ✅ Ejemplo resuelto: ejecutar la celda existente que carga el CSV de edad.

### 5.2 Diccionari de grups d'edat

- ✅ Ejemplo resuelto: ejecutar la celda existente que obtiene las etiquetas de `EDAT_Q`.

### 5.3 Punt mig de cada grup

- [ ] Completar `MIDPOINTS`.
- [ ] Pasar la asercion de comprobacion.

### 5.4 Calcul de la mitjana ponderada

- [ ] Implementar `edat_mitjana_per_lloc`.
- [ ] Excluir el grupo 21.
- [ ] Unir las etiquetas de lugar.

### 5.5 Visualitzacio i interpretacio

- [ ] Crear el grafico de edades y linea global.
- [ ] Guardar `grafic_edat_mitjana.png`.
- [ ] Redactar las dos interpretaciones.

## Parte 6 — Sintesi i comunicacio

### 6.1 Informe breu

- [ ] Redactar 300-500 palabras.
- [ ] Responder tendencias, envejecimiento, convivencia y causalidad.

### 6.2 El millor grafic

- [ ] Elegir y mejorar un grafico.
- [ ] Anadir titulo, subtitulo, etiquetas, leyenda y fuente.
- [ ] Justificar la eleccion en 3-4 frases.

### 6.3 Una pregunta oberta

- [ ] Formular una pregunta no respondible con estos datos.
- [ ] Proponer el dataset adicional.

## Verificacion y cierre

- [ ] Reiniciar el kernel y ejecutar todo el notebook desde cero.
- [ ] Buscar y eliminar marcadores sin resolver como `...` y `___`.
- [ ] Revisar que los graficos y sus salidas son legibles.
- [ ] Marcar una sola tarea como completada despues de revisarla.
- [ ] Informar que tarea y que ficheros se han tocado.
- [ ] Detenerse y esperar confirmacion antes de iniciar la siguiente tarea.
