# Semantic Similarity Analysis of Theses Using  Sentence Embeddings and Knowledge Graph

## Overview

This project performs a **semantic similarity analysis of university theses** using **sentence embeddings** and **knowledge graphs**.  
It aims to identify conceptual relationships between academic works, visualize thematic clusters, and support academic research by leveraging **natural language processing (NLP)** and **graph-based knowledge representation**.

The study uses data extracted from **UNSAAC’s digital thesis repository**, embedding models like **BETO**, and **Neo4j** for graph storage and exploration.

---

## Objectives

- **Automate** the collection of theses metadata (titles, abstracts, faculties, etc.).
- **Preprocess and clean** the textual content to remove noise.
- **Generate semantic embeddings** using a multilingual transformer model.
- **Measure similarity** among theses to identify conceptual proximity.
- **Cluster** thematically related documents using dimensionality reduction and unsupervised methods.
- **Visualize** results and **represent** semantic relationships in a **knowledge graph**.

---

## Methodology

The project follows a modular pipeline divided into six main stages:

| Stage | Description | Main File |
|--------|--------------|-----------|
| 1 **Data Collection** | Scrapes metadata and abstracts from UNSAAC’s repository. | `src/recolector_tesis.py` |
| 2️ **Data Cleaning & Filtering** | Removes duplicates, incomplete records, and normalizes text. | `src/limpieza_filtrado.py` |
| 3️ **Embedding Generation** | Encodes abstracts using **Sentence-Transformers** (`BETO`, `all-MiniLM`, etc.). | `src/generar_embeddings.py` |
| 4️ **Dimensionality Reduction** | Applies **UMAP** to visualize embeddings in 2D/3D space. | `src/reducir_dimensiones.py` |
| 5️ **Similarity Computation & Clustering** | Calculates cosine similarity and groups related theses using **HDBSCAN**. | `src/calcular_similitudes.py` |
| 6️ **Visualization & Knowledge Graph** | Exports and visualizes relationships in **Neo4j**. | `src/visualizacion.py`, `src/carga_neo4j.py` |

---

## Technologies Used

| Category | Tools / Libraries |
|-----------|------------------|
| **Programming Language** | Python 3.10+ |
| **Data Handling** | `pandas`, `numpy`, `dask` |
| **Web Scraping** | `requests`, `beautifulsoup4` |
| **Embeddings** | `sentence-transformers`, `torch` |
| **Dimensionality Reduction** | `umap-learn`, `scikit-learn` |
| **Clustering & Similarity** | `hdbscan`, `scikit-learn`, `numpy` |
| **Visualization** | `matplotlib`, `seaborn`, `plotly` |
| **Knowledge Graph** | `neo4j` |
| **Storage / I/O** | `pyarrow`, `parquet` |

---

## Project Structure

```

tesis-semantic-similarity/
├── data/                     # Raw and filtered data (not versioned)
├── docs/                     # Documentation and figures
├── notebooks/                # Jupyter notebooks (experiments)
├── src/                      # Modular Python scripts
│   ├── recolector_tesis.py
│   ├── limpieza_filtrado.py
│   ├── generar_embeddings.py
│   ├── reducir_dimensiones.py
│   ├── calcular_similitudes.py
│   ├── visualizacion.py
│   └── carga_neo4j.py
├── results/                  # Processed CSVs, plots, reports
├── embeddings_output/         # Embeddings and similarity matrices
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md

````

---

##  Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/tesis-semantic-similarity.git
cd tesis-semantic-similarity
````

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate   # (Linux/macOS)
venv\Scripts\activate      # (Windows)
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Usage

### 1️ Recollect thesis data

```bash
python src/recolector_tesis.py
```

### 2️ Clean and filter dataset

```bash
python src/limpieza_filtrado.py
```

### 3️ Generate embeddings

```bash
python src/generar_embeddings.py
```

### 4️ Reduce dimensions for visualization

```bash
python src/reducir_dimensiones.py
```

### 5️ Compute semantic similarity and cluster

```bash
python src/calcular_similitudes.py
```

### 6️ Load results into Neo4j

```bash
python src/carga_neo4j.py
```

---

## Example Results

| Visualization               | Description                                               |
| --------------------------- | --------------------------------------------------------- |
| **UMAP 2D Plot**            | Theses clustered by thematic similarity.                  |
| **Similarity Matrix**       | Cosine similarity among abstracts.                        |
| **Knowledge Graph (Neo4j)** | Nodes = Theses, Edges = Semantic relations (> threshold). |

Figures and reports are stored in `docs/figures/` or `results/`.

---

## Neo4j Integration

To visualize semantic relationships in a graph form:

1. Start Neo4j Desktop or AuraDB instance.
2. Update connection credentials in `src/carga_neo4j.py`:

   ```python
   URI = "bolt://localhost:7687"
   USER = "neo4j"
   PASSWORD = "yourpassword"
   ```
3. Run:

   ```bash
   python src/carga_neo4j.py
   ```
4. Explore relationships using:

   ```cypher
   MATCH (t:Thesis)-[r:SIMILAR_TO]->(t2:Thesis)
   RETURN t.title, t2.title, r.similarity
   ```

---

## Requirements

See [`requirements.txt`](requirements.txt) for the full list of dependencies.

Main packages include:

* `sentence-transformers`
* `torch`
* `pandas`
* `umap-learn`
* `hdbscan`
* `neo4j`

---

## Performance Notes

* Embedding generation is GPU-accelerated (recommended: CUDA device).
* For large datasets, use **Dask** for distributed DataFrame operations.
* For lightweight experimentation, reduce dataset size or embedding dimensions.

---

## References

* Reimers, N., & Gurevych, I. (2019). *Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks.*
* Neo4j. (2024). *Graph Data Science Library.*
* UNSAAC Repository: [https://repositorio.unsaac.edu.pe](https://repositorio.unsaac.edu.pe)

---

##  Author

** [Your Last Name]**
Faculty of Engineering — UNSAAC
2025

If you use this project or adapt it for research, please cite or mention this repository.

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

* UNSAAC Institutional Repository for data access.
* HuggingFace `sentence-transformers` community.
* Neo4j and UMAP open-source developers.

---

## Future Work

* Integrate automatic topic labeling via LDA or BERTopic.
* Expand dataset to include theses from multiple universities.
* Develop a web interface for exploring semantic graphs interactively.

---

## Citation

If you use this project for academic purposes, please cite as:


LAAD. (2025). Semantic Similarity Analysis of Theses Using Sentence Embeddings and Knowledge Graphs. GitHub Repository. https://github.com/<your-username>/tesis-semantic-similarity


```

---
