---
id: 45
title: Efecto :hover en cualquier cosa
date: 2006-01-05T20:41:40+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=45
permalink: /2006/01/05/efecto-hover-en-cualquier-cosa/
categories:
  - Código
  - CSS
  - JavaScript
---
Esta semana me preguntaron lo siguiente:

> ¿Cómo hacer un :hover en un DIV con Internet Explorer?

No sé si se suponía que debía saberlo, pero la verdad es que me pilló un poco por sorpresa...

> ¿Con #id_del_div:hover, no?

(Comentario que demuestra mi total ignorancia con respecto a las capacidades de Explorer)

> Me temo que Explorer sólo soporta :hover en los 'a'...

Como uno es de naturaleza curiosa, me puse a trastear con el dilema, llegando a la siguiente solución (que no deja de ser una chapuza, pero que no sólo funciona en Explorer sino en Camino, Firefox y Safari):

	<script>
		function replaceHover(){
			var hoverDivs = document.getElementsByTagName("div");
			for(var i=0; i<hoverDivs.length; i++){
				if(hoverDivs[i].className.indexOf('hover') != -1){
					//  ...guardamos las clases del DIV...
					var classes = hoverDivs[i].className;
					//  ...en onmouseover le añadimos una clase extra, 'hoverclass'...
					hoverDivs[i].onmouseover = function(){
						this.className += ' hoverclass';
					}
					//  ...y se la quitamos en onmouseout
					hoverDivs[i].onmouseout = function(){
						this.className = classes;
					}
				}
			}
		}
	</script>

Que quiere decir, en román paladino:

* Obtener todos los DIVs del documento
* Mirar si el DIV tiene asignada una clase CSS 'hover'
* Si es así, le asignamos un evento 'onmouseover' que le añade la clase 'hoverclass' (que tendrá alguna pijadilla del estilo de background-color: rosachicle, o algo por el estilo)
* Y ya puestos, se la quitamos cuando salga el ratón del DIV

Para disparar el cambio se llama a la función 'replaceHover' desde el 'onload' de body:

	<body onload="replaceHover()">

Obviamente, el código se puede usar con otros tags... sólo habría que cambiar el

	getElementsByTagName("div")

por

	getElementsByTagName("nombre_del_tag_que_quieras")

Pos eso... agradecimientos especiales a [Furilo][1] por darme algo en qué pensar... :D

**Update:** <a href="/2006/02/17/efecto-hover-sobre-cualquier-cosa-v20/">un método mucho más elegante usando prototype.js</a>

[1]: http://www.furilo.com