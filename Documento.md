La web
======
La WWW o World Wide Web es un sistema de distribución de documentos de hipertexto que están interconectados y son accesibles vía internet. El usuario a través de un navegador web visualiza el contenido proporcionado por la web compuesto por elementos multimedia y texto.

Pero la web es un entorno con unas características un poco adversas a la hora de poder hacer búsquedas sobre ellas esto es debido a su escala, volatilidad y variabilidad de la calidad de las mismas.

En la web no hay un diseño general, aparte de incluir información verídica puede incluir información obsoleta y contradicciones, el contenido es generado dinámicamente en el tiempo por lo que es necesario volver a analizar cada web para incluirlas en los resultados de las búsquedas de forma rutinaria y por último tiene un gran crecimiento llegando a duplicarse cada pocos meses.

Modelo de arquitectura referente de motores de búsqueda
========================================================

Los motores de búsqueda que operan en internet tienen comunmente una arquitectura centralizada, los elementos que componen esta arquitectura son:

  * **Crawler**: Un crawler o una araña es normalmente un módulo que se encarga de la agregación al sistema de los documentos que posteriormente serán indexados para su búsqueda. De forma obvia la obtención de documentos de Internet no es una cuestión sencilla de resolver debido a la naturaleza descentralizada de la web. El funcionamiento básico de un crawler o araña es:
    ~~~
    - Partimos de un conjunto semilla de URLs iniciales
    - Establecemos una cola con prioridad en la que se irán incluyen las URLs anteriores
    - Para cada URL de la cola:
      - Descargamos el contenido de la web
      - Estraemos los términos de indexación
      - Incluimos los links de la web en la cola con prioridad
      - Se vuelve a añadir a la cola la URL analizada
    ~~~

    Pero este proceso básico no es lo único a tener en cuenta de hecho las arañas suelen necesitar la ayuda de los servidores webs que analizan, con la aportación de datos que permiten entre otras cosas excluir webs del servidor de la araña o moderar el número de peticiones por minuto.

    Existen muchas heurísticas y algoritmos para el crawling y la mayoria de ellos se basan en el análisis de hipertexto en los documentos.

  * **Indexer**: El indexador es el módulo que se encarga de a partir de los datos obtenidos con el proceso de crawling construir una estructura de acceso rápido (normalmente una tabla hash) llamada índice. Existen diversos modelos de indexación algunos de ellos son:
    * Modelo binario: La interpretación principal de este modelo consiste en en la elaboración de un índice centrandose en la aparición o no de los términos en los documentos.
    * Modelo Vectorial: Este modelo a diferencia del alterior tiene en cuenta la frecuencia de aparición de un término en los documentos (tf), sin embargo a lo largo del tiempo han surgido modelos que tienen en cuenta la frecuencia inversa de aparición de un término en un documento (idf), y otro modelo que combina las dos ideas anteriorer llamado modelo tf-idf.
    * Modelo Probabilistico: El modelo probabilistico se centra en la probabilidad de aparición de un término en un documento.

  * **Searcher**: El buscador es aquel módulo que normalmente se encarga de el procesamiento de las consultasque se realizan normalmente a través de un entorno web con un navegador, es el encargado de la realización de consultas sobre el índice creado por el indexador anterior.

  * **Dispatcher**: Por último el dispatcher es el encargado de la recepción de la consulta realizada desde el buscador y enviarla al servidor que realiza el cotejamiento con el índice para posteriormente obtener una lista ordenada por una puntuación denominada relevancia de URLs.
