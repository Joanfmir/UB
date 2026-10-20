# Tareas de `exercici1.ipynb`

Cada tarea se implementa, revisa y marca como `[x]` antes de comenzar la siguiente. La persona desarrolladora debe poder explicar, modificar, depurar y mantener el codigo resultante.

Las celdas ✅ no son tareas pendientes: son ejemplos resueltos que se ejecutan como guia. Las tareas de esta lista corresponden unicamente a las celdas 🔧.

## Parte 1 — Exploracio inicial: un sol any (2026)

### 1.1 Càrrega del fitxer

- ✅ Ejemplo resuelto: ejecutar la carga existente y consultar forma y primeras filas si hace falta.

### 1.2 Inspeccio basica

- [x] **1.2.a** Mostrar columnas y tipos.
- [x] **1.2.b** Contar nulos por columna.
- [x] **1.2.c** Contar `..` y calcular porcentaje.
- [x] **1.2.d** Listar valores unicos de `LLOC_NAIX`.

### 1.3 Diccionari de codis

- ✅ Ejemplo resuelto: ejecutar las celdas existentes que cargan `pad_dimensions.csv` y filtran `LLOC_NAIX`.

### 1.4 Comprensio dels codis

- [x] **1.4.a** Identificar y explicar los codigos agregados 1-6.
- [x] **1.4.b** Calcular la poblacion total de 2026.
- [x] **1.4.c** Escribir la hipotesis sobre la diferencia oficial.

## Parte 2 — Neteja i transformacio

### 2.1 Funcio de neteja

- [x] Implementar `netejar_poblacio(path)`.
- [x] Probarla con el fichero de 2026.

### 2.2 Agregacio a nivell de ciutat

- [x] Crear `df_ciutat` con `groupby`.
- [x] Verificar las 12 filas esperadas.

### 2.3 Unio amb el diccionari

- [x] Unir etiquetas mediante `merge`.

### 2.4 Taula resum

- [x] Crear la tabla pivot por lugar y sexo.
- [x] Incluir el total general.

### 2.5 Reflexio sobre la qualitat

- [x] Explicar el tratamiento de `..` y `NaN`.
- [x] Explicar el posible sesgo.

## Parte 3 — Serie temporal 1997-2026

### 3.1 Carrega de tots els anys

- [x] Localizar los CSV con `glob`.
- [x] Confirmar que hay 30 ficheros.
- [x] Concatenar los resultados en `df_serie`.

### 3.2 Consistencia entre anys

- [x] **3.2.a** Revisar filas por ano y explicar diferencias.
- [x] **3.2.b** Calcular y graficar la poblacion total anual.

### 3.3 Agregacio per lloc de naixement

- [x] Crear `serie_lloc` con las cuatro columnas requeridas.

### 3.4 Visualitzacio de la serie

- [x] Crear las cuatro lineas y agrupar codigos 4-6.
- [x] Anadir etiquetas finales, anotacion, titulo y leyenda.
- [x] Guardar `grafic_serie.png`.

## Parte 4 — Estructura dels domicilis (2026)

### 4.1 Carrega i exploracio

- [x] Inspeccionar forma, tipos, nulos y codigos.

### 4.2 Diccionari de `TIPUS_DOMICILI`

- ✅ Ejemplo resuelto: ejecutar la celda existente para obtener las etiquetas.

### 4.3 Agregacio i unio

- [x] Agregar por codigo, unir etiquetas y ordenar.

### 4.4 Visualitzacio de domicilis

- [x] Crear barras horizontales de los 12 tipos.
- [x] Anadir porcentajes y colores por categoria.

### 4.5 Indicadors clau

- [x] Calcular unipersonales.
- [x] Calcular domicilios con menores, codigos 9-12.
- [x] Comparar mujeres y hombres solos de 65 o mas anos.
- [x] Calcular e interpretar la ratio.

## Parte 5 — Edat mitjana per lloc de naixement (2026)

### 5.1 Estructura del dataset

- ✅ Ejemplo resuelto: ejecutar la celda existente que carga el CSV de edad.

### 5.2 Diccionari de grups d'edat

- ✅ Ejemplo resuelto: ejecutar la celda existente que obtiene las etiquetas de `EDAT_Q`.

### 5.3 Punt mig de cada grup

- [x] Completar `MIDPOINTS`.
- [x] Pasar la asercion de comprobacion.

### 5.4 Calcul de la mitjana ponderada

- [x] Implementar `edat_mitjana_per_lloc`.
- [x] Excluir el grupo 21.
- [x] Unir las etiquetas de lugar.

### 5.5 Visualitzacio i interpretacio

- [x] Crear el grafico de edades y linea global.
- [x] Guardar `grafic_edat_mitjana.png`.
- [x] Redactar las dos interpretaciones.

## Parte 6 — Sintesi i comunicacio

### 6.1 Informe breu

- [x] Redactar 300-500 palabras.
- [x] Responder tendencias, envejecimiento, convivencia y causalidad.

### 6.2 El millor grafic

- [x] Elegir y mejorar un grafico.
- [x] Anadir titulo, subtitulo, etiquetas, leyenda y fuente.
- [x] Justificar la eleccion en 3-4 frases.

### 6.3 Una pregunta oberta

- [x] Formular una pregunta no respondible con estos datos.
- [x] Proponer el dataset adicional.

## Verificacion y cierre

- [x] Reiniciar el kernel y ejecutar todo el notebook desde cero.
- [x] Buscar y eliminar marcadores sin resolver como `...` y `___`.
- [x] Revisar que los graficos y sus salidas son legibles.
- [ ] Marcar una sola tarea como completada despues de revisarla.
- [ ] Informar que tarea y que ficheros se han tocado.
- [ ] Detenerse y esperar confirmacion antes de iniciar la siguiente tarea.
