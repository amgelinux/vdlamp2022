# Vagrant LAMP - Ubuntu Jammy

Por defecto tiene el shell zsh y el tema powerlevel10k con ayudas para Docker.

## Introducción a Hashicorp Vagrant
[Comandos a saber y plugins](https://amgelinux.github.io/vdlamp2022/)

## Acceso desde Virtualbox
- Recuerda que el usuario/contraseña es vagrant/vagrant

## Acceso al servidor Apache: 
- URL: http://192.168.33.10

## MySQL 8:
- Username: root
- Password: toor

Usa MySQL Workbench para gestionar la base de datos.


## Guias para PHP
- Como guía rápida tenemos W3Schools:
  - https://www.w3schools.com/php/default.asp
- Para ir más lento y seguro:
  - [Libro de Eugenia Bahit] (http://46.101.4.154/Libros/El%20lenguaje%20PHP.pdf)
  - este profesor tiene buenos vídeos: [Curso de PHP de pildorasinformaticas](https://youtu.be/I75CUdSJifw) 

## Web root

¡¡¡¡¡¡IMPORTANTE!!!!!!

Crea una carpeta al lado de la que contiene el fichero **Vagrantfile** que se llame **webroot**, que es el web root, compartido y mapeado en la máquina virtual en /var/www/html.


## Uso de composer
```bash
composer require components/jquery 
composer require twbs/bootstrap 
```
Escribiendo 

```bash
composer install 
```
en la carpeta **/var/www/html** de la máquina virtual se carga lo requerido en **composer.json** que está en el repositorio.

## Configuracion de PHPStorm
En proceso

## PHP 8.1

## Laravel 9
Por defecto se instalará la Laravel 9.
Para trabajar con la versión 8:
```
$ composer create-project --prefer-dist laravel/laravel NOMBREPROYECTO "8.*"
```

## Servir la aplicación
Usa un puerto distinto para cada app que vaya a estar funcionando a la vez y no olvides usar el host 0.0.0.0
```bash
$php artisan serve --host=0.0.0.0 --port 10000
```
Recuerda que esta manera de servir es para pruebas, en producción hay que configurar bien un servidor web (Apache, nginx, etc.).


