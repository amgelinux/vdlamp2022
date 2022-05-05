# Vagrant LAMP - Ubuntu Jammy

## Introducción
Este proyecto pretende diseñar una máquina virtual en VirtualBox para programar aplicaciones web desde Windows 10.
Todo nuestro trabajo se guardará en carpetas compartidas con Windows, la máquina se puede borrar y ser creada de nuevo en cualquier momento sin perder nuestro trabajo.
Elimina la necesidad de utilizar la aplicación WAMP en Windows, Docker Desktop, WSL, etc.

## Características

### IP
Le damos la ip 192.168.33.10 y es sólo visible desde nuestro equipo.

### Hashicorp Vagrant
Usa Vagrant para desplegar la máquina virtual.
[Comandos de Vagrant necesarios y plugins](https://amgelinux.github.io/vdlamp2022/)

### Shell
Por defecto tiene el shell zsh y el tema [powerlevel10k](https://github.com/romkatv/powerlevel10k) con ayudas para los comandos de Docker, entre otras cosas.
Es conveniente usar una [Nerd Font](https://www.nerdfonts.com/) en el programa de consola que utilicemos para acceder por ssh a la máquina para ver todos los iconos.

### Virtualbox
- Al final lo que tenemos es una máquina VirtualBox, pero recuerda que el usuario/contraseña es vagrant/vagrant y que conviene entrar mediante el Terminal de Windows. No deberíamos usar el entorno gráfico de VirtualBox.

### Servidor Apache: 
- Funcionando en la URL: http://192.168.33.10

### Web root
¡¡¡¡¡¡IMPORTANTE!!!!!!
Crea una carpeta al lado de la que contiene el fichero **Vagrantfile** que se llame **webroot**, que es el web root, compartido y mapeado en la máquina virtual en /var/www/html.

### MySQL 8.1:
- Username: root
- Password: toor
Puedes usar [MySQL Workbench](https://www.mysql.com/products/workbench/) para gestionar la base de datos.
Se pasará a un contenedor Docker por si queremos usar diferentes versiones y facilitar el backup de datos.

### PHP 8.1
Ficheros de configuración:
- 
- 

#### Guias para PHP
- Como guía rápida tenemos W3Schools:
  - https://www.w3schools.com/php/default.asp
- Para ir más lento y seguro:
  - [Libro de Eugenia Bahit] (http://46.101.4.154/Libros/El%20lenguaje%20PHP.pdf)
  - [Curso de PHP de pildorasinformaticas](https://youtu.be/I75CUdSJifw) 


### Uso de composer
```bash
composer require components/jquery 
composer require twbs/bootstrap 
```
Escribiendo 

```bash
composer install 
```
en la carpeta **/var/www/html** de la máquina virtual se carga lo requerido en **composer.json** que está en el repositorio.

### Configuracion de PHPStorm
[Configurando PHPStorm](https://amgelinux.github.io/vdlamp2022/config_phpstorm)

### Laravel 9
Por defecto se instalará la Laravel 9.
Para trabajar con la versión 8, que es la que usaremos en clase:
```
$ composer create-project --prefer-dist laravel/laravel NOMBREPROYECTO "8.*"
```

*Para servir la aplicación*
Usa un puerto distinto para cada app que vaya a estar funcionando a la vez y no olvides usar el host 0.0.0.0

```bash
$php artisan serve --host=0.0.0.0 --port 10000
```
Recuerda que esta manera es para pruebas, en producción hay que configurar bien un servidor web (Apache, nginx, etc.).


