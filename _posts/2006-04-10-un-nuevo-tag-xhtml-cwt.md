---
id: 58
title: 'Un nuevo tag XHTML: CWT'
date: 2006-04-10T15:01:15+00:00
author: Ale Muñoz
excerpt: |
  Es un hecho demostrado de la vida profesional de cualquiera que trabaje con clientes el que, antes o después, tendrás que producir algo con lo que no estás de acuerdo.
  
  La discrepancia puede ir desde el inofensivo "el color no es apropiado" hasta el demoledor "este proyecto no tiene ningún sentido", pasando por toda una gama de emociones que, a veces, cuesta trabajo describir...
layout: post
guid: http://www.sofanaranja.com/?p=58
permalink: /2006/04/10/un-nuevo-tag-xhtml-cwt/
categories:
  - Código
  - Diseño
  - Freak
---
Es un hecho demostrado de la vida profesional de cualquiera que trabaje con clientes el que, antes o después, tendrás que producir algo con lo que no estás de acuerdo.

La discrepancia puede ir desde el inofensivo "el color no es apropiado" hasta el demoledor "este proyecto no tiene ningún sentido", pasando por toda una gama de emociones que, a veces, cuesta trabajo describir...

Comoquiera que el desarrollador web es un ser social (léase: nos encanta mirar lo que andan haciendo nuestros compañeros de profesión para "inspirarnos"), a veces surge la necesidad de justificar ante nuestra audiencia el por qué de una tipografía infernal, un icono horrible, o toda una paleta de colores sin sentido aparente...

El gran inconveniente de trabajar para clientes (aparte de trabajar para clientes), es que normalmente suele ser poco interesante ser un bocazas. Publicar en un foro o en tu blog que los colores de tu último trabajo surgieron de la retorcida mente de algún "middle manager" incapaz de asumir que el hecho de que a su mujer le encante el rosa no constituye un argumento de peso para cambiar el color de un site es contraproducente. Por no decir que es una grosería. O algo peor...

Pero tus compañeros de profesion **deben** saber que tú jamás serias capaz de presentarle al mundo tal tutti-frutti de tipos y colores sin tener pesadillas por las noches... Que tu preparación y años de estudio te impiden pasar a producción un diseño sin retícula sin que se te abra la úlcera... En definitiva, que si algo no está perfecto, definitivamente, no es porque no seas capaz de hacerlo, sino porque han intervenido "causas de fuerza mayor"

Es por ello (oye) que desde Sofá Naranja proponemos una extensión a la especificación XHTML 1.1, en forma de tag:

## El <del>tag</del> elemento &lt;cwt/&gt; ##
El nombre 'cwt' viene del inglés "Client Wanted This" ("el cliente pidió ésto"). Está en inglés por el mismo motivo por el que están en inglés todos los tags de (X)HTML: porque el Esperanto no tuvo mucho éxito, y escribir un parser de tags multilenguaje habría llevado a Microsoft a la ruina.

Es un tag que convertirá tus páginas en código no válido (aunque si necesitas usarlo lo más probable es que de todas formas no valide).

La función del tag 'cwt' es marcar aquellas partes de tu site que, lejos de ser el resultado de un sesudo análisis, son producto de ese ente despiadado que convenimos en llamar "El Cliente".

Es un tag estríctamente semántico. No tiene representación visual, aunque si estás usando tags 'cwt' en tu código, quizá estés tentado de añadir el siguiente código en tu CSS:

	cwt {
		display: none !important;
	}

a pesar de que (mientras el W3C no apruebe el tag 'cwt') no servirá para nada...

### Veamos un ejemplo... ###

Este era tu código antes del 'cwt':

	<table width="768px">
		<tr>
			<td><img src="/images/spacer.gif" width="768" height="1" /></td>
		</tr>
	</table>


y éste es tu código después del 'cwt':

	<cwt>
		<table width="768px">
			<tr>
				<td><img src="/images/spacer.gif" width="768" height="1" /></td>
			</tr>
		</table>
	</cwt>

Ahora tus compañeros sabrán que dejaste de maquetar usando tablas hace años, y que en este caso sólo lo hiciste porque tienes que pagar una hipoteca...

Desencadenado por: <a href="http://www.clientcopia.com/">nadie en particular, de momento</a>.

<a href="http://furilo.com">Furilo</a> me comenta que el 'cwt' es un candidato perfecto para convertirse en un <a href="http://www.microformats.org">microformato</a>. Seguiremos informando si finalmente nos liamos la manta a la cabeza y lo proponemos como un standard :D

**Update:** Gracias a <a href="http://simplelogica.net/logicola/">mort</a> por la puntualización sobre 'tag' vs 'elemento'. Y veo que lo del microformato va a haber que ir planteándoselo en serio... :D

**Update 2:** En breve con todos ustedes, <a href="http://clientwantedthis.com">clientwantedthis.com</a> :D