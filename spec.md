# Especificacion de `exercici1.ipynb`

## Objetivo

Completar un analisis exploratorio reproducible del Padron Municipal de Habitantes de Barcelona entre 1997 y 2026. El notebook debe cargar, limpiar, agregar y visualizar datos de poblacion, domicilios y edad, y terminar con una interpretacion critica.

## Entradas

- `data/pad_dimensions.csv`: diccionario de codigos.
- `data/poblacio_lloc_naix/*.csv`: poblacion por lugar de nacimiento y sexo, un fichero por ano.
- `data/domicilis_estructura/2026_domicilis_estructura.csv`: estructura de domicilios.
- `data/edat_lloc_naix/2026_edat_lloc_naix.csv`: poblacion por edad quinquenal, lugar y sexo.

Las rutas deben funcionar ejecutando el notebook desde la carpeta que contiene `data/`.

## Estado de las celdas

- **✅ Ejemplo resuelto:** se puede ejecutar y consultar como guia, pero no requiere implementar una solucion nueva.
- **🔧 Tarea pendiente:** se debe completar con codigo, una visualizacion o una respuesta escrita.

En este notebook, las secciones ✅ son `1.1`, `1.3`, `4.2`, `5.1` y `5.2`. El trabajo de entrega corresponde a las secciones y subapartados marcados con 🔧. Las celdas ✅ deben ejecutarse porque preparan variables como `dims`, `lloc_naix_dict`, `tipus_dict` y `df_edat`, pero no se deben contar como tareas pendientes.

## Requisitos funcionales por ejercicios

### Parte 1 — Exploracio inicial: un sol any (2026)

#### 1.1 ✅ Càrrega del fitxer — ejemplo resuelto

Ejecutar el ejemplo existente para cargar `2026_poblacio_lloc_naix.csv` y consultar su forma y primeras filas.

#### 1.2 🔧 Inspeccio basica

- **1.2.a** Mostrar columnas y tipos.
- **1.2.b** Contar nulos por columna.
- **1.2.c** Contar valores `..` de `Valor` y calcular su porcentaje.
- **1.2.d** Contar y listar los valores unicos de `LLOC_NAIX`.

#### 1.3 ✅ Diccionari de codis — ejemplo resuelto

Ejecutar las celdas existentes que cargan `pad_dimensions.csv` y filtran la dimension `LLOC_NAIX`.

#### 1.4 Comprensio dels codis

- **1.4.a** Identificar y explicar los codigos agregados 1-6.
- **1.4.b** Calcular la poblacion total de Barcelona en 2026 usando esos codigos y ambos sexos.
- **1.4.c** Escribir una hipotesis sobre la diferencia frente a la cifra oficial.

### Parte 2 — Neteja i transformacio

#### 2.1 🔧 Funcio de neteja

Implementar `netejar_poblacio(path)`: leer el CSV, convertir `Valor` con `errors="coerce"`, filtrar `LLOC_NAIX` 1-6, extraer `Any` de `Data_Referencia` y devolver el DataFrame limpio.

#### 2.2 Agregacio a nivell de ciutat

Crear `df_ciutat` agrupando por `Any`, `LLOC_NAIX` y `SEXE`. Para 2026 deben resultar 12 filas.

#### 2.3 Unio amb el diccionari

Unir `df_ciutat` con `lloc_naix_dict` mediante `merge`.

#### 2.4 Taula resum

Crear una tabla pivot de 2026 con lugar de nacimiento en filas, sexo en columnas y total general.

#### 2.5 Reflexio sobre la qualitat

Redactar 3-5 frases sobre las decisiones de limpieza, el impacto de `..` y el riesgo de sesgo al ignorarlos.

### Parte 3 — Serie temporal 1997-2026

#### 3.1 Carrega de tots els anys

Localizar los 30 CSV con `glob`, aplicar `netejar_poblacio` y concatenar en `df_serie`.

#### 3.2 Consistencia entre anys

- **3.2.a** Revisar filas por ano y explicar diferencias atipicas.
- **3.2.b** Calcular la poblacion total anual y representarla con lineas.

#### 3.3 Agregacio per lloc de naixement

Crear `serie_lloc` con `Any`, `LLOC_NAIX`, `Lloc_Naix_Label` y `Total`, sumando ambos sexos.

#### 3.4 Visualitzacio de la serie

Crear cuatro lineas: Barcelona, resto de Cataluna, resto de Espana y resto del mundo. Agrupar los codigos 4-6 para este ultimo grupo, anadir etiquetas finales de 2026, anotacion historica, titulo, ejes y leyenda.

### Parte 4 — Estructura dels domicilis (2026)

#### 4.1 Carrega i exploracio

Inspeccionar forma, tipos, nulos y valores unicos de `TIPUS_DOMICILI`.

#### 4.2 ✅ Diccionari de `TIPUS_DOMICILI` — ejemplo resuelto

Ejecutar la celda existente para obtener las etiquetas de la dimension correspondiente.

#### 4.3 Agregacio i unio

Agregar el numero de domicilios por codigo, unir etiquetas y ordenar de mayor a menor.

#### 4.4 Visualitzacio de domicilis

Crear barras horizontales para los 12 tipos, mostrando porcentajes y diferenciando categorias por color.

#### 4.5 Indicadors clau

Calcular domicilios unipersonales, domicilios con menores (codigos 9-12) y la ratio entre mujeres y hombres solos de 65 o mas anos.

### Parte 5 — Edat mitjana per lloc de naixement (2026)

#### 5.1 ✅ Estructura del dataset y 5.2 ✅ diccionario — ejemplos resueltos

Ejecutar las celdas existentes que cargan el fichero de edad y el diccionario de grupos `EDAT_Q`.

#### 5.3 Punt mig de cada grup

Completar `MIDPOINTS` con `2, 7, ..., 97`, `100` para el grupo 20 y `None` para el grupo 21.

#### 5.4 Calcul de la mitjana ponderada

Implementar `edat_mitjana_per_lloc(df, midpoints)`, excluir `EDAT_Q == 21` y devolver la edad media por `LLOC_NAIX`.

#### 5.5 Visualitzacio i interpretacio

Graficar edades medias, incluir la media global y responder las dos preguntas interpretativas del notebook.

### Parte 6 — Sintesi i comunicacio

#### 6.1 Informe breu

Escribir un informe de 300-500 palabras sobre tendencias, envejecimiento, convivencia y limitaciones causales.

#### 6.2 El millor grafic

Elegir un grafico, mejorarlo con titulo, subtitulo, etiquetas, leyenda y fuente, y justificar la eleccion en 3-4 frases.

#### 6.3 Una pregunta oberta

Proponer una pregunta que los datos no respondan y el dataset adicional necesario.

## Criterios de aceptacion

- [ ] Todas las celdas marcadas con 🔧 estan resueltas.
- [ ] El notebook se ejecuta desde cero sin errores.
- [ ] `netejar_poblacio` funciona para un fichero y para los 30 anos.
- [ ] `df_serie` contiene los anos 1997-2026 y solo codigos 1-6.
- [ ] Las agregaciones distinguen valores enmascarados de ceros.
- [ ] Los graficos tienen titulo, ejes, etiquetas, leyenda cuando corresponde y fuente.
- [ ] La media de edad excluye `No consta` y es ponderada por poblacion.
- [ ] El informe tiene entre 300 y 500 palabras y explica limitaciones y causalidad.

## Decisiones que debe poder explicar la persona desarrolladora

La persona desarrolladora debe poder explicar, modificar, depurar y mantener cada linea de codigo que incorpore. Si no puede hacerlo, debe detenerse y pedir aclaracion antes de continuar.
