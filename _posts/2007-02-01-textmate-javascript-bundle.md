---
id: 146
title: TextMate JavaScript Bundle
date: 2007-02-01T21:55:20+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2007/02/01/textmate-javascript-bundle/
permalink: /2007/02/01/textmate-javascript-bundle/
onswipe_thumb:
  - 'http://sofanaranja.com/wp-content/plugins/onswipe/thumb/thumb.php?src=/images/2007/02/textmate-javascript-tools.png&amp;w=600&amp;h=800&amp;zc=1&amp;q=75&amp;f=0'
categories:
  - JavaScript
  - TextMate
  - Web
---
Si programas JavaScript de una manera más o menos asidua, y usas [TextMate](http://macromates.com/), **tienes** que probar el bundle "JavaScript Tools"

![Textmate Javascript Tools](/images/2007/02/textmate-javascript-tools.png)

Javascript Tools pone a tu disposición dos herramientas que (dependiendo de tu nivel programando Javascript) pueden ser una bendición o una pesadilla:

**[JSLint](http://www.javascriptlint.com/)**, un verificador de sintaxis para Javascript. JSLint detecta errores tan comunes como:

* Los ; que siempre se te olvidan al final de una línea.
* Código que nunca se ejecuta.
* `case` sin su `switch` correspondiente.
* Comentarios dentro de comentarios.
* Uso de = en comparaciones (en lugar de ==)
* Etc, etc...

**[JSMin](http://www.crockford.com/javascript/jsmin.html)**, un compresor de ficheros .js que te ahorrará un pico en tu factura de hosting.

La gracia del asunto está en que las dos herramientas se integran perfectamente con TextMate, y si tienes un error en tu código, JSLint te dirá dónde está (con un bonito enlace que te lleva a la línea y columna donde está el error).

![Jslint en Textmate](/images/2007/02/jslint-en-textmate.png)

De regalo, el bundle incluye un comando que verifica la sintaxis cada vez que guardas el fichero, mostrándote un tooltip si hay algún problema.

![Jslint en Textmate 2](/images/2007/02/jslint-en-textmate-2.png)

Así que ya tardan en [descargarse el bundle](http://www.andrewdupont.net/2006/10/01/javascript-tools-textmate-bundle/) y darle las gracias al [autor](http://www.andrewdupont.net/) :)

<div class="techtag"><span>Technorati tags:</span> <a href="http://technorati.com/tag/textmate" rel="tag">textmate</a>, <a href="http://technorati.com/tag/javascript" rel="tag">javascript</a>, <a href="http://technorati.com/tag/jslint" rel="tag">jslint</a></div>