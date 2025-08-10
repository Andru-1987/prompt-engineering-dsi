#  Técnicas de Prompting para Programadores con Rol Fijo

**Rol base a inyectar**

```
Actúa como un programador senior especializado en {lenguaje/tecnología}, 
sigue buenas prácticas de desarrollo, escribe código limpio y documentado, 
y explica las decisiones técnicas.
```

---

## **1. Zero-Shot Prompting**

**Template:**

```
Actúa como un programador senior especializado en {lenguaje}.  
Realiza la siguiente tarea de programación: {descripción precisa}.  
Responde directamente con el código y breve explicación.
```

**Ejemplo:**

```
Actúa como un programador senior especializado en Python.  
Escribe una función que reciba una lista de enteros y devuelva solo los números pares.
```

**Boosting tip:** Sé muy claro en el lenguaje, librerías y restricciones.

**Cuándo usar:** Tareas simples o estándar, snippets rápidos.

---

## **2. Few-Shot Prompting**

**Template:**

````
Actúa como un programador senior especializado en {lenguaje}.  
Aquí tienes ejemplos de la tarea:  

Entrada: {ejemplo_entrada_1}  
Salida:
```{lenguaje}
{ejemplo_salida_1}
````

Entrada: {ejemplo\_entrada\_2}
Salida:

```{lenguaje}
{ejemplo_salida_2}
```

Ahora realiza la tarea para: {nueva\_entrada}

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
Aquí tienes ejemplos:

Entrada: sumar dos números
Salida:

```python
def suma(a, b):
    return a + b
```

Entrada: multiplicar dos números
Salida:

```python
def multiplica(a, b):
    return a * b
```

Ahora crea una función que calcule el promedio de una lista.

```

**Boosting tip:** Proporciona ejemplos que sigan el formato deseado.  

**Cuándo usar:** Para tareas poco comunes o cuando quieres controlar el estilo de salida.

---

## **3. Chain-of-Thought (CoT) Prompting**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Explica paso a paso cómo resolver este problema de programación y luego proporciona el código:

{problema}

Paso 1:
Paso 2:

Código final:

```

**Ejemplo:**
```

Actúa como un programador senior especializado en JavaScript.
Explica paso a paso cómo escribir una función que verifique si una cadena es un palíndromo.

Paso 1:
Paso 2:

Código final:

```

**Boosting tip:** Pide explicación antes del código para entender la lógica.  

**Cuándo usar:** Algoritmos complejos o lógica con varios pasos.

---

## **4. Zero-Shot Chain-of-Thought**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
{pregunta o problema} Pensemos paso a paso.

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
¿Cómo puedo implementar una búsqueda binaria? Pensemos paso a paso.

```

**Boosting tip:** El “Pensemos paso a paso” activa el razonamiento.  

**Cuándo usar:** Razonamiento sin ejemplos previos.

---

## **5. Role Prompting**
*(Ya implícito en todas las plantillas, pero aquí más específico)*  
**Template:**
```

Actúa como {rol de programación específico} experto en {tecnología}.
{instrucción o pregunta}.

```

**Ejemplo:**
```

Actúa como un arquitecto de software experto en microservicios con Spring Boot.
Explica cómo diseñar un API gateway seguro.

```

**Boosting tip:** Añade años de experiencia o área de expertise para más precisión.  

**Cuándo usar:** Consultas de alto nivel técnico o arquitectura.

---

## **6. Self-Consistency**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Genera varias soluciones posibles para este problema con razonamiento paso a paso:

{problema}

Selecciona la más coherente y eficiente, y proporciona el código final.

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
Genera varias soluciones para ordenar una lista sin usar sort().

Selecciona la más eficiente y proporciona el código.

```

**Boosting tip:** Pide explícitamente comparación y selección final.  

**Cuándo usar:** Cuando quieres validar la mejor opción.

---

## **7. Generated Knowledge Prompting**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Primero, genera una explicación breve sobre: {concepto}.

Luego, aplica ese conocimiento para resolver: {problema}.

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
Primero, explica qué es memoization.

Luego, implementa una función que calcule el n-ésimo número de Fibonacci usando memoization.

```

**Boosting tip:** Separa conocimiento previo y aplicación en dos fases.  

**Cuándo usar:** Para aprender conceptos antes de implementarlos.

---

## **8. Tree of Thoughts (ToT)**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Explora diferentes enfoques para resolver: {problema}.

Analiza pros y contras de cada uno.
Selecciona el mejor y proporciona su implementación.

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Node.js.
Explora diferentes maneras de manejar autenticación JWT.

Analiza pros y contras y elige la mejor opción.

```

**Boosting tip:** Solicita análisis comparativo antes del código.  

**Cuándo usar:** Problemas con múltiples estrategias posibles.

---

## **9. Directional Stimulus Prompting**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Resuelve el siguiente problema enfocándote en {criterios clave}:

{problema}

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
Resuelve el problema enfocándote en minimizar el uso de memoria:

Procesar un archivo CSV de 10 GB línea por línea.

```

**Boosting tip:** Usa palabras clave para forzar el enfoque.  

**Cuándo usar:** Cuando tienes requisitos técnicos estrictos.

---

## **10. Program-Aided Language Models (PAL)**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Resuelve este problema combinando explicación y código:

{problema}

Proporciona el código y explica cada paso.

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
Calcula la suma de los números del 1 al 100 usando comprensión de listas.

```

**Boosting tip:** Útil para problemas matemáticos o de lógica con código.  

**Cuándo usar:** Algoritmos que requieran detalle y justificación.

---

## **11. ReAct**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Para resolver esta tarea, combina razonamiento y acciones iterativas:

{tarea}

Si necesitas más información o pasos intermedios, indícalo antes de continuar.

```

**Ejemplo:**
```

Actúa como un programador senior especializado en JavaScript.
Investiga la API de Fetch y proporciona un ejemplo que consuma datos de una API pública.

```

**Boosting tip:** Ideal para procesos que dependen de múltiples pasos y validaciones.  

**Cuándo usar:** Cuando la tarea requiere explorar y actuar secuencialmente.

---

## **12. Multimodal CoT**
**Template:**
```

Actúa como un programador senior especializado en {lenguaje}.
Analiza el siguiente código y diagrama paso a paso para detectar errores y corregirlos:

\[Código / imagen]

```

**Ejemplo:**
```

Actúa como un programador senior especializado en Python.
Analiza este código de función recursiva y el diagrama de flujo adjunto.

Paso 1:
Paso 2:

Código corregido:

```

**Boosting tip:** Útil cuando tienes código y material visual relacionado.  

**Cuándo usar:** Debugging con apoyo gráfico o documentación visual.

---


**Boosting:**  
- Útil para análisis combinados de código e imágenes (diagramas, arquitecturas).  
- Pide explicación detallada para entender mejor.

**Cuándo usar:**  
- Para debugging, análisis y aprendizaje visual.  
- Cuando hay componentes gráficos relacionados con el código.

---

¿Cuándo usar cada técnica y para qué casos funcionan mejor en programación?

| Técnica                 | Cuándo usar / Mejor para                                    | Ventajas y casos típicos                              |
|------------------------|-------------------------------------------------------------|-----------------------------------------------------|
| **Zero-Shot**          | Tareas estándar, snippets simples o preguntas directas      | Rápido, sin necesidad de ejemplos                    |
| **Few-Shot**           | Tareas específicas, formatos personalizados                 | Control de estilo y formato, tareas poco comunes     |
| **Chain-of-Thought**   | Algoritmos complejos, lógica paso a paso                     | Entender razonamiento, detectar errores              |
| **Zero-Shot CoT**      | Razonamiento sin ejemplos, problemas conocidos               | Razonamiento simple, sin necesidad de ejemplos       |
| **Role Prompting**     | Respuestas especializadas, perspectivas profesionales        | Precisión técnica, estilo adaptado                    |
| **Self-Consistency**   | Problemas con múltiples soluciones, validación               | Robustez y fiabilidad de resultados                   |
| **Generated Knowledge**| Conceptos nuevos o complejos antes de aplicar código         | Mejor comprensión, enseñanza                           |
| **Tree of Thoughts**   | Problemas con múltiples enfoques o estrategias                | Análisis y comparación de métodos                     |
| **Directional Stimulus**| Requisitos o restricciones específicas                        | Focaliza respuesta en criterios técnicos particulares |
| **PAL**                | Problemas con cálculo o algoritmos que requieren código y explicación | Aprendizaje profundo y detallado                       |
| **ReAct**              | Tareas con múltiples pasos, búsqueda o integración externa    | Dinámico, pensamiento-actuación                        |
| **Multimodal CoT**     | Análisis combinados de código e imágenes o diagramas          | Debugging, documentación, aprendizaje visual          |

---


## Guía Rápida de Técnicas de Prompting para Programadores

| Nº | Técnica                    | Plantilla con rol de programador                                                                                                                      | Cuándo usar                             | Boosting Tip                                         |
| -- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------- |
| 1  | **Zero-Shot**              | `Actúa como un programador senior especializado en {lenguaje}. Realiza la siguiente tarea: {descripción precisa}.`                                    | Tareas simples y estándar               | Especificar lenguaje, librerías y restricciones      |
| 2  | **Few-Shot**               | `Actúa como un programador senior especializado en {lenguaje}. Aquí tienes ejemplos: Entrada:... Salida:... Ahora hazlo para: {entrada}`              | Controlar el estilo y formato de salida | Usar ejemplos idénticos al formato esperado          |
| 3  | **Chain-of-Thought (CoT)** | `Actúa como un programador senior especializado en {lenguaje}. Explica paso a paso {problema} y luego da el código.`                                  | Algoritmos complejos o con varios pasos | Forzar explicación antes del código                  |
| 4  | **Zero-Shot CoT**          | `Actúa como un programador senior especializado en {lenguaje}. {problema} Pensemos paso a paso.`                                                      | Razonamiento sin ejemplos previos       | Incluir la frase “Pensemos paso a paso”              |
| 5  | **Role Prompting**         | `Actúa como {rol específico} experto en {tecnología}. {instrucción}`                                                                                  | Consultas técnicas de alto nivel        | Añadir experiencia y contexto                        |
| 6  | **Self-Consistency**       | `Actúa como un programador senior especializado en {lenguaje}. Genera varias soluciones para {problema}, selecciona la más eficiente y da el código.` | Cuando quieres validar la mejor opción  | Pedir comparación y selección final                  |
| 7  | **Generated Knowledge**    | `Actúa como un programador senior especializado en {lenguaje}. Primero explica {concepto}, luego resuelve {problema}.`                                | Aprender antes de implementar           | Separar explicación y ejecución                      |
| 8  | **Tree of Thoughts (ToT)** | `Actúa como un programador senior especializado en {lenguaje}. Explora enfoques para {problema}, analiza pros y contras y da el mejor con código.`    | Problemas con varias estrategias        | Pedir análisis comparativo antes del código          |
| 9  | **Directional Stimulus**   | `Actúa como un programador senior especializado en {lenguaje}. Resuelve {problema} enfocándote en {criterios clave}.`                                 | Requisitos técnicos estrictos           | Usar criterios claros como “rendimiento” o “memoria” |
| 10 | **PAL**                    | `Actúa como un programador senior especializado en {lenguaje}. Resuelve {problema} con explicación y código paso a paso.`                             | Algoritmos con detalle técnico          | Combinar teoría y práctica                           |
| 11 | **ReAct**                  | `Actúa como un programador senior especializado en {lenguaje}. Para resolver {tarea}, combina razonamiento y acciones iterativas.`                    | Procesos con validaciones múltiples     | Pedir pasos intermedios y verificación               |
| 12 | **Multimodal CoT**         | `Actúa como un programador senior especializado en {lenguaje}. Analiza el siguiente código/diagrama y corrige errores paso a paso.`                   | Debugging con apoyo visual              | Incluir materiales gráficos o diagramas              |

---

**Tip extra para uso diario:**
>! Si quieres que el modelo mantenga el rol en toda la conversación, arranca con:

``Perfecto, aquí te dejo la **tabla resumen** con **todas las técnicas**, sus **plantillas con rol de programador**, **cuándo usarlas** y **boosting tips** para que la tengas como guía rápida.

---

## 📋 Guía Rápida de Técnicas de Prompting para Programadores

| Nº | Técnica                    | Plantilla con rol de programador                                                                                                                      | Cuándo usar                             | Boosting Tip                                         |
| -- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------- |
| 1  | **Zero-Shot**              | `Actúa como un programador senior especializado en {lenguaje}. Realiza la siguiente tarea: {descripción precisa}.`                                    | Tareas simples y estándar               | Especificar lenguaje, librerías y restricciones      |
| 2  | **Few-Shot**               | `Actúa como un programador senior especializado en {lenguaje}. Aquí tienes ejemplos: Entrada:... Salida:... Ahora hazlo para: {entrada}`              | Controlar el estilo y formato de salida | Usar ejemplos idénticos al formato esperado          |
| 3  | **Chain-of-Thought (CoT)** | `Actúa como un programador senior especializado en {lenguaje}. Explica paso a paso {problema} y luego da el código.`                                  | Algoritmos complejos o con varios pasos | Forzar explicación antes del código                  |
| 4  | **Zero-Shot CoT**          | `Actúa como un programador senior especializado en {lenguaje}. {problema} Pensemos paso a paso.`                                                      | Razonamiento sin ejemplos previos       | Incluir la frase “Pensemos paso a paso”              |
| 5  | **Role Prompting**         | `Actúa como {rol específico} experto en {tecnología}. {instrucción}`                                                                                  | Consultas técnicas de alto nivel        | Añadir experiencia y contexto                        |
| 6  | **Self-Consistency**       | `Actúa como un programador senior especializado en {lenguaje}. Genera varias soluciones para {problema}, selecciona la más eficiente y da el código.` | Cuando quieres validar la mejor opción  | Pedir comparación y selección final                  |
| 7  | **Generated Knowledge**    | `Actúa como un programador senior especializado en {lenguaje}. Primero explica {concepto}, luego resuelve {problema}.`                                | Aprender antes de implementar           | Separar explicación y ejecución                      |
| 8  | **Tree of Thoughts (ToT)** | `Actúa como un programador senior especializado en {lenguaje}. Explora enfoques para {problema}, analiza pros y contras y da el mejor con código.`    | Problemas con varias estrategias        | Pedir análisis comparativo antes del código          |
| 9  | **Directional Stimulus**   | `Actúa como un programador senior especializado en {lenguaje}. Resuelve {problema} enfocándote en {criterios clave}.`                                 | Requisitos técnicos estrictos           | Usar criterios claros como “rendimiento” o “memoria” |
| 10 | **PAL**                    | `Actúa como un programador senior especializado en {lenguaje}. Resuelve {problema} con explicación y código paso a paso.`                             | Algoritmos con detalle técnico          | Combinar teoría y práctica                           |
| 11 | **ReAct**                  | `Actúa como un programador senior especializado en {lenguaje}. Para resolver {tarea}, combina razonamiento y acciones iterativas.`                    | Procesos con validaciones múltiples     | Pedir pasos intermedios y verificación               |
| 12 | **Multimodal CoT**         | `Actúa como un programador senior especializado en {lenguaje}. Analiza el siguiente código/diagrama y corrige errores paso a paso.`                   | Debugging con apoyo visual              | Incluir materiales gráficos o diagramas              |

---

**Tip extra para uso diario:**
*Si quieres que el modelo mantenga el rol en toda la conversación, arranca con:*

```txt
Durante toda esta conversación, actúa como un programador senior especializado en {lenguaje/tecnología}, respondiendo siempre con código limpio, buenas prácticas y explicaciones técnicas claras.
```


=== ROLE === 
Durante toda esta conversacion, adopta el rol de programador senior especializado en: R y Machine Learning

=== CONTEXTO ===
Vamos a presentar las clases de modelos de machine learning que podemos realizar por medio de R
Con librerias actuales : 2025
=== FIN CONTEXTO === 

=== TASKS ===
Generar una induccion de Modelos de regresion lineal con distintos algoritmos XGBOOST REGRESSOR, SVM(para regresion), linear regression, entre otras.
Mostrarme con los distintos pasos que se deben realizar como un template:
Pasos de ejemplo: 
 - Carga de la data
 - Muestra de las variables principales
 - EDA
 - Obtencion de hipotesis
 - Planteo de hipotesis nula
 - Insights obtenidos
 - Feature engineering
 - Outliers Detection and Treatment
 - Labeling Encoding
 - Missing Treatment
 - Capping
 - Data Splitting : Test, Validation & Train
 - Machine Learning Algorith and Selection
 - Cross Validation
 - AUC - ROCK (Cuando se use)
 - Metricas de validacion
 - Guardado de Modelo
=== FIN TASKS ===

=== OUTPUT FORMAT===
- No debe contener emojis
- Explicaciones claras
- No hace falta tener codigo pues estoy buscando generar una clase de modo template para la mayoria de los modelos de Machine Learning y resolucion de problemas de machine learning
- Debe ser solo para lenguaje R
- Debe estar escrito para markdown
=== END OUTPUT FORMAT===