##¿Qué es dxtotal?

En realidad debería llamarse DivXtotal Series Download. Solo que es un nombre poco adecuado para un script de bash. Sirve para mirar en DivXtotal si hay nuevos capítulos de las series que sigues. También los añade a tu programa de torrents. En realidad, el script sólo funciona con Transmission, programa que considero el mejor por muchas cosas. Una de ellas es que permite conectarse de forma remota desde una red local o desde Internet si lo configuras. Y con el comando transmission-remote se puede interactuar. Si has optado por otra solución que permita algo parecido, seguro que no tendrás problema en modificar el script tú mismo para adaptarlo a tu software de torrents.

##Idea tras dxtotal

El caso es que mucha gente sigue series viejas o nuevas por torrent. Prácticamente cada día de la semana miramos a ver si está el siguiente capítulo de nuestro programa favorito en DivXtotal. Aunque sólo mires una vez al día la página, pinchar y añadir los torrents puede ser un trabajo considerable en tiempo. Si lo haces demasiadas veces a la semana, se convierte en una rutina molesta. Y pensé yo, ¿qué me impide escribir un script que haga justamente eso por mi? La respuesta fue: absolutamente nada. Hoy en día hay herramientas de ayer, hoy y siempre; que nos pueden hacer la vida muy fácil. Bash scripting es una de esas cosas. 

Así que ¿qué hace exactamente dxtotal? Muy simple. Descarga la página de series, extrae cada epispdio de la página y comprueba si nuestra copia de Transmission ya tiene cada torrent. Cuando se encuentra uno que no tiene, visita su página, descarga el torrent y lo añade a Transmission. 

El comando no requiere de argumentos. Se puede programar con cron a una hora determinada del día.

##Cómo indicar las series que seguimos

Este script sigue la misma estrategia que clat. No obstante, te lo explico. Crea una carpeta donde te parezca conveniente, que puedes llamar series.que.sigo, o como prefieras. La mía se llama "titles". Una vez dentro, tienes que crear un archivo por cada serie que sigues. El nombre de cada archivo debe coincidir con la serie en DivXtotal. Ten cuidado de escribirla tal cual te aparezca en la web, ya que el script tiene en cuenta mayúsculas y minúsculas. Dentro de cada archivo deberás escribir la ruta donde quieres que Transmissión ponga los archivos de la serie en cuestión. En mi caso, al ejecutar transmissión en otro ordenador, utilizo rutas relativas a ese ordenador.

##Cómo configurar el script

Antes de ejecutar el script hay que abrirlo y modificar las variables SERVER y DIR.
SERVER contiene un fragmento necesario para la linea de comandos de transmission-remote. La dirección IP del ordenador donde está Transmission, el puerto, y si en la configuración de Transmission hemos elegido introducir usuario y contraseña, estos deberán añadirse también detrás de --auth, sustituyendo admin:admin por lo que hayas elegido poner. DIR contiene la ruta hacia el directorio (que mencionamos en el apartado anterior) en el que se guardan los archivos con los nombres de tus series. Una vez cambiadas esas dos variables, ya sólo nos queda comprobar la conexión a Internet y escribir dxtotal en una terminal. El script sólo se compone de un archivo (dxtotal). Asegúrate de que tenga persmiso de ejecución y de ponerlo en un directorio que esté en el PATH, como ~/bin/.

## Opciones

* La forma más sencilla es sin opciones. Descargará la página de la sección de últimas series sin necesidad de ningún argumento.

* Si ponemos algún argumento, down entenderá que debe buscarlo en divxtotal. Para que tenga éxito el argumento debe coincidir con el título de alguna serie o película.

* Si como primer parámetro ponemos -u, a continuación podemos pasarle la url que queramos. Para que funcione deberá tener la misma estructura de DivXtotal.com. Por ejemplo podemos facilitarle una página concreta del mismo DivXtotal con episodios que queramos añadir a Transmission para descargar. De esa forma podremos descargar episodios que no estén en los índices generales de la web.

## Consideraciones finales

El script dxtotal podría utilizarse para descargar películas, pero no tiene mucho sentido, ya que es necesario añadir un archivo por cada película en nuestro directorio de las series que seguimos. Podría servir si estamos esperando algún estreno, crear un fichero con el título de la película que esperamos salga en DivXtotal. El problema es que el título ha de coincidir al menos con el principio del título de la web. Si hay un pequeño cambio, no se descargará.

## El futuro

Me doy cuenta que la utilidad de este script iría mejor encaminada a programar su ejecución una vez al día (por ejemplo con el comando at, o en crontab). Para ello, hace falta un sistema de información al usuario que le permita ver las descargas que se han hecho en el día. Voy a pensarlo unos días. Acepto sugerencias. Una buena forma sería integrarlo con mi otro script: "ver", que uso para ver series o películas y me ayuda a no tener que buscar yo en la carpeta transmission/completed, la cual está sobrecargada siempre de cosas. Por ejemplo que poniendo "ver --hoy" salgan las series que se han descargado desde la última vez que se ejecutó el script. En fin, a pensar.