# 🧠 CNN vs MLP: Análisis Comparativo en Clasificación de Imágenes

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://python.org)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange.svg)](https://tensorflow.org)
[![Dataset](https://img.shields.io/badge/Dataset-CIFAR--10-green.svg)](https://www.cs.toronto.edu/~kriz/cifar.html)

> **Informe técnico comparativo** que demuestra la superioridad de las Redes Neuronales Convolucionales (CNN) frente a los Perceptrones Multicapa (MLP) en tareas de clasificación de imágenes.

**Asignatura:** Machine Learning II — Unidad 2, Tema 1

---

## 📊 Resultados Principales

| Métrica | MLP | CNN | Ventaja CNN |
|---------|-----|-----|-------------|
| **Parámetros** | 1,707,274 | 122,570 | **13.9x menos** |
| **Accuracy Test** | 49.15% | 68.81% | **+19.7%** |
| **Loss Test** | 1.4214 | 0.9127 | **-35.8%** |

> ✅ **La CNN logra 19.7% más accuracy con 13.9x MENOS parámetros**

---

## 📈 Curvas de Aprendizaje

<p align="center">
  <img width="1389" height="495" alt="image" src="https://github.com/user-attachments/assets/27044de3-cd7b-419d-9268-eacf23c7b976" />
</p>

La CNN muestra una trayectoria ascendente sostenida, mientras que el MLP se estanca rápidamente alrededor del 49%.

---

## 🏗️ Arquitecturas

### MLP (Perceptrón Multicapa)
```python
mlp = keras.Sequential([
    layers.Flatten(input_shape=(32, 32, 3)),
    layers.Dense(512, activation='relu'),
    layers.Dense(256, activation='relu'),
    layers.Dense(10, activation='softmax')
], name='MLP')
```

### CNN (Red Neuronal Convolucional)
```python
cnn = keras.Sequential([
    layers.Conv2D(32, (3,3), activation='relu', input_shape=(32,32,3)),
    layers.MaxPooling2D((2,2)),
    layers.Conv2D(64, (3,3), activation='relu'),
    layers.MaxPooling2D((2,2)),
    layers.Conv2D(64, (3,3), activation='relu'),
    layers.Flatten(),
    layers.Dense(64, activation='relu'),
    layers.Dense(10, activation='softmax')
], name='CNN')
```

---

## 🔬 Análisis Teórico

### 1. Escala Paramétrica (Imagen 224×224×3)

| Modelo | Cálculo | Parámetros |
|--------|---------|------------|
| MLP | 150,528 × 512 + 512 | **77,070,848** |
| CNN (96 filtros 11×11×3) | 96 × (11×11×3 + 1) | **34,944** |

> Reducción de **2,206x** en la primera capa.

### 2. Equivarianza a la Traslación

<p align="center">
  <img src="fig_equivarianza.png" alt="Equivarianza" width="600">
</p>

El mismo filtro convolucional detecta bordes verticales **sin importar su ubicación** en la imagen.

### 3. Max-Pooling

<p align="center">
  <img src="fig_maxpooling.png" alt="Max-Pooling" width="700">
</p>

Reduce la dimensionalidad un 75% e introduce **invarianza a perturbaciones locales**.

---

## 📁 Estructura del Proyecto

```
ACT4/
├── CNN_vs_MLP_Comparativo.ipynb   # Notebook con la experimentación completa
├── generar_informe_word.py        # Script generador del informe en Word
├── generar_informe.py             # Script generador del informe en PDF
├── fig_parametros.png             # Gráfica comparativa de parámetros
├── fig_equivarianza.png           # Demostración de equivarianza
├── fig_maxpooling.png             # Demostración de Max-Pooling
├── fig_entrenamiento.png          # Curvas de accuracy y loss
├── Informe_CNN_vs_MLP.docx        # Informe generado (Word)
├── Informe_CNN_vs_MLP.pdf         # Informe generado (PDF)
└── README.md                     # Este archivo
```

---

## 🚀 Cómo Ejecutar

### 1. Clonar el repositorio
```bash
git clone https://github.com/TU_USUARIO/CNN-vs-MLP-CIFAR10.git
cd CNN-vs-MLP-CIFAR10
```

### 2. Instalar dependencias
```bash
pip install tensorflow matplotlib numpy scipy python-docx fpdf2
```

### 3. Ejecutar el notebook
Abrir `CNN_vs_MLP_Comparativo.ipynb` en Jupyter Notebook o Google Colab.

### 4. Generar el informe
```bash
python generar_informe_word.py   # Genera .docx
python generar_informe.py        # Genera .pdf
```

---

## 🎯 Conclusiones

1. **Eficiencia paramétrica**: La CNN utiliza **13.9x menos parámetros** gracias a la conectividad local y compartición de pesos.
2. **Equivarianza**: La CNN generaliza patrones espaciales sin importar su ubicación, logrando **+19.7% accuracy**.
3. **Max-Pooling**: Reduce dimensionalidad y actúa como **regularizador implícito**, previniendo el sobreajuste.

---

## 📚 Referencias

- Krizhevsky, A., Sutskever, I. & Hinton, G. (2012). *ImageNet Classification with Deep Convolutional Neural Networks*. NIPS.
- Goodfellow, I., Bengio, Y. & Courville, A. (2016). *Deep Learning*. MIT Press, Cap. 9.
- Krizhevsky, A. (2009). *Learning Multiple Layers of Features from Tiny Images* (CIFAR-10).

---

<p align="center">
  <i>Desarrollado como parte del curso de Machine Learning II</i>
</p>
