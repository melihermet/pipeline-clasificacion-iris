# Pipeline de entrenamiento, validación y clasificador base

## 1. Descripción

Este proyecto implementa un pipeline de Deep Learning utilizando PyTorch para clasificar las tres especies de flores del conjunto de datos Iris.

Incluye la configuración del entorno, la preparación de los datos, la definición de una arquitectura de red neuronal multicapa (MLP), el entrenamiento del modelo, su evaluación sobre un conjunto de validación independiente y el seguimiento de métricas por época.

## 2. Dataset

Se utiliza el dataset Iris de scikit-learn.

- **Observaciones:** 150
- **Características:** 4 variables numéricas
- **Clases:** setosa, versicolor y virginica
- **División:** 80 % entrenamiento y 20 % validación
- **Estrategia:** división estratificada para conservar la proporción de clases en ambos conjuntos

Las características se estandarizan utilizando exclusivamente el conjunto de entrenamiento. El mismo escalador se aplica posteriormente al conjunto de validación, evitando la fuga de información (data leakage).

## 3. Arquitectura del modelo

Se utiliza un perceptrón multicapa (Multilayer Perceptron, MLP) con una capa oculta:

- **Entrada:** 4 características
- **Capa oculta:** 16 neuronas
- **Activación:** ReLU
- **Salida:** 3 valores (logits), uno por clase

La función de pérdida es CrossEntropyLoss y el optimizador es Adam.

## 4. Parámetros del entrenamiento

- **Framework:** PyTorch
- **Versión observada en el entorno:** 2.11.0+cpu
- **Optimizador:** Adam
- **Learning rate:** 0.01
- **Épocas:** 100
- **Semilla aleatoria:** 42
- **Dispositivo utilizado:** CPU

## 5. Resultados

Al finalizar las 100 épocas se obtuvieron los siguientes valores:

| Métrica | Entrenamiento | Validación |
|---|---:|---:|
| Loss | 0.0590 | 0.0851 |
| Accuracy | 97.50 % | 96.67 % |

La pérdida disminuyó en ambos conjuntos durante el entrenamiento.
No se observa un aumento sostenido de la pérdida de validación
que indique sobreajuste en las épocas evaluadas.

La validación contiene 30 observaciones, por lo que sus métricas
deben interpretarse considerando el tamaño reducido de la muestra.

## 6. Interpretación de las curvas

La pérdida (loss) mide el error según la función CrossEntropyLoss. Su disminución progresiva indica que el modelo mejora sus predicciones durante el entrenamiento.

La exactitud (accuracy) representa la proporción de clasificaciones correctas. La evolución de las métricas de entrenamiento y validación muestra un comportamiento similar, con valores finales cercanos, lo que sugiere una adecuada capacidad de generalización sobre los datos de validación.

## 7. Reproducibilidad

Se fijan semillas para Python, NumPy y PyTorch. La división de los datos también utiliza una semilla fija.

El experimento se ejecutó en CPU. Los resultados pueden variar si se cambia el entorno, las versiones de las librerías o el dispositivo de cálculo.

## 8. Cómo ejecutar

El notebook puede ejecutarse utilizando Google Colab o un entorno local con Python y las dependencias instaladas.

**Opción 1: Google Colab**

1. Abrir el repositorio en GitHub.
2. Ingresar a la carpeta `notebooks/` y abrir el archivo `01_pipeline_clasificador_base.ipynb`.
3. Descargar el notebook o abrirlo en Google Colab.

**Opción 2: Entorno local**

1. Instalar las dependencias indicadas en `requirements.txt`.
2. Abrir el notebook ubicado en `notebooks/`.
3. Ejecutar las celdas en orden, desde la configuración del entorno hasta la visualización de las métricas.

El dataset Iris se carga desde scikit-learn, por lo que no es necesario descargar un archivo de datos manualmente.

## 9. Estructura del repositorio

```text
pipeline-clasificacion-iris/
│
├── notebooks/
│   └── 01_pipeline_clasificador_base.ipynb
│
├── README.md
│
└── requirements.txt
```
