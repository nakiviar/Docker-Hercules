# Docker-Playground
Primeros pasos para aprender Docker :)

![Getting-started-with-Docker](https://github.com/nakiviar/Docker-Playground/assets/54564415/040eec04-0a58-420a-b206-2446e2d5467d)


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

> [!NOTE]
> Nota para la instalacion. Al instalar Docker Desktop, obtienes tanto el cliente de Docker (interfaz de línea de comandos que te permite interactuar con Docker) como el daemon de Docker (el proceso en segundo plano que gestiona los contenedores). Además, Docker Desktop incluye una interfaz gráfica de usuario que facilita la visualización de contenedores, imágenes y otros recursos de Docker.

## Primeros comandos

> [!NOTE]
> Podemos probar los comandos de docker sin tener instalado nada en el local, usando [Play With Docker](https://labs.play-with-docker.com/)

Probemos primero si se instalo correctamente, para ello comprobamos la version:
```diff
docker --version
```
Luego vamos a ejecutar el siguiente comando, para verificar que docker esta funcionando bien:

```diff
docker run hello-world
```
![image](https://github.com/nakiviar/Docker-Playground/assets/54564415/007a1ff2-27fe-4ebb-b019-fa834b2975cc)


1. **El cliente de Docker contactó al daemon de Docker**: Docker funciona en un modelo cliente-servidor. El cliente de Docker es la interfaz que utilizas para interactuar con Docker, y el daemon de Docker es el proceso que gestiona los contenedores. En este paso, el cliente se comunicó con el daemon para ejecutar la acción que le indicaste.

2. **El daemon de Docker descargó la imagen "hello-world" desde Docker Hub**: Docker Hub es un registro público de imágenes Docker. Cuando ejecutaste docker run hello-world, el daemon notó que no tenía la imagen "hello-world" localmente, así que la descargó desde Docker Hub. La imagen "hello-world" es una imagen de prueba comúnmente utilizada para verificar la instalación de Docker.

3. **El daemon de Docker creó un nuevo contenedor a partir de esa imagen**: Una vez que la imagen "hello-world" estuvo disponible localmente, el daemon creó un nuevo contenedor a partir de esa imagen. Un contenedor es una instancia en ejecución de una imagen Docker.

4. **El daemon de Docker transmitió la salida del contenedor al cliente**:El contenedor "hello-world" ejecutó un programa simple que generó el mensaje que estás leyendo. El daemon transmitió esta salida al cliente de Docker, que a su vez la mostró en tu terminal.

Creamos un contenedor en base a una imagen existente desde su ultima version:
```diff
docker run nginx
```
![docker_nginx](https://github.com/nakiviar/Docker-Playground/assets/54564415/cc00e9e1-5135-4640-8321-bc14b263bd2b)

Este es un contenedor que se queda escuchando en un puerto por defecto que es el puerto 80. Esto pasa porque los contenedores gnix  se basan en el servidor web Nginx, que está diseñado para escuchar en una conexión TCP/IP. Esto significa que cualquier cliente que se conecte al contenedor en el puerto 80 podrá acceder al servidor web Nginx.

Creamos un contenedor en base a una imagen existente desde una version especifica:
```diff
docker run nginx:[version]
```
para detener el proceso, se usa el ```Ctrl + C```

> [!NOTE]
> Cuando le das Ctrl+C a un contenedor que se está ejecutando, estás enviando una señal SIGINT al proceso principal del contenedor. Esta señal indica al proceso que se detenga de forma inmediata.
> El proceso principal de un contenedor gnix es el servidor web Nginx. 
> En el caso de los contenedores hello-world, el proceso principal es un shell.


Listar todas las imagenes:
```diff
docker images
```
![docker_images](https://github.com/nakiviar/Docker-Playground/assets/54564415/4a34d50d-ee60-4f8b-aa5e-90982218408c)

Listar imagenes por repositorio:
```diff
docker images [repositorio]
```
![docker_images_with_repo](https://github.com/nakiviar/Docker-Playground/assets/54564415/a424cad0-1b05-41eb-b504-1226b5813fe7)

Listar los contenedores que se estan ejecutando actualmente:
```diff
docker ps
```
![docker_ps](https://github.com/nakiviar/Docker-Playground/assets/54564415/95134415-ec28-49f6-80f1-ba57b4a6ac31)

Listar los contenedores activos como tambien los que estan detenidos:
```diff
docker ps -a
```
![docker_psa](https://github.com/nakiviar/Docker-Playground/assets/54564415/68b825f6-2cc9-47dd-ac04-5d37c202f2fa)

eliminar el contenedor por el nombre o id:
 
```diff
docker rm [nombre_del_contenedor]
docker rm [id_del_contenedor]
docker rm [id_del_contenedor_tres_primeras_letras]
```
![docker_rm](https://github.com/nakiviar/Docker-Playground/assets/54564415/05344ac1-5492-4cf0-98f9-1004bc131cf0)

eliminar una o más imágenes de Docker de su sistema:

```diff
docker rmi [nombre_del_contenedor]
```
![docker_rmi](https://github.com/nakiviar/Docker-Playground/assets/54564415/683829e9-c03f-43fd-a04a-be6ef44d4cc0)

> [!WARNING]
> Para eliminar la imagen, primero debes detener y eliminar los contenedores existentes.
> ![docker_error_rmi](https://github.com/nakiviar/Docker-Playground/assets/54564415/fc10a925-5527-4753-b8eb-286e967beb4f)
