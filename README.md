# Imágenes como datos visuales · Notebooks del Tema 3

**Algoritmos y Arquitecturas para Procesado de Imágenes (AAPI)**
Grado en Ciencia de Datos e Inteligencia Artificial · Universidad Politécnica de Madrid

Notebooks de apoyo al **Tema 3: Imágenes como datos visuales** (extracción de características, anotación semántica, indexado y recuperación de imágenes) y a los proyectos en pareja del tema. Están  pensados para **Google Colab** y salvo las partes de redes neuronales funcionan sin GPU y sin descargar datos: usan las imágenes de ejemplo de `scikit-image` y `scikit-learn`.

---

## Notebooks

| | Notebook | Temario | Qué se aprende | Abrir |
|---|---|---|---|---|
| 1 | [`T3_1_caracteristicas_clasicas.ipynb`](notebooks/T3_1_caracteristicas_clasicas.ipynb) | 3.1 | Histogramas y momentos de color, espacios de color (HSV, L\*a\*b\*), forma (área, perímetro, compacidad), GLCM y Haralick a mano, entropía local, LBP, HOG, SIFT y ORB, bolsa de palabras visuales | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/upm-classes/AAPI_2026/blob/main/notebooks/T3_1_caracteristicas_clasicas.ipynb) |
| 2 | [`T3_2_caracteristicas_profundas.ipynb`](notebooks/T3_2_caracteristicas_profundas.ipynb) | 3.1 | Convolución y *pooling* a mano, ResNet-18 preentrenada como extractor de características, comparación píxeles / HOG / embeddings, mapas de activación, t-SNE, CLIP: búsqueda por texto y clasificación *zero-shot* | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/upm-classes/AAPI_2026/blob/main/notebooks/T3_2_caracteristicas_profundas.ipynb) |
| 3 | [`T3_3_anotacion_semantica.ipynb`](notebooks/T3_3_anotacion_semantica.ipynb) | 3.2 | Niveles de anotación, formatos COCO / YOLO / Pascal VOC, κ de Cohen, anotación automática con clasificadores, F1 macro y micro, multietiqueta, IoU, NMS y precisión media (AP), humanos contra CLIP | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/upm-classes/AAPI_2026/blob/main/notebooks/T3_3_anotacion_semantica.ipynb) |
| 4 | [`T3_4_indexado_recuperacion.ipynb`](notebooks/T3_4_indexado_recuperacion.ipynb) | 3.3 | Medidas de similitud, maldición de la dimensionalidad, árbol k-d frente a fuerza bruta, P@k, AP y mAP, índice IVF desde cero, FAISS (IVF, PQ, HNSW), hashing perceptual para detectar duplicados | [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/upm-classes/AAPI_2026/blob/main/notebooks/T3_4_indexado_recuperacion.ipynb) |

Cada notebook termina con una sección de **ejercicios** pensados para hacer en clase.

### Orden recomendado

```
T3_1  →  T3_2  →  T3_3  →  T3_4
clásicas   profundas   anotación   indexado
```

`T3_3` y `T3_4` reutilizan ideas de `T3_1`, pero cada notebook se puede ejecutar de forma independiente.

---

## Cómo usarlos

### En Google Colab (recomendado)

1. Pulsa el botón **Abrir en Colab** del notebook.
2. *Archivo → Guardar una copia en Drive* para poder modificarlo.
3. Para el notebook 2 y las celdas de CLIP del notebook 3: *Entorno de ejecución → Cambiar tipo de entorno de ejecución → GPU T4*. También funciona sin GPU, pero la extracción de embeddings tarda unos minutos más.
4. *Entorno de ejecución → Ejecutar todas*.

### En local

```bash
git clone https://github.com/upm-classes/AAPI_2026.git
cd REPOSITORIO
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

---

## Celdas marcadas con **[Colab]**

Las celdas cuyo título empieza por `# [Colab]` necesitan PyTorch, descargas o librerías que Colab ya trae o instala en un momento. El resto del notebook funciona sin ellas.

| Notebook | Celdas [Colab] | Necesitan |
|---|---|---|
| T3_1 | ninguna | — |
| T3_2 | 8 | `torch`, `torchvision`, `transformers` y descarga de CIFAR-10 (~170 MB) |
| T3_3 | 3 (sección 7) | `torch`, `torchvision`, `transformers` y CIFAR-10 |
| T3_4 | 3 (FAISS e imagehash) | `pip install faiss-cpu imagehash` |

Los notebooks se entregan **con las salidas ya ejecutadas** en las celdas que no dependen de PyTorch, para que se puedan leer en GitHub sin ejecutarlos.

---

## Requisitos

Todo viene instalado en Colab salvo lo indicado. Para trabajar en local, `requirements.txt`:

```text
numpy
scipy
pandas
matplotlib
scikit-image
scikit-learn
opencv-python
jupyterlab
# Celdas [Colab]
torch
torchvision
transformers
faiss-cpu
imagehash
```

---

## Datos

| Notebook | Datos | Descarga |
|---|---|---|
| T3_1 | `skimage.data` (astronaut, chelsea, coffee, coins, camera, brick, grass, gravel, moon) | ninguna, vienen con `scikit-image` |
| T3_2 | CIFAR-10 (subconjunto de 2 000 + 1 000 imágenes) | automática con `torchvision` |
| T3_3 | `skimage.data.coins`, dígitos de `scikit-learn`, datos sintéticos; CIFAR-10 en la sección 7 | automática |
| T3_4 | dígitos de `scikit-learn`, datos sintéticos, `skimage.data` | ninguna |

---

## Estructura del repositorio

```
.
├── README.md
├── requirements.txt
└── notebooks/
    ├── T3_1_caracteristicas_clasicas.ipynb
    ├── T3_2_caracteristicas_profundas.ipynb
    ├── T3_3_anotacion_semantica.ipynb
    └── T3_4_indexado_recuperacion.ipynb
```