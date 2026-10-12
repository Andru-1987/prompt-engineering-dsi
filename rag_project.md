# Proyecto RAG Local - Plan Completo de Implementación

## 📊 Análisis de Sistema
### Hardware Identificado
- **CPU**: Intel Core i5-2435M @ 2.40GHz (4 cores, 2 threads por core)
- **RAM**: 7.7GB total (3.6GB disponible actualmente)
- **GPU**: Intel HD Graphics 3000 (integrada, sin VRAM dedicada)
- **Almacenamiento**: 218GB total (158GB libre)
- **Sistema**: Debian 12 (Bookworm)

### Limitaciones y Consideraciones
- ❌ Sin GPU dedicada para LLMs
- ⚠️ RAM limitada para modelos grandes
- ✅ CPU adecuada para procesamiento
- ✅ Almacenamiento suficiente para documentos y modelos

## 🎯 Stack Tecnológico Recomendado
```
Stack Optimizado para Sistema:
├── LLM: Ollama con Phi-3 Mini (3.8B parameters)
├── Embeddings: Sentence-Transformers (all-MiniLM-L6-v2)
├── Vector DB: ChromaDB (ligero y persistente)
├── Framework: LangChain con optimización CPU
├── Interfaz: Streamlit (simple y local)
└── Compresión: Context compression agresiva
```

## 🚀 Plan de Implementación por Fases

### Fase 1: Setup Básico (Semana 1)
#### Instalación de Dependencias
```bash
# Environment setup
python -m venv rag-env
source rag-env/bin/activate
pip install --upgrade pip

# Core dependencies
pip install langchain chromadb sentence-transformers
pip install ollama streamlit numpy pandas PyPDF2

# Model download
ollama pull phi-3-mini
```

#### Configuración Inicial
- Descargar Phi-3 Mini (~2GB RAM)
- Configurar ChromaDB básico
- Procesar 5-10 PDFs de prueba
- Crear pipeline LangChain simple

### Fase 2: Optimización (Semana 2)
#### Parámetros Optimizados
```yaml
models:
  primary: "phi-3-mini"
  alternatives: ["qwen2.5-1.5b", "tinyllama-1.1b"]
  embeddings: "all-MiniLM-L6-v2"

optimization:
  chunk_size: 400
  chunk_overlap: 50
  top_k: 3
  max_tokens: 2048
  batch_size: 1
```

#### Estrategias de Optimización
- Memory management con `torch.no_grad()`
- Context compression agresiva
- Batch processing pequeño
- Cache inteligente de embeddings

### Fase 3: Mejoras Avanzadas (Semana 3)
#### Features Adicionales
- Hybrid search (semántico + keywords)
- Re-ranking ligero con cross-encoders
- Memoria conversacional
- Interfaz Streamlit completa

## 🛠️ Arquitectura LangChain Detallada

### Pipeline Completo
```python
# Estructura optimizada para CPU
Document Loaders → PDFs técnicos
    ↓
Text Splitters → RecursiveCharacter (400 tokens, 50 overlap)
    ↓
Embeddings → HuggingFace (CPU mode, all-MiniLM-L6-v2)
    ↓
Vector Store → ChromaDB (persistente)
    ↓
Retriever → ContextualCompression
    ↓
LLM → Ollama (Phi-3 Mini)
    ↓
Chain → ConversationalRetrieval
```

### Componentes Clave
1. **Document Processing**: PDFs técnicos sobre manejo de datos
2. **Chunking Strategy**: 400 tokens con 50 overlap
3. **Embedding Model**: all-MiniLM-L6-v2 (CPU-friendly)
4. **Retrieval**: Top-k=3 con context compression
5. **Generation**: Phi-3 Mini con prompts especializados

## ⚡ Estrategias de Optimización de Recursos

### Memory Management
- Usar `torch.no_grad()` para inferencia
- Limpiar caché entre consultas
- Batch size pequeño (1-2 documentos)
- Offloading a disco cuando sea posible

### Model Optimization
- Cuantización 8-bit para reducir RAM
- Pruning de embeddings si es necesario
- Dynamic batching según carga del sistema

### Retrieval Optimization
- Hybrid search: semántico + keywords
- Re-ranking ligero con cross-encoders
- Dynamic top-k según complejidad de consulta

## 📋 Modelos Recomendados para tu Hardware

### Opción Principal: Phi-3 Mini
- **Parámetros**: 3.8B
- **RAM requerida**: ~2GB
- **Ventajas**: Excelente para español, buen razonamiento técnico

### Alternativas
1. **Qwen2.5-1.5B** - ~1GB RAM, muy eficiente
2. **TinyLlama-1.1B** - ~800MB RAM, rápido pero básico
3. **Gemma-2B** - ~1.5GB RAM, buen balance calidad/recursos

## 🔧 Comandos y Configuración

### Instalación Completa
```bash
# 1. Crear entorno virtual
python -m venv rag-project
cd rag-project
source bin/activate

# 2. Instalar dependencias principales
pip install langchain==0.1.0
pip install chromadb==0.4.22
pip install sentence-transformers==2.2.2
pip install ollama==0.1.7
pip install streamlit==1.29.0
pip install PyPDF2==3.0.1
pip install numpy==1.24.3
pip install pandas==2.0.3

# 3. Descargar modelo
ollama pull phi-3-mini

# 4. Verificar instalación
ollama list
python -c "import langchain, chromadb; print('Dependencies OK')"
```

### Configuración de Variables de Entorno
```bash
# Opcional: para optimización
export OLLAMA_HOST=127.0.0.1:11434
export CHROMA_SERVER_HOST=127.0.0.1
export CHROMA_SERVER_HTTP_PORT=8000
```

## 📊 Métricas de Evaluación

### Benchmarks a Medir
- **Tiempo de respuesta**: < 30 segundos objetivo
- **Uso de RAM**: < 4GB durante operación
- **Precisión de retrieval**: > 80% relevancia
- **Calidad de respuestas**: Evaluación cualitativa

### Testing Strategy
1. **Dataset de prueba**: 10 PDFs técnicos conocidos
2. **Queries de prueba**: 20 preguntas variadas
3. **Evaluación manual**: Calidad y precisión
4. **Métricas automáticas**: Tiempo y recursos

## 🚨 Troubleshooting Común

### Problemas Frecuentes
1. **RAM insuficiente**: Reducir chunk_size o usar modelo más pequeño
2. **Tiempo de respuesta lento**: Optimizar retrieval o reducir top_k
3. **Calidad baja**: Ajustar prompts o usar reranking
4. **Crashes**: Implementar memory management agresivo

### Solutions Quick Reference
```bash
# Si hay problemas de RAM
export PYTORCH_CUDA_ALLOC_CONF=max_split_size_mb:128

# Para limpiar caché
python -c "import torch; torch.cuda.empty_cache()"

# Para debugging
export LANGCHAIN_VERBOSE=true
export LANGCHAIN_DEBUG=true
```

## 🎯 Próximos Pasos

### Checklist de Implementación
- [ ] Crear entorno virtual Python
- [ ] Instalar todas las dependencias
- [ ] Descargar Phi-3 Mini vía Ollama
- [ ] Preparar dataset de PDFs técnicos
- [ ] Implementar pipeline LangChain básico
- [ ] Procesar documentos de prueba
- [ ] Crear interfaz Streamlit simple
- [ ] Optimizar parámetros según rendimiento
- [ ] Implementar features avanzadas
- [ ] Documentar resultados finales

### Decisiones Pendientes
1. **Cantidad de PDFs**: Definir volumen inicial de documentos
2. **Nivel técnico**: Complejidad de los documentos técnicos
3. **Frecuencia de uso**: Uso ocasional vs intensivo
4. **Tiempo de respuesta**: Límite aceptable para consultas

## 📚 Recursos Adicionales

### Documentación Oficial
- [LangChain Documentation](https://python.langchain.com/docs/)
- [Ollama Documentation](https://ollama.ai/documentation)
- [ChromaDB Documentation](https://docs.trychroma.com/)

### Tutoriales Recomendados
- RAG systems with LangChain
- Local LLM optimization
- CPU-only inference strategies

---

**Fecha de creación**: 2025-01-05
**Sistema**: Debian 12 (Bookworm)
**Hardware**: Intel i5-2435M, 7.7GB RAM
**Estado**: Plan completo listo para implementación
