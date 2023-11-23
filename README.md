# Detección de Matrículas de Coches utilizando YOLOv8

En esta práctica, nuestro objetivo es implementar un sistema de detección de matrículas de coches utilizando el modelo YOLOv8 para la detección de vehículos.

### Primera parte ###
#### Detección de matrículas usando bordes ####
El proceso de detección consta de varios pasos para lograr obtener una matrícula:

Primero, utilizamos el modelo YOLOv8 para detectar vehículos en la imagen. Si se identifica un coche o un camión (el modelo tiende a confundir coches grandes con camiones), dividimos la celda aproximadamente a la mitad para así acotar el lugar de búsqueda. Seguidamente, detectamos todos los bordes en la región de interés y filtramos por aquellos que tengan forma rectangular y superen cierto área. Este filtrado consta a su vez de varios pasos:

1. **Filtrado de Rectángulos**: Para asegurarnos de que los bordes formen un rectángulo, calculamos el número de bordes obtenidos, buscando que sean cuatro. Así conseguimos quitar los bordes que tengan formas irregulares con menor o mayor número de bordes.

2. **Filtrado por Área**: A su vez, usamos un pequeño umbral para el área y asegurarnos de quitar bordes que sean demasiado pequeños.

5. **Filtrado por Diferencias de X e Y**: Calculamos las diferencias de X e Y de los lados de un rectángulo. Filtramos las matrículas donde estas diferencias son menores a cierto umbral, permitiendo que las fotos tomadas de lado también sean incluidas en las matrículas filtradas. Este es el paso que mayor filtrado realiza y el que más difícil y problemas ha dado para conseguir que el filtrado se ajuste a lo que buscamos. Hemos probado diversos métodos pero finalmente hemos optado por este ya que daba mejores resultados.

![image](https://github.com/Kronn0/VC_P5/assets/92724148/71e1f7d8-c2cd-4ff2-9d01-372ec5638cd2)

![image](https://github.com/Kronn0/VC_P5/assets/92724148/d065d2ef-fa30-446b-90c2-e241d925f5b1)



### Segunda parte ###
#### Detección de matrículas entrenando el modelo YOLOv8 y reconocimiento de texto ####

En la segunda parte de esta práctica, entrenamos YOLOv8 con 50 épocas y un conjunto de datos de 350 imágenes. El conjunto de datos incluye imágenes de coches con matrículas y las etiquetas "vehicle" y "license-plate". Este conjunto de datos fue obtenido de [Roboflow](https://public.roboflow.com/object-detection/license-plates-us-eu/3/download/yolov8).

Para la lectura de las matrículas, utilizamos la biblioteca pytesseract, que convierte una imagen en una cadena de texto. Cada vez que se detecta una matrícula, usamos pytesseract y realizamos un filtrado previo, ya que la cadena devuelta suele contener caracteres sin sentido provenientes de las distintas partes de la matrícula según su origen.

Finalmente, dibujamos la matrícula en la propia ventana de la imagen para una fácil visualización.

![image](https://github.com/Kronn0/VC_P5/assets/92724148/f4aa4ab9-edcb-42c0-8501-831ace5628f4)

![image](https://github.com/Kronn0/VC_P5/assets/92724148/2377cb78-8b7f-4b7d-b91a-d4c98f7d1d94)

##Matriz de confusión normalizada del entrenamiento:


![confusion_matrix_normalized](https://github.com/Kronn0/VC_P5/assets/92724148/b9dfd69a-94b2-46d1-b3ae-5984beb7f471)



