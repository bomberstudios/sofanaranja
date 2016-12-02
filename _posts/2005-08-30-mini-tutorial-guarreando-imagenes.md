---
id: 25
title: 'Mini-tutorial: Guarreando Imágenes'
date: 2005-08-30T20:00:52+00:00
author: Ale Muñoz
excerpt: |
  Siguiendo la línea didáctica del Mini-tutorial de AJAX, hoy le toca el turno a otro tema del que hablaba hace unos días: el guarreo de imágenes.
  
  En esta ocasión vamos a ver cómo potrear imágenes para tener un look grunge-que-te-cagas por el método manual. Siempre existe la opción de usar el Machine Wash, pero hacerlo a mano es más divertido y te permite más control sobre el resultado final.
  
  Sin más leches, aquí va un mini-tutorial de cómo se hace.
layout: post
guid: http://www.sofanaranja.com/?p=25
permalink: /2005/08/30/mini-tutorial-guarreando-imagenes/
categories:
  - Diseño
---
Jelou...

Siguiendo la línea didáctica del Mini-tutorial de AJAX, hoy le toca el turno a otro tema del que hablaba hace unos días: el guarreo de imágenes.

En esta ocasión vamos a ver cómo potrear imágenes para tener un look grunge-que-te-cagas por el método manual. Siempre existe la opción de usar el Machine Wash, pero hacerlo a mano es más divertido y te permite más control sobre el resultado final.

Sin más leches, aquí va un mini-tutorial de cómo se hace.


## Lo que queremos conseguir ##

La idea es pasar de esto:

<img src='/wp-content/050830001.jpg' alt='' />

a esto:

<img src='/wp-content/050830002.jpg' alt='' />


## Empezamos ##

Vamos a necesitar lo siguiente:

  * Una imagen para guarrear
  * Una textura de fondo, preferentemente un pelín asquerosa (papel antiguo, una pared cochambrosa...)
  * Unos pinceles especiales para dibujar agujeros, rotos, desconchones... Hay algunos muy buenos en [Dubtastic][1]
  * 15 minutillos
  * Un Photoshop :)

Os adjunto un fichero con las imágenes que voy a usar en este tutorial: [Tutorial-guarreo][2]


## Vamos al lío ##

Empezamos abriendo nuestra imagen original. Cuando lo hagamos, convertiremos la capa "Background" en una capa transparente haciendo doble click en el nombre y cambiando "Background" por cualquier otra cosa:

<img src='/wp-content/050830003.png' alt='' /> ------> <img src='/wp-content/050830004.png' alt='' />

Ahora abrimos nuestra imagen de textura y la pegamos detrás de la imagen original.

Para que se vea la textura de fondo, tenemos dos opciones:

  * Cambiarle la transparencia a la capa original
  * Cambiar el modo de la capa original.

Para este tutorial, voy a cambiar el modo de la capa original, de "Normal" a "Multiply".

<img src='/wp-content/050830005.png' alt='' />

El efecto de cada modo depende de las imagenes que tengamos en cada capa. Con las imágenes de este tutorial, el efecto es algo parecido a esto:

<img src='/wp-content/050830006.jpg' alt='' />

con lo que ya le hemos echado 30 años encima a la imagen original :)

Ahora lo que nos queda es potrearla un poquito para darle ese aspecto de "mira lo que acabo de encontrarme en el baúl de mi bisabuela".

Para ello, la técnica más aceptada es la siguiente:

  * Seleccionamos la capa con la imagen original
  * Creamos una nueva capa de máscara del tipo "Reveal All"

<img src='/wp-content/050830007.jpg' alt='' />

Una capa de máscara sirve para mostrar u ocultar partes de la imagen sin borrarlas del original.

La paleta de capas ahora tendrá esta pinta:

<img src='/wp-content/050830008.png' alt='' />

A partir de ahora, para editar la imagen original tendremos que hacer click en el pincel de la capa, y para editar la máscara haremos click en el círculo.

Ahora es cuando podemos empezar a guarrear la imagen.

Seleccionamos algún pincel asqueroso (este es del Set 001 de Dubtastic):

<img src='/wp-content/050830009.png' alt='' />

Y empezamos a borrar un poco (yo suelo poner la opacidad de la herramienta de borrar al 10% para que el efecto no sea demasiado bestia)

<img src='/wp-content/050830010.png' alt='' />

Aquí ya me empezado a cargar una esquina... :P

El resto no tiene ningún misterio... ir borrando en la máscara, cambiando de pincel, hasta que la imagen tenga una pinta realmente asquerosa...

Y poco más, la verdad... :D


[1]: http://www.dubtastic.com/resources.php
[2]: http://www.sofanaranja.com/wp-content/tutorialguarreo.zip