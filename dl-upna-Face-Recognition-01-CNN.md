| [Principal](./index.html) | **versión 1** |  [versión 2](./dl-upna-Face-Recognition-02-VGGFace2Keras.html) | [versión 3](./dl-upna-Face-Recognition-03-VGGFace2Keras-Architectures.html) |  [versión 4](./dl-upna-Face-Recognition-04-FineTuning.html) | [versión 5](./dl-upna-who-am-i.html) |


----
*Notebook*: [dl-upna-Face-Recognition-01-CNN](https://colab.research.google.com/github/afrago/dl-upna-face-recognition/blob/master/dl_upna_Face_Recognition_01_CNN.ipynb)


##                Redes Neuronales Convolucionales
Se produjo un avance en la creación de modelos para la clasificación de imágenes cuando se descubrió que se podía usar una red neuronal convolucional (CNN) para extraer de forma progresiva niveles cada vez más altos de representaciones del contenido de las imágenes. En lugar de preprocesar los datos para obtener atributos como texturas y formas, una CNN toma, como información de entrada, los datos de los píxeles sin procesar de la imagen y aprende a extraer estos atributos y a deducir qué objeto constituyen.
Para comenzar, la CNN recibe un mapa de atributos de entrada: una matriz tridimensional en la que el tamaño de las dos primeras dimensiones corresponde al largo y ancho de las imágenes en píxeles. El tamaño de la tercera dimensión es 3 (corresponde a los 3 canales de una imagen de color: rojo, verde y azul). La CNN abarca un conjunto de módulos, y cada uno realiza tres operaciones.

### Capas convolucionales
Una convolución es la simple aplicación de un filtro a una entrada que resulta en una activación. La aplicación repetida del mismo filtro a una entrada da como resultado un mapa de activaciones llamado mapa de características, que indica las ubicaciones y la fuerza de una característica detectada en una entrada, como una imagen.

Se puede crear una capa convolucional especificando tanto el número de filtros a aprender como el tamaño fijo de cada filtro, a menudo llamado forma de núcleo.

### Capas de agrupación
La agrupación de capas proporciona un enfoque para reducir el muestreo de los mapas de características al resumir la presencia de características en parches del mapa de características.

La agrupación máxima, o agrupación máxima, es una operación de agrupación que calcula el valor máximo, o más grande, en cada parche de cada mapa de características.

### Capa clasificadora
Una vez extraídos los rasgos, pueden ser interpretados y utilizados para hacer una predicción, como la clasificación del tipo de objeto en una fotografía.

Esto puede lograrse primero aplanando los mapas de características bidimensionales, y luego agregando una capa de salida totalmente conectada. Para un problema de **clasificación binaria**, la capa de salida tendría un nodo que predeciría un valor entre 0 y 1 para las dos clases.
#### Ejemplo: 
* [Clasificación de gatos y perros](https://developers.google.com/machine-learning/practica/image-classification/exercise-1).

Un ejemplo de **clasificación multiclase** utilizando CNN es el realizado con el dataset de [CIFAR 10](https://www.cs.toronto.edu/~kriz/cifar.html), donde se pueden llegar a predecir 10 tipos de elementos diferentes; avión, vehículo, pajaro, gato, ciervo, perro, rana, caballo, barco y camión.
#### Ejemplo: 
* [Clasificación con 10 clases CIFAR 10 - keras](https://github.com/keras-team/keras/blob/master/examples/cifar10_cnn.py)
* [Clasificación con 10 clases CIFAR 10 - TensorFlow](https://colab.research.google.com/github/Hvass-Labs/TensorFlow-Tutorials/blob/master/06_CIFAR-10.ipynb#scrollTo=_7IkURkEUWFq)


##               Conclusiones
En este notebook se ha visto como para el reconocimiento facial no nos basta con hacer uso de Redes Neuronales Convolucionales, ya que solo se ha obtenido una precisión del 10%.
Esto es debido a que nos encontramos con 500 clases diferentes y un número de parámetros (679,873,684) demasiado grande en las capas completamente conectadas.

A continuación se va a analizar la detección y reconocimiento de rostros con el modelo Multi-task Cascaded Convolutional Networks [MTCNN](https://kpzhang93.github.io/MTCNN_face_detection_alignment) y el [VGGFace2 en Keras](https://github.com/rcmalli/keras-vggface).
