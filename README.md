[PRMPTING TECHNIQUES](https://www.promptingguide.ai/techniques)

# Técnicas de Prompt Engineering - Resumen Completo

## 1. **Zero-Shot Prompting**
Zero-shot prompting means that the prompt used to interact with the model won't contain examples or demonstrations. The zero-shot prompt directly instructs the model to perform a task without any additional examples to steer it.

**Características:**
- No requiere ejemplos previos
- Se basa únicamente en el conocimiento preentrenado del modelo
- Instrucciones directas para realizar una tarea
- Efectivo para tareas que el modelo ya conoce de su entrenamiento

**Ejemplo:**
```
Traduce la siguiente frase al inglés: "Hola, ¿cómo estás?"
```

## 2. **Few-Shot Prompting**
Few-shot prompting can be used as a technique to enable in-context learning where we provide demonstrations in the prompt to steer the model to better performance. The demonstrations serve as conditioning for subsequent examples where we would like the model to generate a response.

**Características:**
- Incluye ejemplos de entrada y salida esperada
- Permite aprendizaje en contexto (in-context learning)
- Mejor rendimiento en tareas complejas
- Los ejemplos sirven como guía para el modelo

**Ejemplo:**
```
Clasifica el sentimiento de estas frases:

Frase: "Me encanta este producto"
Sentimiento: Positivo

Frase: "Odio esperar tanto tiempo"
Sentimiento: Negativo

Frase: "La película estuvo increíble"
Sentimiento: ?
```

## 3. **Chain-of-Thought (CoT) Prompting**
Chain-of-thought (CoT) prompting enables complex reasoning capabilities through intermediate reasoning steps. You can combine it with few-shot prompting to get better results on more complex tasks that require reasoning before responding.

**Características:**
- Descompone problemas complejos en pasos de razonamiento
- Muestra el proceso de pensamiento paso a paso
- Mejora significativamente el rendimiento en tareas de razonamiento
- Puede combinarse con few-shot prompting

**Ejemplo:**
```
Resuelve: Si tengo 23 manzanas y regalo 8, luego compro 15 más, ¿cuántas tengo?

Paso 1: Empiezo con 23 manzanas
Paso 2: Regalo 8, me quedan 23 - 8 = 15 manzanas
Paso 3: Compro 15 más, ahora tengo 15 + 15 = 30 manzanas
Respuesta: 30 manzanas
```

## 4. **Zero-Shot Chain-of-Thought**
In Zero-Shot CoT, however, we do not have to include input exemplars of Chain-of-Thought responses, but rather just append the words "Let's think step by step" to the end of an input.

**Características:**
- Combina zero-shot con razonamiento paso a paso
- Utiliza frases activadoras como "Pensemos paso a paso"
- Zero-Shot CoT was most effective in tasks that involve arithmetic, commonsense reasoning, and symbolic reasoning
- No requiere ejemplos previos

**Ejemplo:**
```
¿Cuál es la raíz cuadrada de 144? Pensemos paso a paso.
```

## 5. **Role Prompting (Prompting por Roles)**
**Características:**
- Asigna un rol específico al modelo (experto, profesional, etc.)
- Mejora la calidad y relevancia de las respuestas
- Proporciona contexto sobre el tipo de respuesta esperada
- Útil para obtener perspectivas especializadas

**Ejemplo:**
```
Actúa como un médico experimentado. ¿Cuáles son los síntomas más comunes de la gripe?
```

## 6. **Self-Consistency**
**Características:**
- Genera múltiples respuestas usando CoT
- Selecciona la respuesta más consistente
- Mejora la confiabilidad de las respuestas
- Especialmente útil para problemas de razonamiento

## 7. **Generated Knowledge Prompting**
**Características:**
- Solicita al modelo que genere conocimiento relevante primero
- Luego utiliza ese conocimiento para responder la pregunta
- Mejora el rendimiento en tareas que requieren conocimiento específico
- Proceso de dos pasos: generar conocimiento + aplicarlo

## 8. **Tree of Thoughts (ToT)**
**Características:**
- Explora múltiples caminos de razonamiento
- Estructura el pensamiento como un árbol de decisiones
- Permite backtracking y exploración de alternativas
- Útil para problemas complejos con múltiples soluciones

## 9. **Directional Stimulus Prompting**
**Características:**
- Proporciona pistas direccionales para guiar la respuesta
- Incluye palabras clave o conceptos relevantes
- Ayuda a enfocar la atención del modelo
- Mejora la precisión en tareas específicas

## 10. **Program-Aided Language Models (PAL)**
**Características:**
- Combina razonamiento en lenguaje natural con código
- Utiliza programación para resolver partes del problema
- Especialmente útil para matemáticas y lógica
- Mejora la precisión en cálculos complejos

## 11. **ReAct (Reasoning + Acting)**
**Características:**
- Combina razonamiento con acciones
- Permite interacción con herramientas externas
- Útil para tareas que requieren búsqueda de información
- Ciclo continuo de pensamiento y acción

## 12. **Multimodal CoT**
**Características:**
- Extiende Chain-of-Thought a múltiples modalidades
- Integra texto, imágenes y otros tipos de datos
- Razonamiento paso a paso con información visual
- Útil para tareas que requieren comprensión visual

## Técnicas Adicionales de Optimización

### **Prompt Crafting (Elaboración de Prompts)**
- Claridad y especificidad en las instrucciones
- Uso de formato estructurado
- Inclusión de restricciones y requisitos
- Definición del formato de salida deseado

### **Template-Based Prompting**
- Uso de plantillas reutilizables
- Estructuras predefinidas para diferentes tipos de tareas
- Consistencia en la formulación de prompts
- Facilita la escalabilidad

### **Iterative Prompting**
- Refinamiento gradual de prompts
- Mejora continua basada en resultados
- Testing A/B de diferentes versiones
- Optimización basada en métricas

### **Context Window Management**
- Optimización del uso del contexto disponible
- Priorización de información relevante
- Técnicas de compresión de información
- Manejo eficiente de conversaciones largas

## Mejores Prácticas Generales

1. **Ser específico y claro** en las instrucciones
2. **Proporcionar contexto** suficiente sin ser redundante
3. **Usar ejemplos** cuando sea necesario (few-shot)
4. **Estructurar** las respuestas con formatos claros
5. **Iterar y refinar** los prompts basándose en los resultados
6. **Considerar el dominio** y la complejidad de la tarea
7. **Combinar técnicas** según sea apropiado
8. **Evaluar consistencia** y confiabilidad de las respuestas

## Cuándo Usar Cada Técnica

- **Zero-Shot**: Tareas simples que el modelo ya conoce
- **Few-Shot**: Tareas nuevas o que requieren formato específico
- **CoT**: Problemas de razonamiento complejo
- **Zero-Shot CoT**: Razonamiento sin ejemplos previos
- **Role Prompting**: Cuando se necesita expertise específico
- **ReAct**: Tareas que requieren herramientas externas
- **ToT**: Problemas con múltiples soluciones posibles


*Biliografia*
[Ultimate Guide for Prompt Engineering](https://github.com/dair-ai/Prompt-Engineering-Guide.git)