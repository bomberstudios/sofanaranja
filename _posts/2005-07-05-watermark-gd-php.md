---
id: 5
title: Watermarking de imágenes con GD y PHP (versión WordPress)
date: 2005-07-05T23:09:31+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=5
permalink: /2005/07/05/watermark-gd-php/
tags:
  - gd
  - PHP
  - WordPress
categories:
  - Software
  - WordPress
---
Problema: añadir un watermark o sello a **todas** las imágenes de un blog de WordPress.

  - Solución 1: Abre Photoshop (o Fireworks, si eres un bicho raro como un servidor) y distráete una tarde entera poniendo marquitas.

  - Solución 2: GD + PHP. Y vete al cine o a algún bar, que hay gente muy interesante suelta por la calle.

<!--more-->
En breve, la explicación detallada. De momento tenía que escribir esto, porque me siento particularmente orgulloso de un **tremendo** hack a WordPress y tenía que ponerlo en algún sitio. Ahí van unos pantallazos:

<img src="/images/watermarkgdphpscreenshot01.png" style="border: 1px solid;"/>

<img src="/images/watermarkgdphpscreenshot02.png" style="border: 1px solid;"/>

<img src="/images/watermarkgdphpscreenshot03.png" style="border: 1px solid;"/>

Y "esto" es el watermark (un mini PNG que se incrusta en todas las imágenes, respetando la transparencia y todo):

<img src="http://www.flumo.com/images/watermark.png" style="border: 1px solid;"/>

**Nota mental:** intentar convertir el hack en un plugin de WordPress.