| [Principal](./index.html) | [versión 1](./dl-upna-Face-Recognition-01-CNN.html) |  [versión 2](./dl-upna-Face-Recognition-02-VGGFace2Keras.html) | [versión 3](./dl-upna-Face-Recognition-03-VGGFace2Keras-Architectures.html) |  [versión 4](./dl-upna-Face-Recognition-04-FineTuning.html) |


----

*Notebook*: [dl-upna-Face-Recognition-03-VGGFace2Keras_Architectures](https://colab.research.google.com/github/afrago/dl-upna-face-recognition/blob/master/dl_upna_Face_Recognition_03_VGGFace2Keras_Architectures.ipynb)


## Comparación entre los diferentes modelos preentrenados de Keras-VGGFace

La biblioteca keras-vggface proporciona tres modelos VGGModels pre-entrenados, un modelo VGGFace1 a través de model='vgg16′ (el predeterminado), y dos modelos VGGFace2 'resnet50' y 'senet50'.

## Conclusión 
Podemos comprobar como el modelo vgg16 es un modelo más sencillo que los dos posteriores, con muchas menos capas, y que no llega a predecir la celebridad correcta dentro de las 5 predicciónes recogidas. Hay que tener en cuenta que este modelo fue entrenado con la versión 1 del dataset VGGFace.
En los dos siguientes modelos, 'resnet50' y 'senet50', la predicción es correcta y supera el 99%. Una vez llegado a estos niveles de predicción podemos ver que las mejoras son solo pequeñas decimas del porcentaje. En 'resnet50' predice la celebridad correcta con un 99,534%. En 'senet50' la predicción del personaje correcto se hace con un 99,784%

