||Manual de Usuario – Autenticación Universal||
| :-: | :-: | :- |
![Image result for profuturo logo](http://integrandoequipos.com/blog/wp-content/uploads/2017/10/Logo-Profuturo.png)![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.001.png)![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.002.png)

![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.003.png)![Image result for profuturo logo](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.004.png "Logo-Profuturo")

## **Manual de integración**
Motor de Autenticación Universal (Web)
![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.005.png)![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.006.png)**


||||
| :- | :- | :- |

||Manual de Usuario – Autenticación Universal||
| :-: | :-: | :- |
![Image result for profuturo logo](http://integrandoequipos.com/blog/wp-content/uploads/2017/10/Logo-Profuturo.png)![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.007.png)![](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.002.png)

# Contenido
` `TOC \o "1-3" \h \z \u [Manual de integración	 PAGEREF _Toc86337634 \h 1](C:\Users\egarcser\Downloads\MAU_Web_Manual_de_integración.docx#_Toc86337634)

[Contenido	 PAGEREF _Toc86337635 \h 2](#_Toc86337635)

[1. Introducción	 PAGEREF _Toc86337636 \h 2](#_Toc86337636)

[Contenido del MAU Web	 PAGEREF _Toc86337637 \h 3](#_Toc86337637)

[Integración con canales Web	 PAGEREF _Toc86337638 \h 3](#_Toc86337638)

[Invocación del MAU	 PAGEREF _Toc86337639 \h 5](#_Toc86337639)


-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

# 1. Introducción
Como parte de las acciones de Profuturo para continuar impulsando la Transformación Digital e incrementar el nivel de atención al cliente; surge el *Motor de Autenticación Universal*, en respuesta a la necesidad de garantizar la seguirdad de los trámites digitales. 

El *MAU* (Motor de Autenticación Universal) tiene como objetivo identificar a cada persona de forma única e incorporar diferentes factores de autenticación, para ofrecer servicios seguros y a distancia por medio de todos los canales de contacto Profuturo.​

En los siguientes capítulos, encontrarás varias guías que facilitan el uso del *Motor de Autenticación Universal.* 
# Contenido del MAU Web
El MAU Web es un proyecto desarrollado empleando lenguaje Javascript y el framework VueJS. El proyecto se ha diseñado de forma que puede integrarse con facilidad en cualquier canal Web Profuturo que se requiera. Las funcionalidades que se integran dentro del MAU Web son las siguientes:
-
- - Autenticación mediante token, ya sea mediante el envío de un correo electrónico o mediante un mensaje de texto a un número celular determinado.
- - Autenticación facial, en el cual se realizan tomas de imágenes del rostro (*selfie*) y capturas de la identificación. En este flujo se integra además el SDK de Facephi que permite la validación de rostro vs identificación.

Todos los flujos dentro del MAU Web hacen uso de las APIs que integran Autenticación Universal y las cuales se alojan dentro de un único producto en el API Manager y cuyo repositorio de datos central es la Base de Autenticación Universal (*BAU*)

![Diagrama

Descripción generada automáticamente](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.008.png)

**Figura  SEQ Figura \\* ARABIC 1 Arquitectura del MAU Web**
# Integración con canales Web
El proyecto VueJS está conformado por un conjunto de directorios, clasificados de acuerdo con la funcionalidad. El código del proyecto se ubica dentro del directorio **src**.

![Imagen de la pantalla de un video juego

Descripción generada automáticamente con confianza baja](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.009.png)

**Figura  SEQ Figura \\* ARABIC 2 Directorios del Proyecto**
-
- - **assets:** contiene las fuentes y los íconos que se emplean en las vistas.
- - **components:** contiene los componentes que pueden ser reutilizados en otras vistas, tales como cabeceras, pies de páginas, barras de progreso, modales, entre otros.
- - **mixins:** contiene utilizades para el desencriptado de información, especialmente utilizado para el flujo de autenticación facial.
- - **router:** aquí se alberga el archivo index.js, el cual define los mapeos de las rutas para cada vista dentro del proyecto.
- - **services:** son un conjunto de archivos JS que contiene las funciones con la lógica de negocio para cada flujo, cada archivo hace alusión a una funcionalidad, y cada archivo contiene una serie de funciones que tienen en común un objetivo específico.
- - **store:** este directorio es de especial importancia ya que contiene un conjunto de archivos JS que definen ciertas propiedades de algunos objetos, y esta información se comparte de manera global, es decir, es posible modificar estas propiedades desde cualquier vista.
- - **styles:** contiene los estilos scss para los componentes del proyecto
- - **utilities:** contiene las utilidades especificas para el módulo de autenticación facial.
- - **views:** es** otra de los directorios con gran importancia ya que alberga cada una de las vistas que conforman el motor de autenticación web.

Además del directorio src, se encuentra el directorio ***public,*** el cual contiene todas las herramientas para el uso de widgets de FacePhi.

MAU está preparado para funcionar en dos formas, en modo desarrollo, pensado para ejecutarse localmente y visualizarse directamente en el navegador, y el modo productivo, el cual está preparado para integrarse en alguno de los canales Web de Profuturo.
## **Invocación del MAU**
MAU está pensado para funcionar de manera local o como su nombre lo indica, en el ambiente de desarrollo de Profuturo. Esto es especialmente útil cuando se trata de validar el funcionamiento del MAU Web.

Por otro lado, se encuentra el modo productivo, el cual recibe los parámetros por medio de eventos desde la aplicación padre.

Para ejecutar el proyecto de manera local es necesario ejecutar el siguiente comando (también puede ejecutarse dentro de un contenedor)

***npm run serve***

Al finalizar el despliegue, se puede abrir el navegador, si es en ambiente local, la dirección será localhost, o si es en el ambiente de desarrollo de Profuturo, la dirección será <https://motor-autenticacion-universal-ssl-autenticacionuniversal-dev.apps.paasprofuturo-d.r6b1.p1.openshiftapps.com/> 

Para el modo desarrollo es necesario enviar en la URL los siguientes parámetros:
-
- - curp: curp del cliente
- - env: ambiente, en el caso de desarrollo es ***dev.***
- - ptoken: token de la aplicación padre
- - rftoken [opcional]: token de registro factor
- - cuenta: número de cuenta del cliente.

De forma que la URL para consultar el MAU, queda de la siguiente forma:

<https://motor-autenticacion-universal-ssl-autenticacionuniversal-dev.apps.paasprofuturo-d.r6b1.p1.openshiftapps.com/autenticacion?curp=XXXX910915MDFRRR03&env=dev&ptoken=384a7b3c6e1d45d3e2e38baf0e9e4dbd&rftoken=a9c96d35f2674d19f88d99976b412793&cuenta=0000000000>

Además de los datos que se obtienen de los parámetros nombrados anteriormente, se requieren datos relacionados con el proceso y el origen del trámite. Dentro del modo de desarrollo existen unos valores por defecto, estos se almacenan en la *store* del objeto *userProcess (src/store/userProcess.js)*. Por tal motivo siempre que se invoque el motor de autenticación se tendrán los mismos datos. 

Los datos son **origen, proceso y subproceso**, que por defecto tienen los valores 34, 226, 405. Esto nos permite tener un flujo con la autenticación facial y autenticación por token habilitada. 

En cualquier caso, es posible que mientras no se configuren certificados adecuados, la primera página que se observe sea una advertencia de seguridad como la siguiente.

En el ambiente productivo, tanto los datos del usuario como los datos del proceso se reciben del evento, para no exponer los datos en la URL.

![Interfaz de usuario gráfica, Texto, Aplicación, Correo electrónico

Descripción generada automáticamente](Aspose.Words.9a6e1bf2-507c-42f4-a4ea-55cdb6cf37a7.010.png)

**Figura  SEQ Figura \\* ARABIC 3 Advertencia de seguridad MAU Web**

Para poder acceder, hay que desplazarse hasta la parde final de la página y dar clic en la leyenda que dice *“Acceder a motor-autenticacion-universal-ssl-autenticacionuniversal-dev.apps.paasprofuturo-d.r6b1.p1.openshiftapps.com (sitio no seguro)”* 



||||
| :- | :- | :- |

