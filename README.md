# PPS-Unidad1Actividad1-MansurSY
Actividad 1 de la Unidad 1 de Puesta en Producción Segura. Tabajaremos con los Entornos de Desarrollo

Tenemos varios objetivos:

> [Crear un entorno de desarrollo Eclipse con docker](#Eclipse-Docker)

> [Instalar extensiones en un IDE](#Instalar-extensiones)

> [Probar los entornos de Desarrollo](#Prueba-entornos) 
---
## Eclipse Docker

En [este enlace](https://hub.docker.com/r/dockeruc/eclipse) puedes encontrar podemos crear un contenedor docker con un entorno IDE Eclipse

Lee bien las instrucciones y ten en cuenta que tienes que hacer varias operaciones. Las que tienes a continuación son de un entorno Linux:

1. Crear las carpetas necesarias:
~~~
sudo mkdir -p  $HOME/docker/eclipse/datos
sudo chown -R $(whoami) $HOME/docker/eclipse
sudo chgrp -R $(whoami) $HOME/docker/eclipse
~~~

![](/imagenes/C1.png)

2. Configurar el entorno gráfico 

~~~
export DISPLAY=:0
startxwin -- -listen tcp &
xhost + 
~~~

![](/imagenes/C2.png)

3. Lanzar el contenedor

~~~
sudo docker run -ti --rm \
           -e DISPLAY=$DISPLAY \
	       -e artifactory_host='IP:PUERTO'\
		   --name eclipse \
           -v /tmp/.X11-unix:/tmp/.X11-unix \
           -v `pwd`:/workspace \
           -v $HOME/docker/eclipse/datos:/home/developer \
           dockeruc/eclipse	

~~~
 
![](/imagenes/C3.png)

![](/imagenes/C4.png)

> __Explica el comando docker que has utilizado__

## Instalar extensiones

Las extensiones de un IDE nos van a facilitar la labor de programar, hacer más flexible nuestro IDE, además de hacer nuestros código más seguro.
Tenemos muchas extensiones, tanto para lenguajes de programación específicos como para el IDE.

__Las siguientes operaciones las puedes hacer desde el entorno Eclipse que hemos creado o puedes utilizar el IDE que prefieras en tu equipo__
>__Busca cuáles son las mejores extensiones de eclipse para programadores y las añades desde la tienda de tu IDE__

Python:

Editor: Microsoft
    Funcionalidades: Soporte para depuración, IntelliSense, linters, ejecución de scripts, Jupyter Notebook, y más.

Pylance:

Editor: Microsoft
    Funcionalidades: Provee un mejorado soporte de IntelliSense y análisis estático rápido y preciso para Python.

Jupyter:

Editor: Microsoft
    Funcionalidades: Permite trabajar con Jupyter Notebooks directamente en VS Code.

AutoDocstring:

Editor: Nils Werner
    Funcionalidades: Genera automáticamente docstrings para funciones y clases.

Python Docstring Generator:

Editor: Nils Werner
    Funcionalidades: Facilita la creación de docstrings siguiendo el formato estándar.

Python Test Explorer for Visual Studio Code:

Editor: Little Fox Team
    Funcionalidades: Integra un explorador de pruebas para ejecutar y depurar pruebas unitarias de Python.

isort:

Editor: Microsoft
    Funcionalidades: Ordena automáticamente las importaciones de Python en tu código.

Black:

Editor: Joscha Feth
    Funcionalidades: Aplica formateo automático al código según el estilo "Black".

flake8:

Editor: Microsoft
    Funcionalidades: Linter que ayuda a mantener la calidad del código.

Python Type Hint:

Editor: Acme Corp
    Funcionalidades: Agrega sugerencias de tipo a tu código Python, ayudando en la detección temprana de errores.

CodeQL:

Editor: GitHub
    Funcionalidades: Permite realizar análisis de seguridad estáticos en tu código, detectando vulnerabilidades y errores.

ESLint:

Editor: Microsoft
    Funcionalidades: Aunque es más general, ESLint puede ser configurado con reglas de seguridad específicas para detectar patrones peligrosos en el código JavaScript.

TruffleHog3:

Editor: Roger Villarreal
    Funcionalidades: Busca secretos como claves API y contraseñas en tu código, evitando exposiciones accidentales.

Dependency Analytics:

Editor: Red Hat
    Funcionalidades: Analiza las dependencias del proyecto para detectar vulnerabilidades conocidas en bibliotecas y paquetes.

GitLens:

Editor: GitKraken
    Funcionalidades: Aunque es principalmente para la gestión de Git, GitLens ayuda a rastrear cambios de código que podrían introducir vulnerabilidades.

Docker:

Editor: Microsoft
    Funcionalidades: Útil para quienes trabajan con contenedores, facilitando la configuración segura de entornos Docker.

REST Client:

Editor: Huachao Mao
    Funcionalidades: Permite hacer pruebas de API directamente en VS Code, lo que es útil para pruebas de penetración en servicios web.

VulnCost:

Editor: Snyk
    Funcionalidades: Muestra las vulnerabilidades conocidas en las dependencias de tu proyecto a medida que escribes código.

>__ Busca y escribe para qué sirven estos plugins: Checkstyle, Sonar Lint.__

Checkstyle: Herramienta para verificar que el código Java cumpla con estándares de codificación, mejorando la calidad y mantenibilidad.

SonarLint: Extensión para IDEs que detecta en tiempo real problemas de calidad y seguridad en el código, proporcionando correcciones sugeridas.

>__Instala los plugins y complementos que has encontrado. Además busca e instala los plugins Checkstyle y Sonar Lint.__

![](/imagenes/C5.png)

![](/imagenes/C6.png)

![](/imagenes/C7.png)

![](/imagenes/C8.png)

## Prueba entornos

El entorno de desarrollo nos sirve para crear nuestras aplicaciones y además podemos comprobar los errores que tienen, problemas de seguridad, etc. por lo que desde allí vamos a poder corregirlos.
>__Descarga el código fuente de un proyecto java o python: compila, enlaza y ejecutaló. Tienes algunos ejemplos en la carpeta Sources de este repositorio__
>__Utiliza las herramientas de depuración de Eclipse o Netbeans para depurar el proyecto, y las diferentes extensiones para ver información, problemas, etc.__

Primero seleccionamos el archivo de prueba de calculadora.py y en el menu izquierdo le damos a depurar y ejecutar

![](/imagenes/C9.png)

![](/imagenes/C10.png)

En el terminal de abajo nos muestra los problemas o las recomendaciones en mi caso solo muestra una recomendacion generada por sonarqube

![](/imagenes/C11.png)

---
## ENTREGA
>__Crea un repositorio  con nombre PPS-Unidad1Actividad1-Tu nombre que contenga las respuestas a las preguntas y las evidencias de que has realizado las operaciones indicadas.__

>__Sube a la plataforma, tanto el repositorio comprimido como la dirección a tu repositorio de Github.__
