| [Principal](./index.html) | [versión 1](./dl-upna-Face-Recognition-01-CNN.html) |  [versión 2](./dl-upna-Face-Recognition-02-VGGFace2Keras.html) | [versión 3](./dl-upna-Face-Recognition-03-VGGFace2Keras-Architectures.html) |  [versión 4](./dl-upna-Face-Recognition-04-FineTuning.html) |
----

*Notebook*: [dl_upna_Face_Recognition_04_FineTuning](https://github.com/afrago/dl-upna-face-recognition/blob/master/dl_upna_Face_Recognition_04_FineTuning.ipynb)

## Finetuning
El ajuste fino es un proceso para tomar un modelo de red que ya ha sido entrenado para una tarea determinada, y hacer que realice una segunda tarea similar.
En el siguiente notebook se realiza un modelo personalizado, basado en la arquitectura de VGGFace16, el cual es entrenado con una serie de imágenes.
Estas imágenes han sido divididas en tres directorios; train, validation y test. Dentro de train y validation aparecen varias fotos de los diferentes personajes. Una vez entrenado el modelo se realiza la predicción de las imagenes almacenadas en el directorio test.


## Cómo funciona el reconocimiento facial

### Etapa 1 y 2: Detección y alineación
La detección de rostros y ojos puede ser manejada por un algoritmo [adaboost](https://sefiks.com/2018/11/02/a-step-by-step-adaboost-example/). En otras palabras, el aprendizaje profundo no aparece en este paso. Los paquetes de visión computarizada comunes en python como OpenCV y Dlib ofrecen detección de cara y ojos.

La alineación es fácil si la cara y los ojos ya se han detectado. Los experimentos muestran que la aplicación de la alineación de la cara aumenta la precisión del modelo en más de un 1%. Desafortunadamente, ni OpenCV ni Dlib ofrecen alineación de cara como una función de salida. Tenemos que hacer algo de trigonometría aquí para alinear las caras.

El aprendizaje profundo sólo aparece en esta etapa de representación. Alimentaremos con imágenes de rostros a un modelo de redes neuronales convolucionales pero la tarea aquí no es la clasificación. Usaremos modelos de CNN para encontrar incrustaciones similares a los [Autoencoder](https://sefiks.com/2018/03/21/autoencoder-neural-networks-for-unsupervised-learning).

### Etapa 3: Representación
Una vez detectadas y alineadas las imágenes de las caras y las hemos alimentado a un modelo de reconocimiento facial en los pasos anteriores. Ahora, tenemos representaciones vectoriales para cada imagen. Transformaremos los vectores de 1D en matrices de 2D, agregando el propio vector. De esta manera, cada línea de la matriz tendrá la misma información. 
*Esto es similar a los códigos de barras. Sólo almacenan datos horizontalmente. Si dañas el código de barras horizontalmente, todavía puedes leer datos de él. Sin embargo, los daños verticales también causan pérdida de datos.*
[La representación de la cara de VGG tiene 2622 ranuras horizontales](https://i2.wp.com/sefiks.com/wp-content/uploads/2020/05/vggface-representation.png?resize=720%2C365&ssl=1)

### Etapa 4: Verificación
Compararemos las representaciones vectoriales de las imágenes. La forma más fácil de comparar dos vectores es encontrar la [distancia euclidiana](https://sefiks.com/2018/08/13/cosine-similarity-in-machine-learning) entre ellos. 

