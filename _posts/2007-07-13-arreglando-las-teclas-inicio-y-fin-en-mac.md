---
id: 186
title: Arreglando las teclas Inicio y Fin en Mac
date: 2007-07-13T11:23:22+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2007/07/13/arreglando-las-teclas-inicio-y-fin-en-mac/
permalink: /2007/07/13/arreglando-las-teclas-inicio-y-fin-en-mac/
onswipe_thumb:
  - SKIP
categories:
  - Mac
  - Trucos
tags:
  - Mac
---
Si eres un usuario de Mac que viene del mundo Windows (o Linux) te habrás dado cuenta de que el comportamiento de las teclas "Inicio" y "Fin" en Mac no tiene nada que ver con otros sistemas operativos.

Lo mismo sucede con las teclas "Avanzar Página" y "Retroceder Página", que en Mac avanzan y retroceden, pero no mueven el cursor de sitio...

Si quieres que la tecla "Inicio" vaya al principio de la línea, la tecla "Fin" vaya al final, y las teclas de Avanzar y Retroceder página funcionen de una forma racional, sólo tienes que crear un ficherito de texto con este contenido:

    {
      "\UF729"  = "moveToBeginningOfLine:";
      "$\UF729" = "moveToBeginningOfLineAndModifySelection:";
      "\UF72B"  = "moveToEndOfLine:";
      "$\UF72B" = "moveToEndOfLineAndModifySelection:";
      "\UF72C"  = "pageUp:";
      "\UF72D"  = "pageDown:";
    }

y guardarlo en `~/Library/KeyBindings/DefaultKeyBinding.dict` (creando la carpeta si no existe todavía)

Poseso! :)