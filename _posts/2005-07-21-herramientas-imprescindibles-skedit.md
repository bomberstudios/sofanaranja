---
id: 10
title: 'Herramientas imprescindibles: skEdit'
date: 2005-07-21T21:53:14+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=10
permalink: /2005/07/21/herramientas-imprescindibles-skedit/
categories:
  - Imprescindible
  - Software
---
Una de las grandes ventajas de ser usuario de Mac es poder usar todos los días herramientas tan maravillosas como [skEdit][1], uno de los mejores editores de HTML/XHTML/CSS/PHP que he tenido la ocasión de probar (y no han sido pocos).

skEdit es la obra maestra de [Sean Kelly][2], un chico la mar de agradable que contesta todos tus emails.

¿Y qué tiene skEdit de especial?

Pues que es uno de los editores de código más bonitos (totalmente programado en Cocoa, el entorno nativo de OSX), que es rápido, que es funcional, que no le falta ni le sobra ni una funcionalidad y que es terriblemente barato (la licencia <strong>de por vida</strong> de skEdit sólo te costará $20)

Una de las funcionalidades que me conquistó de skEdit es el 'autocomplete' inteligente (más que inteligente, yo diría que es "más listo que los ratones coloraos"). Normalmente un autocomplete te muestra una lista de términos cuando empiezas a escribir... el de skEdit no... skEdit te los muestra sin que escribas nada.

Un ejemplo: empiezas a escribir un <code>&lt;a</code> y cuando pulsas la barra espaciadora, skEdit te muestra una lista de atributos del tag 'a':

<img src="/wp-content/skedit001.png" style="border: 1px solid #666"/>

Rellenas un par de atributos, y te encuentras con sorpresas como que también autocompleta los valores de algunos atributos:

<img src="/wp-content/skedit003.png" style="border: 1px solid #666"/>

Hasta ahora, nada demasiado especial...

¿Pero qué pasa si tienes un CSS enlazado en tu HTML?

<img src="/wp-content/skedit004_01.png" style="border: 1px solid #666"/>

skEdit identifica las clases que tengas definidas para autocompletar el class!!! Lo mejor de todo es que distingue entre ID y CLASS, para que no confundas tus #footer con tus .footer.

Esta idea de autocompletar usando tus propios elementos se usa también a la hora de insertar imágenes:

<img src="/wp-content/skedit005.png" style="border: 1px solid #666"/>

Y también funciona con los <code>href</code>:

<img src="/wp-content/skedit006.png" style="border: 1px solid #666"/>

Por lo demás, el editor es una delicia de usar. Aparte del maravilloso sistema de autocomplete, otras funcionalidades de skEdit son:

* Gestor SFTP integrado
* Soporte para 'snippets' (fragmentos de código reutilizables)
* Soporte para scripts
* Integración con [HTML Tidy][3]
* Integración con CVS (y Subversion en la próxima versión)
* Navegador de funciones configurable con expresiones regulares
* Gestor de proyectos
* Code hints en PHP (y creo que también en ColdFusion)

La próxima versión (v3.6) nos traerá además pestañas (ahora mismo usa un desplegable, al estilo BBEdit), "Live Preview" y alguna que otra sorpresilla.

Creo que lo único que se le puede objetar a skEdit es que no soporte más lenguajes (aunque teóricamente se pueden implementar, pero la documentación es un pelín confusa) y quizá el "code folding" de [TextMate][4] (otro editor del que ya os contaré algo otro día)

Por todo esto (y por otros muchos motivos, entre ellos el fantástico icono), skEdit es una herramienta que no puede faltar en el arsenal de todo diseñador web (todo el que curre con Mac, se entiende), por mucho que mi querido [hermano][5] insista en que me pase a ["the one true editor"][6] :)

[1]: http://www.skti.org/skEdit.php
[2]: http://www.skti.org
[3]: http://tidy.sourceforge.net/
[4]: http://www.macromates.com
[5]: http://www.boundp.net
[6]: http://www.gnu.org/software/emacs/emacs.html