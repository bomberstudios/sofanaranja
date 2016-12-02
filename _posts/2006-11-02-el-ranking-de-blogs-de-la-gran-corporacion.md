---
id: 125
title: El ranking de blogs de La Gran Corporación
date: 2006-11-02T01:38:52+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2006/11/02/el-ranking-de-blogs-de-la-gran-corporacion/
permalink: /2006/11/02/el-ranking-de-blogs-de-la-gran-corporacion/
categories:
  - Personal
  - Web
---
Como mantener [el ranking de blogs de La Gran Corporación™](/2006/11/01/estadisticas-absurdas-volumen-2/) a mano resulta ser una paliza, he hecho lo que todo geek que se precie haría: automatizar :)

Usando la [API de Technorati](http://technorati.com/developers/api/) y un poco de tiempo libre, aquí está el auténtico, genuino, glamouroso y completamente inutil* <strong>Ranking de blogs de La Gran Corporación™</strong>:

<script type="text/javascript" language="javascript" charset="utf-8">
// <![CDATA[
	showSpinner = function(){
		var s = document.getElementById("spinner");
		s.style.display = "block";
	}
	hideSpinner = function(){
		var s = document.getElementById("spinner");
		s.style.display = "none";
	}
	cargaRanking = function(){
		Ajax.load("/xp/technorati/get_ranking.php","ranking_blogs",hideSpinner,showSpinner);
	}
// ]]>
</script>
<script src="/js/ajax.js" type="text/javascript" language="javascript" charset="utf-8"></script>

<a href="javascript:cargaRanking();">Cargar ranking!</a>

<div id="ranking_blogs">
</div>
<!-- /ranking_blogs -->
<span id="spinner" style="display: none;"><img src="/images/spinner.gif" /></span>

(El engendro usa un pequeño montoncito de JavaScript, así que te sugiero que abras el post en una pestaña nueva si estás usando [Bloglines](http://www.bloglines.com/)).

*: "Completamente inutil" salvo para [decidir quién se lleva el jamón estas navidades](http://www.the-mixer.net/mixer/post/2006/11/01/the-cocktail-technorati) :P

**Update:** Parece que Technorati se ha levantado puñetero esta mañana y no está devolviendo los datos a través de la API. A dios pongo por testigo de que En Mi Máquina Funcionaba™ :P

**Update 2:** Como diría Sergio, "a ver si leemos, coñe". La API de Technorati sólo te deja hacer 500 consultas al día, y parece que nos las hemos comido todas en un rato : (

<div class="techtag"><span>Technorati tags:</span> <a href="http://technorati.com/tag/technorati" rel="tag">technorati</a>, <a href="http://technorati.com/tag/ranking" rel="tag">ranking</a>, <a href="http://technorati.com/tag/javascript" rel="tag">javascript</a></div>