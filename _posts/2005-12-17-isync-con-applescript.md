---
id: 36
title: iSync con AppleScript
date: 2005-12-17T12:56:30+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=36
permalink: /2005/12/17/isync-con-applescript/
categories:
  - AppleScript
  - Código
  - Mac
---
Una de las maravillas de Mac OS X es poder sincronizar los contactos y calendarios vía Bluetooth con tu PDA/móvil/smartphone...

Sin embargo, con la versión 10.4 (Tiger) del sistema operativo, Apple ha modificado el comportamiento de iSync, de manera que el menú de la barra superior no funciona (o al menos no lo hace como antes)

Si seleccionas en las preferencias de iSync "Show status in menu bar", aparecerá un icono mediante el cual puedes sincronizar tu gadget favorito desde cualquier aplicación.

<img src='/images/isync_prefs.png' alt='' />

Lo probarás, veras que funciona muy bien, y te olvidarás del tema.

Hasta que otro día selecciones "Sync Now" y te escames de que tu teléfono parece no hacer nada... El icono se mueve, aquello parece que progresa adecuadamente, y ni siquiera aparece un mensaje de error.

<img src='/images/isync_menu_item.png' alt='' />

Lo más probable es que se te olvide el incidente hasta que unos días después, en plena vorágine de trabajo, te des cuenta de que en tu PDA/móvil/smartphone faltan tareas, citas...

¿Qué pasa aquí?

Pues lo que pasa es una cosa tan simple como la siguiente: la opción "Sync Now" no funciona a menos que tengas abierto el iSync. Por qué los ingenieros de Apple decidieron no abrir el iSync si no está abierto es uno de esos grandes misterios de la vida que (de momento) quedarán sin resolver.

La cuestión es... ¿y cómo se arregla este problema?

La solución viene (como casi siempre que uno se pone a enredar con Mac OS X) de la mano de AppleScript.

Esto que viene a continuación es un pequeño script que sustituye a la opción "Sync Now" (y de paso te ahorras unos valiosos pixels en la barra de menú : )

<img src='/images/scripts_menu_item.png' alt='' />

	tell application "iSync"
		activate
		synchronize
		repeat until syncing is false
			if syncing is false then
				quit
			end if
		end repeat
	end tell

Si guardas el script en /Users/usuario/Library/Scripts/ y activas el menú de scripts, tendrás la misma funcionalidad que con el menú de iSync (con la ventaja añadida de que funciona : )

<img src='/images/scripts_location.png' alt='' />

Que aproveche...