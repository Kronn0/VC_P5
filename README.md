# VC_P5

# Tarea 

En esta practica tenemos que detectar matriculas de coches, para ello hemos utilizado YOLO8 para la detección de vehiculos, si detectamos que es un coche o un camión, dividimos la celda aproximada a la mitad y detectamos todos los bordes, de ellos elegimos los bordes que tengan forma rectangular, y superen un cierto area. 



Luego la segunda parte hemos entrenado YOLO8 con 50 epocas y un dataset de 350 imagenes las cuales consisten en coches con matriculas, hemos obtenido el dataset de Roboflow. Entrenado, podemos detectar automaticamente las matriculas de coche, luego para leer las matriculas en sí, hemos utilizado pytesseract el cual puede pasar una imagen a una String. Con ella cada vez que detectamos una matricula, la pasamos por pytesseract y luego dibujamos que lee de la matricula.
