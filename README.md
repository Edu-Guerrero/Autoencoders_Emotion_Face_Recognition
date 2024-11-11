# 1. Análisis del Dataset
El dataset cuanta con una carpeta de entrenamienton de 200 imagenes y una carpeta de prueba con 12 imagenes. Las imagenes tratan de emociones expresadas por distintas personas y los nombres de las imagenes siguen el siguiente formato: NombrePersona.EmocionNumero.Numero.jpg}

![KA.AN1.39](Images/KA.AN1.39.jpg)

*La Imagen KA.AN1.39 muestra al sujeto KA con la emocion AN, angry*

Haciendo un análisis del dataset se obtiene las siguientes frecuencias de emociones
![Emotions_training](Images/Emotions_training.jpeg)

![Emotions_test](Images/Emotions_test.jpeg)

# Implementación de Autoencoders
## Sparse
### Parámetros

| No. | Dim | Sparsity |
|-----|-----|----------|
| 1   | 32  | 1e-5     |
| 2   | 64  | 1e-6     |
| 3   | 128 | 1e-7     |

Épocas: 100
Batch_size: 16
Validation_split: 0.2

### Gráfica loss
![Sparse_loss](Images/sparse_loss.png)

### Reconstrucción de las imágenes
![Sparse_Reconstruct1](Images/sparse_reconstruction_1.png)
![Sparse_Reconstruct2](Images/sparse_reconstruction_2.png)
![Sparse_Reconstruct3](Images/sparse_reconstruction_3.png)

### TSNE para visualización del espacio latente en el conjunto de entrenamiento
![Sparse_TSNE](Images/tsne_sparse.png)

## Denoising
### Parámetros

| No. | Dim | Noise   |
|-----|-----|---------|
| 1   | 32  | 0.1     |
| 2   | 64  | 0.2     |
| 3   | 128 | 0.3     |

Épocas: 100
Batch_size: 16
Validation_split: 0.2

### Gráfica loss
![Sparse_loss](Images/denoising_loss.png)

### Reconstrucción de las imágenes
![Sparse_Reconstruct1](Images/denoising_reconstruction_1.png)
![Sparse_Reconstruct2](Images/denoising_reconstruction_2.png)
![Sparse_Reconstruct3](Images/denoising_reconstruction_3.png)

### TSNE para visualización del espacio latente en el conjunto de entrenamiento
![Sparse_TSNE](Images/tsne_denoising.png)

# Comparación de los autoencoders
## Proceso de Clasificación

1. Etapa de Codificación: Pasar cada imagen a través de la parte del codificador del autoencoder. Esto genera una representación en el espacio latente (un vector de características comprimido y significativo) para cada imagen.

2. Guardar Representaciones Latentes: Recopilar y almacenar estas representaciones latentes, ya que sirven como el conjunto de características para el modelo de clasificación.

3. Modelo de Clasificación: Entrenar un algoritmo de clasificación (por ejemplo, SVM, regresión logística o una red neuronal) utilizando las representaciones del espacio latente como entrada y las etiquetas correspondientes como objetivo.

4. Evaluación: Probar el rendimiento del clasificador en un conjunto de validación o prueba para asegurar la calidad del espacio latente generado por el autoencoder.

## Comparación del error de reconstrucción
![Reconstruction_Error](Images/reconstruction_error.png)

## Evaluación con SVM
![SVM](Images/svm_ae.jpeg)

## Resultados para todas las configuraciones

| Tipo de modelo | Dimensión de codificación | Parámetro adicional               | Accuracy |
|----------------|---------------------------|-----------------------------------|----------|
| Sparse         | 32                        | Regularización de sparsity: 1e-05 | 0.0000   |
| Denoising      | 32                        | Tasa de dropout: 0.1              | 0.2500   |
| Sparse         | 64                        | Regularización de sparsity: 1e-06 | 0.0000   |
| Denoising      | 64                        | Tasa de dropout: 0.2              | 0.0833   |
| Sparse         | 128                       | Regularización de sparsity: 1e-07 | 0.0833   |
| Denoising      | 128                       | Tasa de dropout: 0.3              | 0.3333   |

## Evaluación con Naive Bayes
![Naive_Bayer](Images/naive_ae.jpeg)


| Tipo de modelo | Dimensión de codificación | Parámetro adicional               | Accuracy |
|----------------|---------------------------|-----------------------------------|----------|
| Sparse         | 32                        | Regularización de sparsity: 1e-05 | 0.4167   |
| Denoising      | 32                        | Tasa de dropout: 0.1              | 0.0833   |
| Sparse         | 64                        | Regularización de sparsity: 1e-06 | 0.4167   |
| Denoising      | 64                        | Tasa de dropout: 0.2              | 0.0833   |
| Sparse         | 128                       | Regularización de sparsity: 1e-07 | 0.0833   |
| Denoising      | 128                       | Tasa de dropout: 0.3              | 0.0833   |










