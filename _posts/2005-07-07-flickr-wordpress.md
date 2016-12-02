---
id: 7
title: FlickR + WordPress
date: 2005-07-07T23:46:51+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=7
permalink: /2005/07/07/flickr-wordpress/
categories:
  - Plugins
  - WordPress
---
Pues nada, andaba yo felizmente por esos mundos de dios cuando se me ocurrió la brillante idea: ¿se podrá montar una galería de fotos en WordPress usando FlickR? (en realidad me hacía falta para un proyecto, pero es que contado así no tenía mucha gracia)

<!--more-->
Googleando un poco, me encuentro con [este plugin de WordPress][1], que resulta ser lo más difícil de instalar del mundo, no funciona bien con WordPress 1.5 y además usa <code>fopen()</code>, por lo que no rula en [DreamHost][2]

Afortunadamente aún queda gente amable en el mundo, y Nick Bouton se ha currado una [versión actualizada][3] que usa _libcurl_ (que es lo único que se puede usar en DreamHost para pillar ficheros remotos) y que medio funciona con WordPress 1.5.

La instalación es una pequeña pesadilla, pero al final merece la pena:

<a href="http://www.flumo.com/photos" target="_blank"><img src="/images/flickrwordpress-02.png"/></a>

[1]: http://www.worrad.com/archives/2005/01/08/flickr-gallery-07/
[2]: http://www.dreamhost.com
[3]: http://www.nickbouton.com/archives/2005/04/25/updated-flickr-gallery-wordpress-plug-in/