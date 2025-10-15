# Semantic Similarity Analysis of Theses Using  Sentence Embeddings and Knowledge Graph

### Universidad Nacional de San Antonio Abad del Cusco (UNSAAC)  
**Proyecto de investigación:** Recolección, limpieza, análisis semántico y graficado de tesis mediante *Sentence Embeddings* y *Knowledge Graphs*  
**Autores:**   
**Año:** 2025

---

## Descripción General

Este proyecto implementa un **pipeline automatizado** para recolectar, procesar y analizar tesis publicadas en el [Repositorio Institucional de la UNSAAC](https://repositorio.unsaac.edu.pe/).  
Mediante el uso de técnicas de **Procesamiento del Lenguaje Natural (NLP)**, se calcula la **similitud semántica entre tesis** y se construye un **grafo de conocimiento (Knowledge Graph)** en **Neo4j** para representar relaciones entre Facultades, Escuelas y documentos académicos.

El flujo completo se compone de cinco etapas principales:

1. **Recolección automatizada de tesis (Web Scraping)**  
2. **Limpieza y filtrado de datos**
3. **Generación de embeddings semánticos (BERT, BETO, RoBERTa, SciBERT, etc.)**
4. **Visualización y reducción de dimensionalidad (UMAP, Heatmaps)**
5. **Creación del grafo en Neo4j AuraDB**

---

## Tecnologías utilizadas

- **Python 3.10+**
- **Google Colab / Jupyter**
- **BeautifulSoup4**, **Requests**, **Pandas**, **NumPy**
- **SentenceTransformers (HuggingFace)**
- **UMAP**, **Matplotlib**, **Plotly**
- **Neo4j AuraDB**
- **Torch (CUDA compatible)**

---

## 1 Recolección de Datos

El proceso de scraping recorre todas las páginas del repositorio UNSAAC, extrae enlaces individuales y obtiene:

- Título  
- Facultad  
- Escuela  
- Año  
- Resumen  
- Palabras clave  
- Enlace al PDF  

El script almacena cada registro en una clase `DatosTesis` y genera un archivo CSV:

```bash
tesis_unsaac.csv
