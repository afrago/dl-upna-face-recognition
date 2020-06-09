| [versión 1](./dl-upna-Face-Recognition-01-CNN.html) |  [versión 2](./dl-upna-Face-Recognition-02-VGGFace2Keras.html) | [versión 3](./dl-upna-Face-Recognition-03-VGGFace2Keras-Architectures.html) |  [versión 4](./dl-upna-Face-Recognition-04-FineTuning.html) |


----


*Notebook*: [dl-upna-Face-Recognition-02-VGGFace2Keras](https://colab.research.google.com/github/afrago/dl-upna-face-recognition/blob/master/dl_upna_Face_Recognition_02_VGGFace2Keras.ipynb)


## Sistemas de reconocimiento facial
El sistema de reconocimiento facial es una aplicación dirigida por ordenador que identifica automáticamente a una persona en una imagen digital. Esto es posible mediante un análisis de las características faciales del sujeto extraídas de la imagen.
Los métodos de aprendizaje profundo son capaces de aprovechar conjuntos de datos muy grandes de rostros, lo que permite a los modelos modernos entrenarse y evaluar si se ha realizado correctamente el proceso de reconocmiento facial.
Un sistema de reconocimiento facial consta de dos modos:
1. verificación (o autenticación) de la cara:
* La verificación de la cara implica una relación de coincidencia uno a uno, donde se compara una cara de una imagen de consulta, con la imagen de la cara una persona ya identificada. 
2. identificación (o reconocimiento) de la cara.
* La identificación de la cara implica una comparación de uno a muchos que compara una cara de la consulta contra múltiples caras en la base de datos para asociar la identidad de la cara consultada con una de las que están en la base de datos. 

### Proceso de trabajo
El reconocimiento de las caras se describe a menudo como un proceso que consta de cuatro pasos: detección de las caras, alineación de las caras, extracción de los rasgos y, por último, reconocimiento de las caras.

#### Etapa 1 y 2: Detección y alineación
El primer paso en cualquier cara automática sistemas de reconocimiento es la detección de rostros en imágenes. Después de que una cara ha sido detectada, la tarea de extracción de características es para obtener los rasgos que se introducen en un rostro sistema de clasificación. Dependiendo del tipo de sistema de clasificación, las características pueden ser características locales como líneas o puntos, o rasgos faciales como los ojos, la nariz y la boca.

En este ejemplo se hace uso de la Red Neural Convolucional en Cascada Multitarea, o MTCNN, para la detección y la alineación de la cara. Los enfoques de aprendizaje profundo pueden lograr un rendimiento impresionante en estas dos tareas.  MTCNN propone un marco de tareas múltiples en cascada profunda que explota la correlación inherente entre ellas para aumentar su rendimiento. En particular, este marco adopta una estructura en cascada con tres etapas de redes convolucionales profundas cuidadosamente diseñadas que predicen la cara y la ubicación de los puntos de referencia de una manera de grueso a fino. 

#### Etapa 3: Representaciones
Hemos detectado y alineado las imágenes de las caras y las hemos alimentado a un modelo de reconocimiento facial en los pasos anteriores. Ahora, tenemos representaciones vectoriales para cada imagen.

#### Etapa 4: Verificación
Compararemos las representaciones vectoriales de las imágenes. 

## Conclusión 
Con este notebook podemos comprobar como las redes neuronales son un sistema válido de reconocimiento facial. 
El reconocimiento facial opera en uno o dos modos: 1) verificación (o autenticación) de la cara, y 2) identificación (o reconocimiento) de la cara. En ambos módos se puede hacer uso de las redes neuronales.
