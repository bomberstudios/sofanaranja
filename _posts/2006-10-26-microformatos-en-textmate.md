---
id: 122
title: Microformatos en TextMate
date: 2006-10-26T23:59:11+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2006/10/26/microformatos-en-textmate/
permalink: /2006/10/26/microformatos-en-textmate/
categories:
  - TextMate
  - Web
---
Acabo de enviar a la lista de correo de [TextMate](http://macromates.com/) mi pequeña contribución al desarrollo de los [Microformatos](http://microformats.org/): un bundle de TextMate con dos snippets para [hCalendar](http://microformats.org/wiki/hcalendar) y [hCard](http://microformats.org/wiki/hcard), que harán tu vida un pelín más fácil si quieres empezar a trastear con la "web semántica en minúsculas".

Puedes bajarte el bundle [aquí](/dl/Microformats.zip).

Y esto es un pequeño screencast de cómo funciona:

<script src="http://sofanaranja.com/js/swfobject.js" type="text/javascript" charset="utf-8"></script>
<div id="flashplayer">
	Si estás leyendo este post usando un lector de feeds, puede que tengas que visitar la web para ver el vídeo...
</div>
<script type="text/javascript">
	// <![CDATA[
	var so = new SWFObject("/flvplayer.swf", "sotester", "544", "500", "6", "#cccccc");
	so.addVariable("file", "http://sofanaranja.com/dl/microformate.flv");
	so.addVariable("watermarkPath", "http://sofanaranja.com/images/sn-tv-flat");
	so.write("flashplayer");
	// ]]>
</script>

Intentaré ir ampliando el bundle con otros microformatos (hReview es el próximo) y haciéndolo un pelín más inteligente (lo de componer timestamps a mano en hCalendar acaba resultando un poco pesado :)

**Update:** He creado un [repositorio de Subversion para el bundle](http://sofanaranja.com/subversion/textmate/bundles/microformate/). Iré actualizándolo con ideas que han propuesto en la lista... El acceso de lectura es público (sin usuario ni contraseña). Para hacer un checkout del bundle:

	svn co http://sofanaranja.com/subversion/textmate/bundles/microformate/

(o usa mi cliente favorito de Subversion después de la línea de comando y el propio TextMate: [ZigVersion](http://zigversion.com/))

<div class="techtag"><a href="http://technorati.com/tag/textmate" rel="tag">textmate</a>, <a href="http://technorati.com/tag/microformatos" rel="tag">microformatos</a></div>