# Homografia_RANSAC_OpenCV

Este repositorio contiene un notebook de Google Colab que implementa la estimación de homografía entre dos imágenes utilizando DLT normalizado y el algoritmo RANSAC para una detección robusta de correspondencias. Se emplea el algoritmo SIFT para la extracción de características y FLANN para el emparejamiento.

## Descripción del Proyecto

El proyecto aborda el problema de la estimación de la matriz de homografía que transforma puntos de una imagen a otra. Esto es fundamental en visión por computador para tareas como el stitching de imágenes (unión de varias imágenes para crear una panorámica), el registro de imágenes o la detección de objetos en diferentes vistas. La implementación incluye:

- **Normalización de Puntos:** Para mejorar la estabilidad numérica del algoritmo DLT.
- **DLT (Direct Linear Transformation):** Para calcular una homografía inicial a partir de un conjunto mínimo de correspondencias.
- **RANSAC (Random Sample Consensus):** Un algoritmo robusto para estimar el modelo de homografía, que es capaz de manejar una gran cantidad de *outliers* (correspondencias incorrectas) entre los puntos emparejados.
- **SIFT (Scale-Invariant Feature Transform):** Para detectar y describir puntos de interés en las imágenes de manera invariante a escala y rotación.
- **FLANN (Fast Library for Approximate Nearest Neighbors):** Para un emparejamiento rápido y eficiente de las descripciones SIFT.

El código toma dos imágenes, encuentra correspondencias de características entre ellas, estima la homografía más robusta y luego proyecta una imagen sobre la otra para visualizar la transformación.

## Requisitos

Para ejecutar este notebook, necesitarás las siguientes librerías de Python:

- `numpy`
- `matplotlib`
- `opencv-python` (cv2)

Estas librerías suelen estar preinstaladas en Google Colab. Si las ejecutas localmente, puedes instalarlas con `pip`:

```bash
pip install numpy matplotlib opencv-python
Cómo Usar
Clonar el Repositorio: Clona este repositorio en tu máquina local o ábrelo directamente en Google Colab.
Cargar Imágenes: Asegúrate de tener las imágenes de entrada (box.jpg y photo01a.jpg) en el mismo directorio que el notebook o ajusta las rutas en el código.
Ejecutar el Notebook: Abre el archivo .ipynb en Google Colab o Jupyter Notebook y ejecuta todas las celdas.
El notebook realizará los siguientes pasos:

Cargará las imágenes.
Detectará características SIFT en ambas imágenes.
Emparejará las características utilizando FLANN.
Aplicará RANSAC para encontrar la homografía más robusta.
Transformará la primera imagen usando la homografía calculada.
Mostrará las imágenes originales, las correspondencias y la imagen transformada.
Archivos de Ejemplo
El notebook espera encontrar dos imágenes:

box.jpg: Una imagen de consulta (queryImage).
photo01a.jpg: Una imagen de entrenamiento (trainImage).
Si deseas usar tus propias imágenes, simplemente reemplaza estos archivos y actualiza los nombres en la celda de carga de imágenes.

Resultados
El notebook generará varias visualizaciones:

Las imágenes originales (img1 e img2).
La imagen transformada (img4), que muestra img1 proyectada sobre img2 de acuerdo con la homografía encontrada.
Un plot de matplotlib mostrando las coincidencias entre las dos imágenes, así como las imágenes individuales y la imagen transformada para una mejor comparación.
