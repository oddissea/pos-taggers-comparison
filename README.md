# Comparativa de Etiquetadores Estadísticos

Este repositorio contiene el código y los resultados de un análisis comparativo entre los etiquetadores morfosintácticos Stanza y spaCy, evaluando su rendimiento en la tarea de Part-of-Speech (POS) tagging sobre un corpus del Universal Dependencies English EWT.

## Descripción

El etiquetado de categorías gramaticales (POS tagging) constituye una tarea fundamental en el procesamiento del lenguaje natural. Este proyecto evalúa sistemáticamente el rendimiento de dos etiquetadores estadísticos modernos:

- **Stanza**: Implementa un etiquetador morfosintáctico basado en una red LSTM bidireccional con mecanismo de puntuación biafín.
- **spaCy**: Utiliza un enfoque basado en redes neuronales convolucionales y transformers optimizados para eficiencia.

El análisis se centra en la capacidad de ambos sistemas para manejar casos de ambigüedad léxica y categorías gramaticales complejas en inglés.

## Estructura del Repositorio

```
.
├── data/
│   ├── texto_ud.txt                # Texto original de evaluación
│   ├── texto_ud_gold.txt           # Etiquetado de referencia (gold standard)
│   ├── texto_stanza.txt            # Salida del etiquetador Stanza
│   └── texto_spacy.txt             # Salida del etiquetador spaCy
├── results/
│   ├── resultados.csv              # Resultados comparativos detallados
│   ├── stanza_metrics.csv          # Métricas de rendimiento de Stanza
│   ├── spacy_metrics.csv           # Métricas de rendimiento de spaCy
│   ├── accuracy_comparison.png     # Comparación visual de precisión
│   ├── tag_distribution.png        # Distribución de etiquetas
│   ├── confusion_matrix_stanza.png # Matriz de confusión de Stanza
│   └── confusion_matrix_spacy.png  # Matriz de confusión de spaCy
├── notebooks/
│   ├── comparativa_etiquetadores.ipynb # Pipeline principal de evaluación
│   └── analisis_resultados.ipynb      # Análisis detallado de resultados
├── src/
│   └── tagger_evaluator.py         # Clase principal para evaluación
├── requirements.txt                # Dependencias del proyecto
└── README.md                       # Este archivo
```

## Metodología

El proceso de evaluación comprende los siguientes pasos:

1. **Extracción y preparación de datos**: Selección de un fragmento de 299 tokens del corpus UD English EWT.
2. **Alineamiento de tokens**: Implementación de un sistema basado en SequenceMatcher para manejar discrepancias en la tokenización.
3. **Etiquetado**: Procesamiento del texto mediante Stanza (modelo en_ewt) y spaCy (modelo en_core_web_sm).
4. **Evaluación cuantitativa**:
   - Cálculo de exactitud global
   - Análisis de precisión por categoría gramatical
   - Generación de matrices de confusión
   - Identificación de patrones de error

## Resultados Principales

1. **Precisión global**:
   - Stanza: 98.99%
   - spaCy: 97.31%

2. **Análisis por categorías**:
   - Stanza presenta dificultades con adjetivos (92.31%)
   - spaCy muestra debilidad en nombres propios y plurales (94.44%)
   - Ambos sistemas etiquetan correctamente casos de ambigüedad léxica cuando disponen de contexto suficiente

3. **Patrones de error**:
   - Confusión entre participios y adjetivos
   - Dificultades en contracciones negativas
   - Tratamiento variable de nombres propios compuestos

## Requisitos

```
stanza==1.0.0
spacy==2.2.0
pandas==1.3.5
numpy==1.21.5
matplotlib==3.5.1
seaborn==0.11.2
jupyter==1.0.0
```

Para instalar las dependencias:

```bash
pip install -r requirements.txt
python -m spacy download en_core_web_sm
```

## Uso

1. Para ejecutar la evaluación completa:

```bash
jupyter notebook notebooks/comparativa_etiquetadores.ipynb
```

2. Para analizar los resultados detallados:

```bash
jupyter notebook notebooks/analisis_resultados.ipynb
```

## Citar este trabajo

Si utilizas este código o resultados en tu investigación, por favor cita este repositorio:

```
@misc{nasser-eddine2025postaggers,
  author = {Nasser-Eddine López, Fernando H.},
  title = {Comparativa de Etiquetadores Estadísticos},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/oddissea/pos-taggers-comparison}
}
```

## Licencia

Este proyecto está licenciado bajo los términos de la licencia MIT.