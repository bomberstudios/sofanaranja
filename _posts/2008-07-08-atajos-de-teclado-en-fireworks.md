---
id: 247
title: Atajos de teclado en Fireworks
date: 2008-07-08T12:23:59+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/?p=247
permalink: /2008/07/08/atajos-de-teclado-en-fireworks/
onswipe_thumb:
  - 'http://sofanaranja.com/wp-content/plugins/onswipe/thumb/thumb.php?src=/images/2008/07/picture-85.png&amp;w=600&amp;h=800&amp;zc=1&amp;q=75&amp;f=0'
categories:
  - Código
  - Productividad
tags:
  - Fireworks
---
Ya he comentado en alguna ocasión que en [la Gran Corporación](http://the-cocktail.com) somos fans de Fireworks. Tengo pendiente un post más detallado explicando por qué, pero de momento aquí va un pequeño adelanto : )

Independientemente del software que utilices, ya sabrás que los atajos de teclado son el mejor aliado de la productividad y la vagancia.

Lo que a lo mejor no sabes es que los atajos de teclado de Fireworks, además de ser personalizables de una forma bastante sencilla, pueden asignarse a tus propios comandos.

Para personalizar los atajos de teclado, abre el menú **Fireworks » Keyboard Shortcuts...**

![Panel de asignación de atajos de teclado de Fireworks](/images/2008/07/picture-85.png)

Puedes seleccionar varios grupos de atajos por defecto (Illustrator, Freehand, Photoshop...) para que no tengas que reaprender lo que ya sabes, y puedes guardar tu propio set personalizado (ideal para transportarlo de un equipo a otro si usas varios ordenadores)

Si te fijas en el panel verás que aparece el menú "Commands", que es donde se encuentran cosas como [Reticulator](http://sofanaranja.com/reticulator/) y otros comandos personalizados:

![Panel de atajos con teclas personalizadas](/images/2008/07/picture-86.png)

Si seleccionas un item de menú podrás asignarle la combinación de teclas que más rabia te de, y lo mejor es que el atajo funcionará *siempre* (ahora veremos por qué esto es importante)

### Un ejemplo práctico (al menos para mi : )

Una cosa que siempre me ha molestado de Fireworks (y de Illustrator, y de Freehand, y de...) es que no es fácil cambiar el color de una selección sin hacer malabarismos con el ratón. Tienes que moverlo a donde tengas la paleta de colores, seleccionar el color, y luego volver a donde estabas. Si además tienes las paletas ocultas la operación es un coñazo. Y en el caso de Fireworks, si tienes un texto seleccionado el 90% de las veces te lo acabarás cargando al darle a TAB para mostrar las paletas.

Solución: un comando de Fireworks, claro : )

Guarda el fichero [Show Color Picker.jsf](http://code.sofanaranja.com/fwcommands/Color/Show%20Color%20Picker.jsf) en tu carpeta de comandos (en Mac es `~/Library/Application Support/Adobe/Fireworks CS3/Commands/`)
y asígnale un atajo de teclado (yo he usado `Ctrl + Shift + C`). A partir de ahora, cuando quieras cambiar el color de **cualquier cosa** sólo tienes que pulsar el atajo de teclas, y un bello selector de color aparecerá en la posición donde tengas el ratón:

![Show Color Picker en acción](/images/2008/07/picture-82-480x300.png)

Aún tengo que arreglar un par de bugs, a saber:

* <del>si el objeto seleccionado no tiene relleno, inexplicablemente no funciona con el color #FFFFFF (con todos los demás si). Esto parece un bug de Fireworks, pero tengo que confirmarlo.</del> Bug corregido! Es un fallo de Fireworks, pero he encontrado un bonito "workaround" :P
* si usas el comando con una selección de texto se colorea toda la caja de texto y no sólo la selección. Más que un bug es un "así funciona Fireworks", pero ya tengo más o menos claro cómo resolverlo, sólo es cuestión de tiempo.

Espero que os sea útil!