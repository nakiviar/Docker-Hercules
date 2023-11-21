# Docker-Playground
Primeros pasos para aprender Docker :)

## Conceptos basicos

Comencemos con los conceptos básicos:

- Contenedor:
Un contenedor es una unidad ejecutable ligera que contiene una aplicación y sus dependencias, junto con la configuración del entorno necesario para ejecutarla. Los contenedores son aislados entre sí y del sistema operativo subyacente.

- Imagen: 
Una imagen Docker es un paquete ejecutable que incluye todo lo necesario para ejecutar una aplicación, incluyendo el código, las bibliotecas, las dependencias y la configuración. Las imágenes se utilizan como base para crear contenedores. Si queremos hacer una analogia con programacion orientada a objetos, la imagen seria como la clase, y cuando ejecutas una imagen, creas una instancia de esa imagen, y esa instancia se llama un "contenedor" que seria el simil al objeto.

- Dockerfile:
Un Dockerfile es un archivo de texto que contiene las instrucciones para construir una imagen Docker. Define cómo se debe construir una imagen, qué sistema operativo base usar, qué aplicaciones instalar y cómo configurar el entorno.

- Registro Docker (Docker Hub):
Un registro Docker es un repositorio centralizado para almacenar y compartir imágenes Docker. Docker Hub es un registro público, pero también puedes usar registros privados para gestionar tus propias imágenes.

- Docker Compose:
Es una herramienta para definir y gestionar aplicaciones Docker multi-contenedor. Utiliza un archivo docker-compose.yml para describir la configuración de la aplicación.

- Orquestación de Contenedores:
La orquestación de contenedores es el proceso de gestionar y coordinar múltiples contenedores que trabajan juntos como parte de una aplicación. Herramientas como Docker Compose y Kubernetes son utilizadas para facilitar la orquestación.

## Instalacion

Para empezar a utilizar Docker en tu máquina local solo hay que instalar [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/) , el cual requiere de que actives la virtualizacion en tu PC (enable hardware virtualization) e instales WSL2. Por si se preguntan para que sirve el WSL2, esta permite ejecutar contenedores Docker basados en Linux , ya que es una característica de Windows que permite ejecutar un sistema operativo Linux en paralelo con Windows sin necesidad de una máquina virtual.
Ademas permite una mejor interoperabilidad entre el entorno Windows y el entorno Linux. Puedes ejecutar comandos de Linux directamente desde la terminal de Windows, y viceversa.


> Nota para la instalacion. Al instalar Docker Desktop, obtienes tanto el cliente de Docker (interfaz de línea de comandos que te permite interactuar con Docker) como el daemon de Docker (el proceso en segundo plano que gestiona los contenedores). Además, Docker Desktop incluye una interfaz gráfica de usuario que facilita la visualización de contenedores, imágenes y otros recursos de Docker.

## Primeros comandos
