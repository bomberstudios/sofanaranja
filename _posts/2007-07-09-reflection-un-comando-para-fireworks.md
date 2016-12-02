---
id: 177
title: Reflection, un comando para Fireworks
date: 2007-07-09T08:41:58+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2007/07/09/reflection-un-comando-para-fireworks/
permalink: /2007/07/09/reflection-un-comando-para-fireworks/
onswipe_thumb:
  - 'http://sofanaranja.com/wp-content/plugins/onswipe/thumb/thumb.php?src=/images/2007/07/reflection-baby.png&amp;w=600&amp;h=800&amp;zc=1&amp;q=75&amp;f=0'
categories:
  - Código
  - Diseño
  - Software
tags:
  - code
  - Fireworks
---
Admitámoslo. El efecto "reflejo en hielo/agua/cristal" es el "bevel & emboss" de esta década.

Si alguna vez te ha tocado crear uno, sabrás que es un pelín coñazo. Si además tienes que añadir un reflejo a 50 imágenes, habrás estado al borde del suicidio.

Sobre todo si después de la paliza alguien te dice cosas como:

* "Hmm... ¿por qué los reflejos no tienen todos la misma altura?"
* "¿Sabes qué? Creo que habría que hacer los reflejos un poco más pequeños"
* "Mira... mejor vamos a cambiarlo todo por un 'drop shadow', que vuelve a estar de moda"

(situaciones estas totalmente hipotéticas)

La cuestión es que, si eres un vago profesional, esta es una de esas veces en las que piensas... "hmmm... automatización..."

Así que, con ayuda de la *terrible* documentación de Fireworks CS3, me puse a programar un comando para hacer reflejos.

El resultado es que, con un sólo click, tienes un bonito efecto como este:

![Reflection, baby](/images/2007/07/reflection-baby.png)

Bonito, ¿verdad? :)

Para conseguir este glamouroso comando, guarda el siguiente código en un fichero `Reflection.jsf` en la carpeta ~/Library/Application Support/Adobe/Fireworks CS3/Commands/ (o su equivalente en Windows que debería ser algo como C:/Documents and Settings/usuario/Application Data/Adobe/Fireworks CS3/Commands/), y luego selecciona un objeto en Fireworks y en el menú "Commands" elige la opción "Reflection".

	// Reflection Command 1.0
	// Ale Muñoz <http://bomberstudios.com>

	// Ask for shadow height:
	shadow_height = prompt("Reflection Height","50");

	// Get the original object
	original = fw.selection[0];
	original.name = "original";

	// Clone, reflect and move original
	fw.getDocumentDOM().cloneSelection();
	fw.getDocumentDOM().reflectSelection(false, true, "autoTrimImages transformAttributes");
	fw.getDocumentDOM().moveSelectionBy({x:0, y:original.height + 5}, false, false);

	// Get the cloned object
	copy = fw.selection[0]; // Current selection is now the copy
	copy.name = "copy";

	// Create the mask
	fw.getDocumentDOM().addNewRectanglePrimitive({left:copy.left - 2, top:copy.top - 2, right:copy.width + copy.left + 2, bottom:copy.height + copy.top + 2}, 0);
	// White to black gradient
	fw.getDocumentDOM().setFill({ category:"fc_Linear", ditherColors:[ "#000000", "#000000" ], edgeType:"antialiased", feather:0, gradient:{ name:"cn_Custom", nodes:[ { color:"#ffffff", isOpacityNode:false, position:0 }, { color:"#000000", isOpacityNode:false, position:1 } ], opacityNodes:[ { color:"#000000", isOpacityNode:true, position:0 }, { color:"#000000", isOpacityNode:true, position:1 } ] }, name:"Linear Smooth", pattern:null, shape:"linear", stampingMode:"blend", textureBlend:0, webDitherTransparent:false });
	// Reposition gradient
	fw.getDocumentDOM().moveFillVectorHandleBy({x:0, y:shadow_height}, "end1", true, false);

	// Get the mask
	mask = fw.selection[0];
	mask.name = "mask";

	// Remove mask's stroke
	fw.getDocumentDOM().removeBrush();

	// Apply the mask to the cloned object
	fw.selection = [copy, mask];
	fw.getDocumentDOM().group("mask to image");

	// Finally, set opacity to 30 so it looks like a reflection
	fw.getDocumentDOM().setOpacity(30);

Para usarlo, selecciona un objeto y elige la opción "Reflection" del menú "Commands".

Te pedirá que introduzcas la altura del reflejo en píxels (por defecto, 50)

Y ya está! :D

![Reflection Code Reflection](/images/2007/07/reflection-code-reflection.png)

Si encuentras algún fallo o se te ocurre alguna mejora, deja un comentario...

Y recuerda el lema de los vagos profesionales: "lo importante no es trabajar más, sino trabajar mejor" ;)