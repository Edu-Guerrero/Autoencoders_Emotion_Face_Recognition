# 1. Análisis del Dataset
El dataset cuanta con una carpeta de entrenamienton de 200 imagenes y una carpeta de prueba con 12 imagenes. Las imagenes tratan de emociones expresadas por distintas personas y los nombres de las imagenes siguen el siguiente formato: NombrePersona.EmocionNumero.Numero.jpg
![KA.AN1.39](Images\KA.AN1.39.jpg)

*La Imagen KA.AN1.39 muestra al sujeto KA con la emocion AN, angry*

Haciendo un análisis del dataset se obtiene las siguientes frecuencias de emociones
![Emotions_training](Images\Emotions_training.jpeg)

![Emotions_test](Images\Emotions_test.jpeg)

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
![Sparse_loss](Images\sparse_loss.png)

### Reconstrucción de las imágenes
![Sparse_Reconstruct1](Images\sparse_reconstruction_1.png)
![Sparse_Reconstruct2](Images\sparse_reconstruction_2.png)
![Sparse_Reconstruct3](Images\sparse_reconstruction_3.png)

### Espacio latente
![Sparse_Latent_Space](Images\sparse_latent_space.png)

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
![Sparse_loss](Images\denoising_loss.png)

### Reconstrucción de las imágenes
![Sparse_Reconstruct1](Images\sparse_reconstruction_1.png)
![Sparse_Reconstruct2](Images\sparse_reconstruction_2.png)
![Sparse_Reconstruct3](Images\sparse_reconstruction_3.png)

### Espacio latente
![Sparse_Latent_Space](Images\sparse_latent_space.png)