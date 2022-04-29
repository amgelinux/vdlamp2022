layout: page
title: "Intro"
permalink: /intro/

# Introducción a Vagrant

## Lecturas recomendadas
- [Documentacion de Vagrant](https://www.vagrantup.com/docs)

## Repaso de VirtualBox
Cuando se configura una máquina VirtualBox, al final se tiene:
- un fichero que contiene un disco duro virtualizado (.vdi, .vmdk, .vhd, ...) y 
- un archivo .vbox que contiene en XML (Lenguaje de Marcas) la configuración de esa máquina virtual (rutas de los archivos, parámetros de memoria, procesadores, red, etc.).

Las máquinas virtuales suelen alojarse en la **carpeta $HOME\VirtualBox VMs**, y en el menú del entorno gráfico de VirtualBox lo que aparece son las máquinas que este entorno tiene registradas.

Aparte del entorno gráfico, _VirtualBox tiene un ejecutable de línea de comandos__ que nos permite interaccionar con las máquinas virtuales sin la necesidad de usar este entorno gráfico.

## ¿Qué es Vagrant?
Vagrant es una aplicación de línea de comandos que se encarga de:
- Automatizar la descarga y aprovisionamiento de una máquina virtual en diferentes plataformas (VirtualBox, VMWare, Hyper-V, etc.)
- Controlar el estado de la máquina y permitir la interacción con ella (ssh, rdp, etc.).

**O sea, que se encarga de descargar un disco duro virtual ya creado, configurar un archivo de configuración, por ejemplo, de VirtualBox (.vbox) con los parámetros que queramos y además podemos ejecutar antes del primer uso unos scripts de aprovisionamiento para que nos quede una máquina virtual lista para desarrollar la tarea que se necesite.**

_NO TIENE INTERFAZ GRÁFICO_

## Descarga e instalación
Se descarga de la página [Hashicorp Vagrant](https://vagrantup.com) y su instalación es trivial (como si fuera VirtualBox).

## Uso

### Descarga y aprovisionamiento de la máquina virtual

Podemos crear una carpeta que se llame VagrantVMs para alojar ahí una carpeta nueva por cada máquina que vayamos a desplegar.

Se pueden descargar máquinas ya configuradas desde el enlace [Vagrant Box](https://app.vagrantup.com/boxes/search)

Una vez elegida la máquina tenemos 2 opciones:

- **OPCIÓN 1. Descargarla mediante comandos**. Estando situados en la carpeta donde se va a interaccionar con la máquina, tecleamos la orden **vagrant init ubuntu/trusty64** para descargar el archivo Vagrantfile y a continuación **vagrant up** para ejecutarla (y aprovisionarla en esta primera ejecución).
- **OPCIÓN 2. Desplegarla mediante un fichero Vagrantfile**. Estando situados en la carpeta donde se va a interaccionar con la máquina, creamos un fichero que se llame **Vagrantfile** y escribimos en él la configuración de la máquina. También debemos posteriormente teclear **vagrant up** para ejecutarla y aprovisionarla.

Vemos que en cualquier caso se trata de ejecutar el comando **vagrant up** en una carpeta donde exista un fichero con el nombre **Vagrantfile**. Dependiendo de la opción que escojamos, escribimos nosotros el Vagrantfile o el comando vagrant init escribe por nosotros un fichero con una configuración mínima (las 3 líneas de la captura anterior).

Una vez hecho esto, tenemos una máquina normal de VirtualBox que además puede ser controlada por comandos Vagrant. Los más importantes los vemos en el siguiente punto.

### Otros comandos
Estos comandos también _hay que ejecutarlos en la carpeta donde está el Vagrantfile de la máquina virtual_.
- **vagrant up** --> inicia la máquina si está parada. También si es la primera vez que se inicia la aprovisiona (ver arriba).
- **vagrant ssh** --> accedemos a una sesión ssh en la máquina. Recuerda que el usuario por defecto es vagrant y la contraseña vagrant. La mayoría de las máquinas se usarán sin necesidad de entorno gráfico. Podemos abandonar la sesión con el comando exit (en Linux).
- **vagrant halt** --> para la máquina virtual.
- **vagrant destroy** --> borra la máquina virtual.

Podemos comprobar todas estas interacciones en el entorno gráfico de VirtualBox.

### Plugins para Vagrant
Con el comando **vagrant plugin list** vemos los plugins instalados.
Son especialmente interesantes:
- **vagrant-faster**, que modifica la cantidad de CPU y memoria en función de la disponibilidad.
- **vagrant-vbguest**, que actualiza en la máquina virtual las Guest Additions.

Se instalan con el comando **vagrant plugin install NOMBRE_PLUGIN**

## Usuario y contraseña por defecto
El usuario es vagrant
La contraseña es vagrant
El teclado suele estar en inglés.

## Carpetas compartidas
Además de las carpetas compartidas que se definan en el fichero Vagrantfile, se establece una compartición entre la carpeta actual (la del Vagrantfile) de la máquina real y la carpeta /vagrant de la máquina virtual.

## Configuración de una máquina virtual ya preparada para ejecutar contenedores Docker.
Sigo la información obtenida desde este [GitHub de PeladoNerd](https://github.com/pablokbs/peladonerd/tree/master/docker/13).

Usamos el siguiente Vagrantfile:

xxxxx
