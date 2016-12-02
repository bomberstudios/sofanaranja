---
id: 215
title: Ahorrando tiempo con TextMate y Subversion
date: 2007-11-15T19:08:09+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2007/11/15/ahorrando-tiempo-con-textmate-y-subversion/
permalink: /2007/11/15/ahorrando-tiempo-con-textmate-y-subversion/
onswipe_thumb:
  - 'http://sofanaranja.com/images/plugins/onswipe/thumb/thumb.php?src=/images/2007/11/nuevo-comando-de-textmate.png&amp;w=600&amp;h=800&amp;zc=1&amp;q=75&amp;f=0'
categories:
  - Código
  - Productividad
  - TextMate
  - Trucos
tags:
  - Mac
  - Productividad
  - svn
  - TextMate
---
Como llevo una temporada sin postear, aprovecho unos segundos de tiempo libre para contaros un pequeño truco motivado por el espíritu de la Infinita Vagancia™ y el típico comentario de "molaría que TextMate hiciera..." (en este caso, de [David Alonso](http://autodidacto.com))

El truco de hoy es la típica chorrada que te molesta 80 veces al día, y cuando la resuelves te das cuenta de lo poco que nos queremos en general (resolverlo no llevó más de 2 minutos)

**Escenario:** usas [Subversion](http://subversion.tigris.org) desde línea de comando, pero escribes tus mensajes de commit con TextMate (y si no lo haces, ahora te cuento cómo)

**Problema:** cuando escribes tu mensaje de commit, tienes que guardar el documento y luego cerrarlo para que se "registre" el mensaje y se haga el commit.

**Idea:** guardar y cerrar con un atajo de teclado, pero sólo en los mensajes de commit de Subversion.


## Usando TextMate como editor de mensajes de commit

Si quieres usar TextMate para editar tus mensajes de commit, la cosa es bastante simple. Tienes que asegurarte de tener instalada la utilidad "mate" (usando el menú "Help » Terminal Usage...") y añadir esto en tu fichero .bash_profile:

    export SVN_EDITOR='mate -w'

Para ello, cuando hayas instalado 'mate' puedes abrir una ventana de Terminal.app (que por defecto inicia una sesión en tu carpeta $HOME) y escribir:

    mate .bash_profile

Se abrirá el fichero .bash_profile si existe, y si no se creará.

Añade la línea "export ..." donde quieras, cierra el fichero y cierra la ventana de Terminal.app (necesitas abrir una nueva para que el fichero .bash_profile se vuelva a leer)


## Siguiente paso: el comando de TextMate

Una de las múltiples maravillas de TextMate es el sistema de "scoping".

De una forma muy simplificada, el "scoping" es una forma de identificar qué tipo de texto estás editando. Mediante un sistema de expresiones regulares, TextMate puede reconocer en qué lenguaje estás programando; Y dentro de ese lenguaje, si estás editando un String, una función, un número...

Afortunadamente, los tipos que mantienen el bundle de Subversion tuvieron la deferencia de identificar cuándo un fichero es un mensaje de commit de Subversion.

El scope para un mensaje de commit es

    text.subversion-commit

Otra maravilla de TextMate es que puedes limitar un comando a un scope, de forma que podemos escribir un comando que sólo funcione cuando estamos editando un mensaje de commit.

Para hacer nuestra vida más fácil, vamos a crear un comando que guarde y cierre el documento actual, y asignarlo a la combinación de teclas &#x2318; + S (que ya estamos usando para guardar)

Así que abrimos el editor de Bundles con &#x2303; + &#x2325; + &#x2318; + B y creamos un nuevo comando en el bundle de Subversion:

![Nuevo Comando de TextMate](/images/2007/11/nuevo-comando-de-textmate.png)

Le asignamos un bonito nombre:

![Nombrando el Comando](/images/2007/11/nombrando-el-comando.png)

lo rellenamos de contenido:

![Comando Save and Commit](/images/2007/11/comando-save-and-commit.png)

y cerramos la ventana del Bundle Editor.

A partir de ahora, cuando escribamos

    svn ci nuestro_bello_fichero_modificado

se abrirá una ventana de TextMate con esta pinta:

![Ventana de Commit](/images/2007/11/ventana-de-commit.png)

donde podemos escribir nuestro mensaje de commit, y al pulsar &#x2318; + S para guardar, se cerrará automáticamente y empezará nuestro commit :)

Y eso es todo, de momento...