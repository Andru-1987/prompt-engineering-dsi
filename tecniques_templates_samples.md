## 1. Zero-Shot Prompting

**Template:**

```
Realiza la siguiente tarea: {descripción de la tarea}  
Sin ejemplos previos, solo responde basado en tu conocimiento.
```

**Ejemplo aplicado:**

```
Realiza la siguiente tarea: Traduce la frase "Buenos días" al francés.  
Sin ejemplos previos, solo responde basado en tu conocimiento.
```

---

## 2. Few-Shot Prompting

**Template:**

```
Aquí hay algunos ejemplos de la tarea:  

Entrada: {ejemplo_entrada_1}  
Salida: {ejemplo_salida_1}  

Entrada: {ejemplo_entrada_2}  
Salida: {ejemplo_salida_2}  

Ahora, realiza la tarea para la siguiente entrada: {nueva_entrada}
```

**Ejemplo aplicado:**

```
Aquí hay algunos ejemplos de la tarea:  

Frase: "Estoy feliz"  
Sentimiento: Positivo  

Frase: "Esto es terrible"  
Sentimiento: Negativo  

Ahora, clasifica el sentimiento de esta frase: "No me gusta este lugar"
```

---

## 3. Chain-of-Thought (CoT) Prompting

**Template:**

```
Resuelve el siguiente problema mostrando paso a paso tu razonamiento:  

{problema}  

Paso 1:  
Paso 2:  
...  

Respuesta final:
```

**Ejemplo aplicado:**

```
Resuelve el siguiente problema mostrando paso a paso tu razonamiento:  

Si compro 5 manzanas, luego regalo 2, ¿cuántas me quedan?  

Paso 1:  
Paso 2:  

Respuesta final:
```

---

## 4. Zero-Shot Chain-of-Thought (Zero-Shot CoT)

**Template:**

```
{pregunta o problema} Pensemos paso a paso.
```

**Ejemplo aplicado:**

```
¿Cuántos días hay en 3 semanas? Pensemos paso a paso.
```

---

## 5. Role Prompting

**Template:**

```
Actúa como un {rol específico}. {instrucción o pregunta específica}.
```

**Ejemplo aplicado:**

```
Actúa como un profesor de matemáticas. Explica qué es un número primo.
```

---

## 6. Self-Consistency

**Template:**

```
Genera varias respuestas para esta pregunta usando razonamiento paso a paso:  

{pregunta}  

Luego, selecciona la respuesta que aparece con mayor consistencia.
```

**Ejemplo aplicado:**

```
Genera varias respuestas para esta pregunta usando razonamiento paso a paso:  

¿Cuánto es 15 x 12?  

Luego, selecciona la respuesta que aparece con mayor consistencia.
```

---

## 7. Generated Knowledge Prompting

**Template:**

```
Primero, genera conocimiento relevante sobre: {tema o pregunta}  

Luego, usando ese conocimiento, responde la siguiente pregunta: {pregunta}.
```

**Ejemplo aplicado:**

```
Primero, genera conocimiento relevante sobre los síntomas comunes de la gripe.  

Luego, usando ese conocimiento, responde: ¿Cuáles son los síntomas que debería vigilar?
```

---

## 8. Tree of Thoughts (ToT)

**Template:**

```
Explora múltiples caminos de razonamiento para resolver: {problema}  

Para cada camino, detalla los pasos y posibles resultados.  

Selecciona la mejor solución considerando todas las opciones.
```

**Ejemplo aplicado:**

```
Explora múltiples caminos de razonamiento para decidir el mejor método para aprender un idioma en 3 meses.  

Para cada camino, detalla los pasos y posibles resultados.  

Selecciona la mejor solución considerando todas las opciones.
```

---

## 9. Directional Stimulus Prompting

**Template:**

```
Responde la siguiente pregunta enfocándote en {palabras clave o conceptos}:  

{pregunta}
```

**Ejemplo aplicado:**

```
Responde la siguiente pregunta enfocándote en eficiencia energética y ahorro de costos:  

¿Cómo puedo reducir el consumo eléctrico en mi hogar?
```

---

## 10. Program-Aided Language Models (PAL)

**Template:**

```
Resuelve el siguiente problema combinando razonamiento natural con código:  

{problema}  

Escribe el código necesario para calcular la respuesta y explica cada paso.
```

**Ejemplo aplicado:**

```
Resuelve el siguiente problema combinando razonamiento natural con código:  

Calcula la suma de los primeros 100 números enteros.  

Escribe el código necesario para calcular la respuesta y explica cada paso.
```

---

## 11. ReAct (Reasoning + Acting)

**Template:**

```
Para resolver esta tarea, combina pensamiento y acción:  

{tarea}  

Si necesitas información adicional, indícala y luego actúa en consecuencia.
```

**Ejemplo aplicado:**

```
Para resolver esta tarea, combina pensamiento y acción:  

Encuentra la capital del país con mayor población del mundo.  

Si necesitas información adicional, indícala y luego actúa en consecuencia.
```

---

## 12. Multimodal CoT

**Template:**

```
Analiza la siguiente imagen y texto, y razona paso a paso para responder:  

[Imagen: {descripción o link}]  
Texto: {texto relacionado}  

Paso 1:  
Paso 2:  
...  

Respuesta final:
```

**Ejemplo aplicado:**

```
Analiza la siguiente imagen y texto, y razona paso a paso para responder:  

[Imagen: gráfico de barras que muestra ventas por mes]  
Texto: Las ventas aumentaron en diciembre.  

Paso 1:  
Paso 2:  

Respuesta final:
```
