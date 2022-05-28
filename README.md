# Project2_WebScrapping
Segundo proyecto del Bootcamp de Análisis de datos, esta vez enfocado a la obtención de información mediante Web Scrapping o el uso de API's dedicadas para la obtención de información. Especificamente en este proyecto, se utilizó el método de Web Scrapping para la obtención de información de la página IMDb. De esta recopilación se buscaron los valores de Titulo, Año(s) de emision y los posibles generos que pueden encasillar al contenido.

### Obtención de información
El proceso que se llevó a cabo para la extracción de la información fue el siguiente:

Para la obtención de la información, decidí moverme desde la página principal de IMDb a la página donde se estructura por géneros, desde esta pagina mediante web scrapping se buscaron los links que nos enviaran a cada una de estas páginas. 

Con los links encontrados, se visitó el primero, ya en esta página, se despliegan 50 títulos de los que podemos obtener la información, la información se extrae de estos títulos y posteriormente utilizando Selenium se busca el botón de Next al fondo dela página y se le dá un click, esto se mete dentro de un loop for para hacerlo la cantidad de veces solicitada. 

Este primer link se hizo de forma independiente para verificar el funcionamiento del código. Posteriormente para cada uno de los links de los géneros, entrando a la página principal y haciendo la búsqueda de la info de los 50 títulos, fechas y generos para las paginas requeridas para cada uno de los géneros.

Para unir todo en un solo dataframe, primero se creó un dataframe base al cual se le realizaron numerosos append para al final obtener 7500 renglones.

### Resultados
Los resultados son CSV creado a partir de un dataframe de 7500 renglones y 3 columnas conformado por un total de 15 genero con respectivos subgeneros.

### Obstaculos

Originalmente queria utilizar una API para la extracción de información de datos relacionados a precios de activos de inversiones encontrada en https://polygon.io/stocks?gclid=EAIaIQobChMIvITv_pOD-AIVDD6tBh1nnQvIEAAYASAAEgKSpPD_BwE, pero encontrando con el primer problema el cual fue que esta API unicamente permite realizar 5 llamadas por minuto, si quisiera realizar extracción de miles de datos, tomaria un timpo considerable, además de que la documentación no es especialmente clara sobre los parámetros que debe llevar la solicitud lo que dificultó utilizar esta API. 

Posteriormente quise mantener el uso de APIs para la extracción de la información por lo que decidí investigar la API de Skyscanner disponible en https://www.partners.skyscanner.net/affiliates/travel-apis donde me di cuenta que tenia que solicitar acceso a la API para poder gener un key que pudiera utilizar para llamar a la API. Por cuestiones de tiempo solicitar y esperar el acceso a la API no era una opción viable por lo que se tuvieron que conciderar otras opciones.

Finalmente llegando a la página de IMDb, pensé en utilizar la API de esta página pero igualmente era necesario solicitar acceso por lo que finalmente decidí utilizar el método de web scrapping.

En el apartado de APIs, me parece que el obstaculo más grande se trata de la documentación de la API en si misma ya que muchas veces los parametros que se tienen que pasar a la API para hacer la llamada no son especialmente claros.

Como web scrapping, creo que una de los obstaculos que encontré es que la información se encuentra en el orden en que se encuentra el HTML por lo que si hay poarte de la información perdida o no se encuentra, puede resultar incompleta y dependiendo del método que se use para hacer los dataframes puede no funcionar. en este caso utilicé list comprenhension por lo que si las listas de la información no eran del mismo tamaño, no podia crear los dataframes lo que me obligó a no poder obtener información que queria obtener.

###Lecciones aprendidas
Me parece que las lecciones aprendidas más importantes es hacer una correcta investigación de las APIs que se plantean utilizar para entenderlas a profundidad ya que aunque es relativamente sencillo, pueden encontrarse obstaculos que hay que resolver. Como web scrapping, muchas veces hay que utilizar pensamiento out of the box para poderlo resolver encontrando toda la información necesaria o que la información faltante no nos afecte.
