---
id: 50
title: Efecto :hover sobre cualquier cosa, v2.0
date: 2006-02-17T10:02:26+00:00
author: Ale Muñoz
excerpt: 'En respuesta a un <a href="/2006/01/05/efecto-hover-en-cualquier-cosa/#comment-59">comentario</a> en el post sobre <a href="/2006/01/05/efecto-hover-en-cualquier-cosa/">"Efecto :hover en cualquier cosa"</a>, me puse a jugar con prototype.js para ver si se podía hacer lo mismo de una forma menos farragosa.'
layout: post
guid: http://www.sofanaranja.com/?p=50
permalink: /2006/02/17/efecto-hover-sobre-cualquier-cosa-v20/
categories:
  - Código
  - JavaScript
---
En respuesta a un <a href="/2006/01/05/efecto-hover-en-cualquier-cosa/#comment-59">comentario</a> en el post sobre <a href="/2006/01/05/efecto-hover-en-cualquier-cosa/">"Efecto :hover en cualquier cosa"</a>, me puse a jugar con [prototype.js][1] para ver si se podía hacer lo mismo de una forma menos farragosa.

El resultado:

	function setHover(className,hoverClassName) {
		var hoverDivs = document.getElementsByClassName(className);
		hoverDivs = $A(hoverDivs);
		hoverDivs.each(
			function(div){
				div.onmouseover = function(){
					Element.addClassName(this,hoverClassName);
				}
				div.onmouseout = function(){
					Element.removeClassName(this,hoverClassName);
				}
			}
		);
		}
	function init (){
		setHover('hover','hoverclass');
	}
	Event.observe(window, 'load', init, false);

La idea es que a todos los elementos que queramos hacerles un hover les asignamos la clase "hover", y definimos en otra clase "hoverclass" los atributos del estado hover.

A pesar de que en el código se usa una variable llamada 'div', funciona con *cualquier* elemento de la página...

Lo que hacemos, igual que con el <a href="/2006/01/05/efecto-hover-en-cualquier-cosa/">método anterior</a>, es buscar elementos que contengan la clase 'hover', y les asignamos la clase 'hoverclass' en el evento 'onmouseover'.

Más cosillas... <code>Event.observe()</code> es la forma inteligente de asignar una función a un evento sin "manchar" el HTML de la página. En este caso le asigno la función 'init()', que se encarga de llamar a 'setHover()' con los dos parámetros que necesita (el class que he usado para definir qué elementos tienen hover, y el class que quiero usar cuando se hace rollover).

Gracias a tutiplén a <a href="http://mildiez.net/">demimismo</a> por sugerir el uso de prototype.js. Creo que estoy enamorado de otra librería :D


[1]: http://prototype.conio.net/