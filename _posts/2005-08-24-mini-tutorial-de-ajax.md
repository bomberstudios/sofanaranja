---
id: 24
title: Mini-tutorial de AJAX
date: 2005-08-24T15:46:13+00:00
author: Ale Muñoz
excerpt: 'Sofá Naranja, en su empeño por acercar la tecnología al pueblo, presenta un mini-tutorial sobre el palabro de moda: AJAX. Si andabas buscando una excusa para trastear con AJAX, la acabas de encontrar. AJAX es fácil. AJAX es potente. AJAX lava más blanco. AJAX es, en definitiva, una Cosa Guapa™'
layout: post
guid: http://www.sofanaranja.com/?p=24
permalink: /2005/08/24/mini-tutorial-de-ajax/
onswipe_thumb:
  - SKIP
categories:
  - Código
  - JavaScript
---
Sofá Naranja, en su empeño por acercar la tecnología al pueblo, presenta un mini-tutorial sobre el palabro de moda: AJAX. Si andabas buscando una excusa para trastear con AJAX, la acabas de encontrar. AJAX es fácil. AJAX es potente. AJAX lava más blanco. AJAX es, en definitiva, una Cosa Guapa™


## ¿Qué es AJAX? ##

AJAX son las siglas de _Asynchronous JavaScript And XML_. Es una colección de tecnologías que permiten desarrollar webs altamente interactivas ahorrando ancho de banda y recargas de página.

La clave para el funcionamiento de AJAX es el objeto XMLHttpRequest (uno de los pocos inventos útiles de Microsoft, mira por dónde)

Actualmente, AJAX funciona en los siguientes navegadores:

  * Mozilla y familia
  * Internet Explorer Windows (a partir de la versión 5)
  * Safari y familia (en teoría, no tengo un Konqueror para probar)

Más información en la [Wikipedia][2]


## Qué necesitamos para este tutorial ##

  * Un editor de texto
  * Un servidor web
  * Café (opcional)
  * Unos 30 minutillos

Vamos a construir una página web simple, donde cargaremos datos a partir de otra sin necesidad de recargar la página actual. También veremos como darle al usuario un poco de "feedback" de qué está pasando. Con suerte, también nos tomaremos un café.


## Empezamos ##

La cosa empieza suave. Vamos a crear un fichero HTML (que en un derroche de originalidad llamaremos 'index.html') con el siguiente contenido (véase que somos unos pedantes y vamos a usar sintaxis XHTML 1.1 pata negra):

**index.html**

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
	<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="es">
		<head>
			<meta http-equiv="content-type" content="text/html; charset=utf-8" />
			<title>Mini-tutorial AJAX</title>
		</head>
		<body>
			<h4>Mini-tutorial AJAX</h4>
			<div id="detalles"></div>
		</body>
	</html>

Como vemos, nada del otro mundo. Nótese el detalle de que tenemos un DIV vacío, al que le hemos asignado un ID único. Es en este DIV donde vamos a cargar nuestro contenido dinámico.


## Complicando el tema ##

Ahora vamos a crear el objeto XMLHttpRequest, que será el encargado de actualizar el contenido dinámico de nuestro DIV 'detalles'.

Creamos un fichero (que, recurriendo a nuestra creatividad habitual, llamaremos 'ajax.js'):

**ajax.js**

	//	Vamos a presuponer que el usuario es una persona inteligente...
	var isIE = false;
	//	Creamos una variable para el objeto XMLHttpRequest
	var req;
	//	Creamos una funcion para cargar los datos en nuestro objeto.
	//	Logicamente, antes tenemos que crear el objeto.
	//	Vease que la sintaxis varia dependiendo de si usamos un navegador decente
	//	o Internet Explorer
	function cargaXML(url) {
		//	Primero vamos a ver si la URL es una URL :)
		if(url==''){
			return;
		}
		//	Usuario inteligente...
		if (window.XMLHttpRequest) {
			req = new XMLHttpRequest();
			req.onreadystatechange = processReqChange;
			req.open("GET", url, true);
			req.send(null);
		//	...y usuario de Internet Explorer Windows
		} else if (window.ActiveXObject) {
			isIE = true;
			req = new ActiveXObject("Microsoft.XMLHTTP");
			if (req) {
				req.onreadystatechange = processReqChange;
				req.open("GET", url, true);
				req.send();
			}
		}
	}

Bien. De momento tenemos una función que crea un objeto XMLHttpRequest (con una u otra sintaxis, dependiendo del navegador) y le asigna la función 'processReqChange' al evento 'onreadystatechange' (que ahora explicaremos qué quiere decir :)

También hemos usado el método 'open' de XMLHttpRequest (que se usa para asignarle la dirección URL de donde va a cargar los datos) y el método 'send' (que se usa para efectuar la llamada a la URL asignada con 'open')

Nos vamos a detener un poco en la sintaxis de 'open':

	open('metodo','URL',modo-asincrono,'usuario','password');

Los dos primeros parámetros son obligatorios. 'metodo' puede ser GET o POST, modo-asincrono es un booleano (TRUE|FALSE) que indica si la llamada será asíncrona (se seguiran ejecutando scripts en la página mientras se cargan los datos) o no (se detendrá la ejecución de los scripts hasta que se complete la carga de datos). 'usuario' y 'password' son, sorprendentemente, el usuario y el password a usar si la URL requiere autentificación

Seguimos...

Ahora declararemos la función processReqChange:

	function processReqChange(){
		//    Referencia a nuestro DIV con ID unica:
		var detalles = document.getElementById("detalles");
		//    Si se ha completado la carga de datos, los mostramos en el DIV...
		if(req.readyState == 4){
			detalles.innerHTML = req.responseText;
		} else {
			//    ...en caso contrario, le diremos al usuario que los estamos cargando:
			detalles.innerHTML = '<img src="loading.gif" align="absmiddle" /> Cargando...';
		}
	}

processReqChange es una función que se ejecuta cada vez que se dispara el evento 'onreadystatechange' del objeto XMLHttpRequest. ¿Y cuando se dispara este evento? Pues, como su propio nombre indica, cada vez que cambia el estado del objeto. Este evento le asigna al objeto XMLHttpRequest una variable ('readyState') que puede tener los siguientes valores (puede tener más, pero es que si no esto no sería un mini-tutorial):

  * 0 = no inicilizado (por ejemplo, cuando acabamos de crear el objeto)
  * 1 = cargando datos (hemos llamado al método 'send' del objeto)
  * 4 = carga completada (ya podemos acceder a los datos que nos ha devuelto el servidor)

Entonces, cada vez que cambie la variable 'readyState' miramos si es igual a 4 (carga completada), y si es así metemos el contenido del objeto XMLHttpRequest

	req.responseText

en nuestro DIV

	detalles.innerHTML = req.responseText


## Integrando el script ##

Ahora vamos a enlazar el JavaScript con el HTML (por aquello de que funcione, y tal... es que si no no tiene gracia...)

**index.html**

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
	<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="es">
		<head>
			<meta http-equiv="content-type" content="text/html; charset=utf-8" />
			<title>Mini-tutorial AJAX</title>
			<script src="ajax.js" language="JavaScript"></script>
		</head>
		<body>
			<h4>Mini-tutorial AJAX</h4>
			<div id="detalles"></div>
		</body>
	</html>

Bien... ahora nos falta llamar a la función 'cargaXML' de alguna forma. En nuestro ejemplo, vamos a usar un 'select' más o menos de este pelaje:

	<select onchange="cargaXML(this.value)">
		<option value="">Elige...</option>
		<option value="001.html">001</option>
		<option value="002.html">002</option>
		<option value="003.html">003</option>
	</select>

Lo que estamos haciendo es decirle al navegador que cuando cambie la selección ('onchange') se ejecute la función 'cargaXML' con la URL que hemos puesto en el 'value' como parámetro'.

Nuestro 'index.html' definitivo quedaría tal que así (voy a añadir unos estilos para que se vea más claramente nuestro DIV 'detalles', y para que veamos que se puede decorar el contenido cargado dinámicamente con CSS):

**index.html**

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
	<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="es">
		<head>
			<meta http-equiv="content-type" content="text/html; charset=utf-8" />
			<title>Mini-tutorial AJAX</title>
			<script src="ajax.js" language="JavaScript"></script>
			<style>
				#detalles {
					margin: 20px;
					border: 1px solid #F0F0F0;
					padding: 10px;
					font-size: 10px;
				}
			</style>
		</head>
		<body>
			<h4>Mini-tutorial AJAX</h4>
			<select onchange="cargaXML(this.value)">
				<option value="">Elige...</option>
				<option value="001.html">001</option>
				<option value="002.html">002</option>
				<option value="003.html">003</option>
			</select>
			<div id="detalles"></div>
		</body>
	</html>

Lógicamente, ahora deberemos crear los ficheros '001.html', '002.html' y '003.html'. Esto, como diría mi profesor de álgebra, es trivial y se deja como ejercicio para casa.

**Nota:** si estás pensando en usar una URL externa a tu dominio, que se te vaya quitando la idea de la cabeza. XMLHttpRequest está sometido a las mismas restricciones de seguridad que el _sandbox_ de JavaScript: no puedes usar el protocolo file:// y no puedes acceder a direcciones fuera de tu dominio. Ahora bien, si tu proveedor es un poco freestyle en temas de seguridad (y es un tema que, digamos, tampoco te preocupa demasiado a ti) puedes usar el viejo truco de incluir el fichero mediante PHP:

	include('url-externa-de-la-que-no-sabemos-nada');

Vaya por delante que hacer esto es una locura, y que lo más probable es que tu proveedor no te deje ni intentarlo.


## Chapando ##

Bueno, pues de momento esto es todo... aquí os dejo [un ZIP con todos los ficheros][3], y espero vuestros comentarios.

Para más información, y un tutorial más completo sobre XMLHttpRequest (incluyendo algunas nociones de cómo parsear XML) date una vuelta por la web de [Apple Developer][1]


[1]: http://developer.apple.com/internet/webcontent/xmlhttpreq.html
[2]: http://es.wikipedia.org/wiki/AJAX
[3]: http://www.sofanaranja.com/images/minitutorial-ajax.zip