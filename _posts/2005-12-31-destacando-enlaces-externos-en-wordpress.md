---
id: 42
title: Destacando enlaces externos en WordPress
date: 2005-12-31T21:15:49+00:00
author: Ale Muñoz
excerpt: El viejo truco de destacar los enlaces externos de tu blog, con ejemplos de código para WordPress.
layout: post
guid: http://www.sofanaranja.com/?p=42
permalink: /2005/12/31/destacando-enlaces-externos-en-wordpress/
categories:
  - Código
  - JavaScript
  - WordPress
---
Hay pequeños detalles que hacen la vida de los visitantes de tu blog un poco más agradables. Uno de ellos es destacar de alguna manera qué enlaces son internos (es decir, conducen a otra página de tu web) y cuáles son externos (conducen a un sitio distinto).

Para Sofá Naranja quería añadir esta funcionalidad. Empecé a buscar plugins para WordPress, pero al cabo de un rato llegué a la conclusión de que ninguno me convencía demasiado, y acabé programando un hack que hace lo mismo.

El resultado que quería conseguir es este:

<img src='/images/external_vs_internal_link.png' alt='Enlace interno y externo' style="border: 1px solid #ccc" />

Los enlaces externos son del mismo color, pero les añado un pequeño icono a la derecha.

Para no meterme demasiado en las tripas del monstruo, y para hacer algo portable, decidí trastear un poco con JavaScript.

La idea de mi script es la siguiente:

* Recorro todos los tags <code>&lt;a href...&gt;</code>
* Miro si el enlace contiene la URL de mi blog.
* Si no es así, le aplico un estilo CSS.

Aquí va la cosa:

	var links = document.getElementsByTagName('a');
	for(var i=0 ; i < links.length; i++){
		var link = links[i];
		if(link.href.indexOf('sofanaranja.com') == -1){
			//	es un enlace externo
			link.style.paddingRight = "10px";
			link.style.backgroundImage = "url(/images/aoutside.gif)";
			link.style.backgroundPosition = "right center";
			link.style.backgroundRepeat = "no-repeat";
		}
	}

Lo que hago es asignar a la variable </code><code>links</code> todos los tags <code>&lt;a ...&gt;</code> de la página. Luego voy mirando si el <code>href</code> del enlace contiene la URL de mi blog con <code>indexOf()</code>, que devuelve -1 si no se ha encontrado la cadena.

Una vez localizado un enlace externo, sólo falta cambiar los atributos CSS. Esto se hace accediendo a los atributos con <code>objeto.style.nombreDelAtributo</code>

Hay que decir que los nombres de atributos en JavaScript no son exactamente iguales que en CSS. Imprescindible usar esta lista de conversión de [propiedades CSS a atributos de JS][cssjs].

Ahora viene la gran pregunta: ¿y cuándo se ejecuta esto?

Yo lo he puesto en el evento <code>onload</code> de <code>body:</code>

	<script type="text/javascript">
		function init(){
			var links = document.getElementsByTagName('a');
			for(var i=0 ; i < links.length; i++){
				var link = links[i];
				if(link.href.indexOf('sofanaranja.com') == -1){
					//	es un enlace externo
					link.style.paddingRight = "10px";
					link.style.backgroundImage = "url(images/aoutside.gif)";
					link.style.backgroundPosition = "right center";
					link.style.backgroundRepeat = "no-repeat";
				}
			}
		}
	</script>
	<?php wp_head(); ?>
	</head>
	<body onload="init()">

Este cambio lo he puesto en el fichero <code>header.php</code> de mi tema de WordPress, para que funcione en todas las páginas del blog (incluyendo las que no son posts).

El icono es gentileza de [web-graphics.com][1].

[cssjs]: http://codepunk.hardwar.org.uk/css2js.htm
[1]: http://www.web-graphics.com/mtarchive/000305.php#000305