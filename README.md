# MOD-DEVOPS-CON-NODE.JS

## Ejercicio 1
Desplegada la app que desarrollé en la práctica del módulo “Programación Backend con Node” en un servidor Ubuntu de la plataforma Amazon Web Services (AWS). 

La **URL de acceso** es: 

http://ec2-13-48-52-119.eu-north-1.compute.amazonaws.com/legopop/anuncios

Para la puesta en producción he seguido la arquitectura indicada en el enunciado de la práctica. 

He realizado las siguientes acciones:
- Configuración del servidor Ubuntu indicando que dispone de espacio en disco de 8 GB. La IP se configura para que sea fija, siendo la 13.48.52.119. Los puertos abiertos son el 22 para protocolo SSH y el 80 para HTTP. Se generan la clave pública-privada para permitir el acceso al administrador del sistema, usuario Ubuntu. 
- Instalación de  Advanced Package Tool (APT) para facilitar la instalación de paquetes en Ubuntu.
- Instalación de Nginx. Se usa en el servidor como servidor web y como proxy inverso para redirigir las peticiones por DNS a Node. 
- Instalación de Node Version Manager (NVM) para gestionar las versiones e instalación de Node
- Instalación de Node.
- Instalación de Legopop. Para realizar una instalación no relajada, se crea el usuario “node” para copiar los ficheros de la app en su home. Se realiza un git clone desde el repositorio de Github. Nginx se configura para que sirva directamente las imágenes y las hojas de estilo para mejorar el rendimiento. Además se le añade a la cabecera el valor: “mariadelamareria”, para las comprobaciones del profesor.
- Instalación y configuración de PM2 como gestor de procesos. Se añade la app Legopop a los procesos gestionados. PM2 se encarga de mantenerla activa, tanto en el caso de caídas de la aplicación, como en el caso de reinicio del servidor.
- Instalación y securización de MongoDB.  Se crea la base de datos legopopdb y se da permisos de acceso a legopopusr. Se crea la cadena de conexión a la base de datos, asignándosela a una variable de entorno para facilitar su uso desde Legopop.
- Se modifican los módulos de Legopop de conexión a la base de datos. Usan la cadena de conexión oportuna, recogiéndola desde la variable de entorno DATABASE_URI.
- Se rellena la base de datos legopopdb.

## Ejercicio 2

Se instala y configura la web “Stylish Portfolio” copiada de startbootstrap.com. 

La **URL de acceso** es:

http://13.48.52.119/

Para la puesta en producción se han seguido los siguientes pasos:

- Creación de usuario website,  en su home se copian los ficheros de la app.
- Descarga de la web Stylish portfolio y carga en el servidor con el comando scp.
- Configuración de Nginx para el acceso a la app. Creación del fichero website en sites-available y establecimiento de enlace simbólico desde sites-enabled.
