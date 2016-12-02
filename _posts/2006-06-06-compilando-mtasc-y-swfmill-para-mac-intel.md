---
id: 75
title: Compilando MTASC y Swfmill para Mac Intel
date: 2006-06-06T13:16:34+00:00
author: Ale Muñoz
excerpt: |
  Ultimamente estoy revisando mi sistema de trabajo para proyectos de ActionScript.
  
  Una de las primeras opciones ha sido usar MTASC junto con Swfmill (y un bonito sistema usando un Rakefile en Ruby, pero esa es otra historia...)
  
  Las primeras pruebas de compilación fueron bastante alentadoras, pero me encontré con la siguiente sorpresa:
  
  Mi PowerBook 12" 1.3Ghz compila un 50% más rápido que un iMac Dual Core a 2Ghz!
  
  En este post está la solución :D
  
  <strong>Update:</strong> Los binarios están disponibles para descargar...
layout: post
guid: http://sofanaranja.com/?p=75
permalink: /2006/06/06/compilando-mtasc-y-swfmill-para-mac-intel/
categories:
  - Código
  - Mac
  - Software
---
**Note:** The post is available in English [here][english]

### El problema

Ultimamente estoy revisando mi sistema de trabajo para proyectos de ActionScript.

Una de las primeras opciones ha sido usar [MTASC][mtasc] junto con [Swfmill][swfmill] (y un bonito sistema usando un Rakefile en Ruby, pero esa es otra historia...)

Las primeras pruebas de compilación fueron bastante alentadoras, pero me encontré con la siguiente sorpresa:

**Mi PowerBook 12" 1.3Ghz compila un 50% más rápido que un iMac Dual Core a 2Ghz!**
<!-- more -->

Lo primero que hice fue comprobar que estaba usando la misma versión de MTASC y Swfmill en los dos sistemas. Y descubrí que en el PowerBook estaba usando una versión más antigua de MTASC. Al actualizarla, la diferencia era aún mayor...

Lo siguiente era averiguar si, como me temía, la última versión de MTASC no estaba optimizada para procesadores Intel:

	AleMac:~ ale$ file bin/mtasc
	bin/mtasc: Mach-O executable ppc

Lo que me temía...

Y Swfmill?

	AleMac:~ ale$ file bin/swfmill
	bin/swfmill: Mach-O executable ppc

Fantástico...

### La solución

Como uno es un poco freak, la solución obvia era recompilar MTASC y Swfmill (grandes ventajas del Open Source :) para Mac Intel.

Si pensaste que era fácil, estás equivocado. Aquí tienes la crónica de cómo compilar MTASC y Swfmill en Tiger para Mac Intel sin pegarte un tiro...


### Requisitos ###

  * Apple Developer Tools (incluídas en los CDs/DVDs del sistema operativo)
  * [DarwinPorts][dp] 1.2.1
  * [Código fuente de Swfmill 0.22.11][swfmill-src]
  * [GODI][godi]
  * [Script de instalación de MTASC][mtasc-src]

### Instalando dependencias

Primero actualizamos los paquetes de DarwinPorts

	sudo port -d selfupdate
	Password:
	DEBUG: Rebuilding the darwinports base system if needed.
	Synchronizing from rsync://rsync.darwinports.org/dpupdate/dports
	receiving file list ... done

Para compilar MTASC y Swfmill necesitamos instalar una serie de paquetes usando DarwinPorts:

  * zLib
  * pkgconfig
  * libxml2
  * libxslt
  * freetype
  * libpng
  * gdbm

A compilar!

	sudo port install zlib
	sudo port install pkgconfig
	sudo port install libxml2
	sudo port install libxslt
	sudo port install freetype
	sudo port install libpng
	sudo port install gdbm

Esto debería tardar unos 10 minutillos (en un iMac Dual Core 2.0Ghz)

También es necesario instalar OCaml y findlib.

OCaml está en la lista de paquetes de DarwinPorts, pero no findlib, así que lo haremos usando [GODI][godi]

### Instalando OCaml y findlib con GODI

Primero nos bajamos el código fuente de [GODI][godi-src] y lo descomprimimos donde nos de más coraje. Yo voy a ponerlo en ~/src (un directorio 'src' en mi carpeta home)

Para compilar GODI, hay que configurar un par de cositas...

	cd /Users/ale/src/godi-bootstrap-20060405/
	./bootstrap --prefix $HOME/src/godi

Y empezamos a compilar... Los binarios se instalarán en ~/src/godi/bin y ~/src/godi/sbin, así que habrá que añadir esas dos rutas al PATH (y si no sabes cómo se hace, quizá no deberías haber llegado hasta aquí :)

Y ahora es cuando empieza lo divertido:

	cd /Users/ale/src/godi-bootstrap-20060405/
	./bootstrap_stage2

Tras un tiempo prudencial (6 minutos tardó esto...) tendremos un compilador de OCaml nativo para Mac Intel, y GODI listo para empezar a instalar paquetes... Para ello, ejecutamos 'godi_console' y nos buscamos la vida para instalar:

  * godi-findlib
  * conf-tcltk
  * conf-gdbm
  * godi-ocaml-dbm
  * godi-ocaml-all

Ahora ya estamos listos para empezar a compilar MTASC (si, esto no ha hecho más que empezar...)

### Compilando MTASC

Comparado con lo que hemos hecho hasta ahora, compilar MTASC es un juego de niños...

Nos bajamos el script de instalación de MTASC desde aquí: [http://www.mtasc.org/doc/mtasc/install.ml][mtasc-src]

Yo lo he guardado en ~/src/mtasc

	cd /Users/ale/src
	mkdir mtasc
	cd mtasc
	curl http://tech.motion-twin.com/doc/mtasc/install.ml -o install.ml

Y ahora viene lo más divertido, que es parchear 'install.ml' para que compile en OSX. Para ello, buscamos la línea que dice

	let zlib = match Sys.os_type with "Win32" -> "zlib.lib" | _ -> "-lz"

por algo parecido a esto:

	let zlib = "/opt/local/lib/libz.a"

(que es donde DarwinPorts instala zLib por defecto...)

Ahora compilamos MTASC:

	ocaml install.ml

Con un poco de suerte, cuando terminen de pasar líneas a toda velocidad por la pantalla, tendrás dos ejecutables: 'mtasc' y 'mtasc-byte' en la carpeta 'mtasc/bin'

La prueba de fuego...

	AleMac:~/src/mtasc/bin ale$ file mtasc
	mtasc: Mach-O executable i386
	AleMac:~/src/mtasc/bin ale$ file mtasc-byte
	mtasc-byte: Mach-O executable i386

Woohoo! :D

Ahora vamos a intentar compilar Swfmill

### Compilando Swfmill

Descomprimimos los fuentes de Swfmill en ~/src

	tar xvzf swfmill-0.2.11.tar.gz

Yo no he conseguido que compile sin hacer la siguiente chapuza: buscar en todos los ficheros la cadena '-static' y sustituirla por '' (Teóricamente bastaría con poner --disable-static en configure, pero por algún motivo pasa del tema...)

Y ahora configuramos con las siguientes opciones:

	./configure --prefix=$HOME

y compilamos...

	make

Cuando acabe, tendremos un bonito binario en src/swfmill-0.2.11/src

De nuevo, la prueba del algodón:

	AleMac:~/src/swfmill-0.2.11/src ale$ file swfmill
	swfmill: Mach-O executable i386

### Rescatando el fruto de nuestro trabajo

Ahora, lo ideal sería poner nuestras nuevas versiones de MTASC y Swfmill en algún sitio fuera de los directorios donde los hemos compilado...

Yo los he metido en ~/bin, que es un directorio que tengo en el PATH.

### ¿Merece la pena?

Bueno... pues aquí van unas pruebecillas de rendimiento en un pequeño test que tengo montado con MTAS + Swfmill, comparando la versión descargable de MTASC con la versión "native" y "bytecode", compiladas en Intel.

La prueba consistió en compilar 4 veces seguidas midiendo el tiempo de compilación con el comando 'time'. Mi proyectillo usa la opción '-keep', con lo que las compilaciones a partir de la primera son más rápidas. Entre medición y medición se eliminaron todos los .swf

#### MTASC PowerPC + Swfmill PowerPC

	real    0m1.020s
	user    0m0.649s
	sys     0m0.352s

	real    0m0.197s
	user    0m0.073s
	sys     0m0.026s

	real    0m0.101s
	user    0m0.073s
	sys     0m0.025s

	real    0m0.103s
	user    0m0.073s
	sys     0m0.024s

#### MTASC "native" Intel + Swfmill Intel

	real    0m0.568s
	user    0m0.150s
	sys     0m0.072s

	real    0m0.105s
	user    0m0.073s
	sys     0m0.025s

	real    0m0.103s
	user    0m0.073s
	sys     0m0.026s

	real    0m0.101s
	user    0m0.073s
	sys     0m0.025s

#### MTASC "bytecode" Intel + Swfmill Intel

	real    0m0.227s
	user    0m0.156s
	sys     0m0.061s

	real    0m0.102s
	user    0m0.073s
	sys     0m0.025s

	real    0m0.102s
	user    0m0.073s
	sys     0m0.026s

	real    0m0.101s
	user    0m0.073s
	sys     0m0.026s

Creo que sobran las palabras... :D

Pues eso... ¡que lo disfruten!

**Nota:** Si alguien tiene algún proyecto gordo donde se puedan hacer pruebas más contundentes (el mío es sólo un test) le agradecería que pusiera sus comentarios, o que me enviara código a ale {arrobilla} bomberstudios {puntillo} com

**Update:** Ante el clamor popular, aquí están los binarios compilados:

  * <a href="/dl/mtasc-1.12.native-macintel.zip">mtasc-1.12.native-macintel.zip</a> 288Kb
  * <a href="/dl/mtasc-1.12.bytecode-macintel.zip">mtasc-1.12.bytecode-macintel.zip</a> 172Kb (esta es la versión que va más rápido en mi sistema...)
  * <a href="/dl/swfmill-0.2.11-macintel.zip">swfmill-0.2.11-macintel.zip</a> 1,6Mb

Los binarios son **sólo** para Mac Intel (no son Universales) y sólo los he probado en 2 equipos. Se agradecerán comentarios si funcionan en más cacharros...

[dp]: http://darwinports.opendarwin.org/
[mtasc]: http://mtasc.org
[mtasc-src]: http://tech.motion-twin.com/doc/mtasc/install.ml
[swfmill]: http://iterative.org/swfmill/
[swfmill-src]: http://iterative.org/swfmill/releases/swfmill-0.2.11.tar.gz
[godi]: http://godi.ocaml-programming.de
[godi-src]: http://www.ocaml-programming.de/packages/godi-bootstrap-20060405.tar.gz
[english]: http://bomberstudios.com/2006/06/07/compiling-mtasc-and-swfmill-for-intel-mac/