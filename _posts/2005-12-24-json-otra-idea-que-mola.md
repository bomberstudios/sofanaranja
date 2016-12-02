---
id: 38
title: 'JSON, otra idea que mola&#8230;'
date: 2005-12-24T21:40:54+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=38
permalink: /2005/12/24/json-otra-idea-que-mola/
onswipe_thumb:
  - SKIP
categories:
  - Código
  - JavaScript
  - PHP
---
Uno de los grandes inconvenientes a la hora de desarrollar aplicaciones web es el intercambio de información entre las partes de la aplicación.

Uno de los objetivos de XML es, precisamente, solucionar este problema. Pero a veces usar XML es como matar moscas a cañonazos.

Un ejemplo... tienes un Array en JavaScript y quieres usarlo en PHP...

La opción XML pasa por:

* Convertir el array en un XML (tremendo coñazo)
* Pasarle el XML al servidor
* Parsear el XML en el servidor
* Convertir los datos en un array

El sistema es un poco plasta, además de ser un coñazo cuando cambian las especificaciones de datos (¡sorpresa! ¡el cliente ahora quiere los datos en un Array **multidimensional**!)

Para solventar este y otros muchos inconvenientes, se crea [JSON][1], un formato de intercambio de datos "ligero" basado en JavaScript.

Existen implementaciones de JSON en casi todos los lenguajes que merecen la pena. Aquí va un mísero ejemplo usando [PHP-JSON][2] y [JSON en JavaScript][3]. El código es muy simple: creamos un Array en PHP y se lo pasamos a JavaScript para trabajar con él...

	<?php
		include("JSON.php");
		$json = new Services_JSON();
		$my_array = Array(1,2,3,4,5);
		$myjson = $json->encode($my_array);
	?>
	<script src="json.js" type="text/javascript" language="javascript" charset="utf-8"></script>
	<script>
		var myArray = JSON.parse('<?php echo $myjson; ?>');
		alert(myArray[0]);
	</script>

Fantástico... en el alert aparece '1'... te acabas de ahorrar un dolor de cabeza...

¿Funcionará con objetos?

Veamos...

	<?php
		include("JSON.php");
		$json = new Services_JSON();
		$foo->id = 'Foo';
		$foo->Class = 'Object';
		$myjson = $json->encode($foo);
	?>
	<script src="json.js" type="text/javascript" language="javascript" charset="utf-8"></script>
	<script>
		var myObj = JSON.parse('<?php echo $myjson; ?>');
		alert(myObj.id);
	</script>

Dios mio! En el alert aparece 'Foo'! :D

Sin entrar a valorar si JSON tendrá el mismo futuro que [WDDX][4] (una tecnología parecida, igualmente práctica y que no usa nadie), la verdad es que a mí por lo menos me va a venir de coña para un par de chorradas que ando programando...

Espero que el hecho de que [Yahoo haya empezado a ofrecer sus Web Services en JSON][6] le de un empujoncillo al sistema.

Si te has quedado con ganillas de más, aquí va un tutorial de XML.com: [JSON and the Dynamic Script Tag: Easy, XML-less Web Services for JavaScript][7]

[1]: http://www.crockford.com/JSON/
[2]: http://mike.teczno.com/json.html
[3]: http://www.crockford.com/JSON/js.html
[4]: http://www.openwddx.org/
[5]: http://www.designvox.com/~borys/JSON/JSON.as
[6]: http://mcmanus.typepad.com/grind/2005/12/yahoo_loves_jav.html
[7]: http://www.xml.com/pub/a/2005/12/21/json-dynamic-script-tag.html