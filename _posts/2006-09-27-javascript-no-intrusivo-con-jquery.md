---
id: 101
title: Javascript no intrusivo con jQuery
date: 2006-09-27T01:26:21+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/?p=101
permalink: /2006/09/27/javascript-no-intrusivo-con-jquery/
categories:
  - Código
  - JavaScript
  - Web
---
Tenía a [jQuery](http://jquery.com) en mi lista de “cosas que tengo que probar un día de estos” desde hace tiempo.

Para un proyecto que [tenemos](http://the-cocktail.com), he empezado a trastear con esta librería, y los resultados (inmediatos) me han dejado muy buen sabor de boca.

Vamos con unos ejemplitos de lo que sabe hacer jQuery:

### Lista de resultados “con pijama”...

Este es un quebradero de cabeza clásico, para el que se han planteado muchas soluciones. La que he encontrado, usando los [selectores CSS + DOM de jQuery](http://jquery.com/docs/) es tan simple que casi da miedo:

	$("#lista ul li:even").addClass("even");

Que viene a decir: “dentro del div #lista, me seleccione todos los li impares dentro de un ul, y les añada la clase 'even'”

El HTML que estoy usando es bastante limpito:

	<div id="lista">
		<ul>
			<li>Elemento 1</li>
			<li>Elemento 2</li>
			<li>Elemento 3</li>
			<li>Elemento 4</li>
		</ul>
	</div>

Pero dejarlo así sería desaprovechar toda la potencia de jQuery (y manchar un poco el HTML, en realidad). Así que, después de mirar un rato (10 minutos) la documentación, me encuentro con que puedo dejar mi HTML tal que así:

	<ul>
		<li>Elemento 1</li>
		<li>Elemento 2</li>
		<li>Elemento 3</li>
		<li>Elemento 4</li>
	</ul>

¿Y entonces cómo sé a qué lista tengo que ponerle el pijama? Aquí es donde entra en juego toda la potencia de los pseudo-selectores de jQuery (el li:even) es uno de ellos, pero hay [muchos más](http://jquery.com/docs/Base/Expression/Custom/)

	$(body ul:first li:even).addClass("even");

Que es como decir: “le añada la clase 'even' a los li impares de la primera ul que aparezca en el body” (en este caso he hecho trampa, porque sé que mi ul será la primera que aparezca en el documento)

### Añadir un icono a los enlaces externos...

Este es un asunto que ya visitamos en un artículo anterior ([Destacando enlaces externos en WordPress](/2005/12/31/destacando-enlaces-externos-en-wordpress/))

Usando jQuery hay varias maneras de hacer esto, pero voy a elegir una particularmente curiosa: usar una expresión XPath.

	$("//a[not(contains(@href,'sofanaranja.com'))]").addClass("externo");

Esto sería el equivalente a “busca todos los elementos 'a' cuyo atributo src no contenga la cadena 'sofanaranja.com', y les añades la clase 'externo'”.

(Lo de escribir expresiones XPath se sale un poco de la temática del post... : )

### Javascript no intrusivo

Como vemos con este par de ejemplitos, los selectores de jQuery nos permiten hacer toda clase de perrerías (tanto en presentación como en comportamiento) sobre el DOM de nuestro documento sin (practicamente) guarrear el HTML.

Usando jQuery no hay excusa para ese crimen que es

	... href="javascript:abreVentana()" ...

Me temo que seguiré comentando las bondades de jQuery una temporadita :D

### Por qué me gusta jQuery, personalmente

  * Porque ocupa poco (15Kb comprimida)
  * Porque no le sobra nada, y lo poco que le falta es, casi siempre, innecesario :)
  * Porque la [documentación](http://jquery.com/docs/) está actualizada, bien escrita, y tiene ejemplos claros de qué se puede hacer y cómo.
  * Porque seleccionar elementos del DOM usando selectores CSS y [XPath](http://www.w3.org/TR/xpath) es droga dura: una vez que lo pruebas no puedes vivir sin ello.

#### Recursos interesantes...

Para trabajar con XPath, hace tiempo me encontré con [AquaPath](http://www.ditchnet.org/aquapath/), una utilidad para Mac que vale su peso en oro...