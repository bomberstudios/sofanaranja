---
id: 148
title: Trucos con SSH
date: 2007-02-15T21:55:57+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2007/02/15/trucos-con-ssh/
permalink: /2007/02/15/trucos-con-ssh/
onswipe_thumb:
  - SKIP
categories:
  - Código
---
Si trabajas habitualmente con servidores remotos, probablemente ya [te estés autentificando con llaves RSA](http://www.inwebwetrust.net/inwebwetrust/post/2006/09/26/exportar-contrasenas-ssh).

Pero lo que quizá no supieras es que en tu carpeta $HOME/.ssh/ puedes configurar algunos atajos para tus servidores habituales.

La cosa es tan simple como crear un fichero 'config' en $HOME/.ssh/ y añadir esto:

	Host sn
	HostName sofanaranja.com
	User nombre_de_usuario

A partir de entonces, puedes usar el atajo 'sn' para acceder al servidor sofanaranja.com usando SSH:

	ssh sn

y no tendrás que preocuparte de añadir el nombre de usuario o el nombre de host.

También funciona con SCP:

	scp mi_fichero.png sn:www/img

y para ejecutar comandos remotos:

	ssh sn ls www/img

(que te dará un listado de todos los ficheros remotos en www/img)

Si tienes más de un servidor "favorito" (estoy pensando en la [Ruby Room](http://www.lacoctelera.com/rubyroom/) y su [colección de máquinas con nombres atómicos](http://www.lacoctelera.com/nando/tags/the-shaker-club/posts)) la cosa es tan fácil como separar cada host en el fichero por una línea en blanco:

	Host sn
	HostName sofanaranja.com
	User nombre_de_usuario

	Host bs
	HostName bomberstudios.com
	User nombre_de_usuario

Yo no es que tenga muchas máquinas... según [DreamHost](http://www.dreamhost.com/r.cgi?899) todos mis sitios (unos 15) están en 4 máquinas. Lo que pasa es que como dijo aquel: ["Good Programmers Are Lazy And Dumb"](http://blog.outer-court.com/archive/2005-08-24-n14.html). Trabajar menos, en mi opinión, es una obligación moral de todo el que use ordenadores ;)

Y para terminar, otra gran cita:

> "I am rarely happier than when spending an entire day programming my computer to perform automatically a task that it would otherwise take me a good ten seconds to do by hand" -- Douglas Adams