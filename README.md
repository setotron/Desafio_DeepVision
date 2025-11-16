📹# Proyecto de Deep Vision: Clasificación de CIFAR-10 con CNNs

Este repositorio documenta un ejercicio práctico de Deep Vision para la clasificación de imágenes del dataset **CIFAR-10** (10 clases) utilizando TensorFlow y Keras.

El objetivo principal es comparar el rendimiento de una Red Neuronal Densa (MLP) simple frente a varias arquitecturas de Redes Neuronales Convolucionales (CNNs), analizando el impacto de diferentes técnicas de regularización para combatir el sobreajuste (*overfitting*).

## 🚀 Objetivos del Proyecto

* Establecer un *baseline* (punto de referencia) usando un **MLP (Red Densa)**.
* Construir una **CNN de 2 bloques** (Conv+Pool) para aprovechar el sesgo inductivo espacial.
* Implementar técnicas de **regularización** (L2, Dropout, EarlyStopping) para combatir el *overfitting*.
* Aplicar **Data Augmentation** (aumento de datos) para mejorar la generalización del modelo.
* Experimentar con la **profundidad** (CNN de 3 bloques) y comparar optimizadores (Adam vs. SGD).
* Analizar el rendimiento del mejor modelo mediante una **matriz de confusión** y un análisis de errores.
* Realizar un **estudio de ablación** para medir el impacto cuantitativo de cada técnica de regularización.

## 📊 Resultados Principales

La CNN de 3 bloques (con regularización completa) fue el modelo con mejor rendimiento. El estudio de ablación demostró que el **Data Augmentation** fue la técnica individual más importante para la generalización.

### Estudio de Ablación (Resultados en Test)

*(Nota: Los valores son ilustrativos. Reemplazar con los resultados reales de `results/ablation_study_summary.md`)*

| Variante (Componente Retirado) | Test Accuracy | Caída vs. Control |
| :--- | :---: | :---: |
| **A (Control - Todo Activo)** | **~77.5%** | **N/A** |
| B (Sin Data Augmentation) | ~68.0% | -9.5% |
| C (Sin L2) | ~76.1% | -1.4% |
| D (Sin Dropout) | ~75.8% | -1.7% |

### Análisis de Errores

El análisis del mejor modelo (ver `figuras/confusion_matrix_BEST_...png`) muestra que las confusiones más comunes ocurren entre clases visualmente similares en 32x32px, principalmente:
* **Gato ↔ Perro**
* **Camión ↔ Coche**
* **Pájaro ↔ Avión**

## 🧬 Reproducibilidad (Release v1.0)

Este proyecto está congelado en la versión `v1.0` para garantizar la reproducibilidad de los resultados.

* **Seed Global:** `42`
* **Tag de Release:** `v1.0-P3-CIFAR10_[TuApellido]`
* **Hash de Datos (SHA-256):** `[Ver results/data_meta.json]`
* **Resultados Completos:** `[Ver results/metrics_FINAL.json]`

## 🛠️ Cómo Ejecutar

1.  Clona el repositorio:
    ```bash
    git clone [URL_DE_TU_REPO]
    cd [NOMBRE_DEL_REPO]
    ```
2.  (Opcional) Crea un entorno virtual e instala las dependencias:
    ```bash
    python -m venv venv
    source venv/bin/activate
    pip install -r env/requirements.txt
    ```
3.  Abre el notebook principal en Google Colab o Jupyter Lab:
    `CIFAR10_CNN_[tu_apellido].ipynb`
4.  Ejecuta todas las celdas de principio a fin. El notebook está diseñado para generar automáticamente todas las figuras y artefactos en las carpetas `figuras/` y `results/`.

## 📁 Estructura del Repositorio
