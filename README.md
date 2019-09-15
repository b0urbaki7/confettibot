# ConfettiBot

Este progama resuelve preguntas del juego de trivia de Facebook "Confetti" a través de Reconocimiento Óptico de Caracteres y búsquedas de Google. El proyecto es una prueba de concepto y se considera abandonado.

### Instalación de Tesseract
Info de pytesseract: https://pypi.org/project/pytesseract/  
Repo de Tessseract OCR: https://github.com/tesseract-ocr/tesseract  
Instaladores para Windows: https://github.com/UB-Mannheim/tesseract/wiki  
Archivos de Idioma para Tesseract: https://github.com/tesseract-ocr/tessdata  

Para que esto funcione, basta utilizar el instalador adecuado (puse Windows porque ese usé, macOS y Linux también disponibles), descargar el archivo de idioma para Español y colocarlo en el directorio de instalación.

### Buscador personalizado
Google API key: https://console.developers.google.com/  
Ayuda sobre API: http://developers.google.com/console/help/managing-projects  
Google Custom Search Engine (CSE): https://cse.google.com/cse/all  
StackOverflow con paso a paso (en inglés): https://stackoverflow.com/questions/37083058/programmatically-searching-google-in-python-using-custom-search  

Este paso es algo rebuscado, consiste en conseguir credenciales de Google para habilitar búsqueda, crear un motor de búsqueda personalizado con las credenciales obtenidas y habilitarlo a buscar en toda la web, instalar la librería google-api-python-client. Y listo.

### Otros requisitos
Como Confetti sólo puede ser jugado por medio de un móvil (no experimenté con emular Android), necesitamos una forma de retransmitir el juego al ordenador; para Android utilicé la aplicación Vysor, tenía buena calidad de imagen y al conectarse por USB no tenía lag, e incluso permitía enviar clicks desde el ordenador al móvil; el único inconveniente es que tenía anuncios de pantalla completa cada 30 minutos. Mobizen no me funcionó y TeamViewer era muy lento.  

Para usuarios de iOS, Quicktime funciona, pero no estoy seguro de si es el mejor método.

### El método
El método consiste en extraer el texto de las preguntas y respuestas de la transmisión y buscar en Google pregunta+respuesta, para cada una de las respuestas y seleccionar como correcta la respuesta tal que pregunta+respuesta generó más resultados de búsqueda.

### Fallas y posibles mejoras
Con una tasa promedio de 4/10 respuestas correctas, el método es apenas mejor que selección al azar. Esto se debe al rudimentario método de búsqueda y al limitante de 10 segundos para responder. Con respecto al método, éste se puede mejorar agregando condicionales e.g. interpretar las palabras "nunca, no, jamás, menos" en la pregunta como negaciones e invertir el orden de selección de respuesta i.e. escoger la respuesta con el menor número de resultados; agregar complejidad puede mejorar la presición del programa, sin embargo, esto nos lleva al problema del tiempo.


Confetti tiene un tiempo límite de 10 segundos por pregunta, los cuales son principalmente invertidos en realizar las búsquedas web, tanto así que preguntas más complejas exceden los 10 segundos. Para combatir esto, se pueden realizar menos búsquedas, se puede automatizar el proceso de búsqueda i.e. detectar cuando se hace una pregunta e inmediatamenrte empezar el programa, optimizar el código en general.


Dicho todo esto, considero que la forma óptima de utilizar este programa es agregar condicionales simples, automatizarlo y tenerlo como ayuda al momento de jugar; seleccionar las respuestas que uno conozca y cuando eso no sea posible, el programa es mejor que selección al azar.
