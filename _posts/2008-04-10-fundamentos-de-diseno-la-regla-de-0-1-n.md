---
id: 225
title: 'Fundamentos de diseño: La Regla de 0-1-n'
date: 2008-04-10T17:08:51+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/2008/04/10/fundamentos-de-diseno-la-regla-de-0-1-n/
permalink: /2008/04/10/fundamentos-de-diseno-la-regla-de-0-1-n/
onswipe_thumb:
  - SKIP
categories:
  - Diseño
tags:
  - Diseño
  - escalabilidad
  - fundamentos
  - incertidumbre
---
Preparando mis notas para unas clases que daré próximamente, me doy cuenta de que tengo un mini artículo pendiente de publicar sobre el "diseño para la incertidumbre": la Regla de 0-1-n.

Es un teorema/principio/hipótesis/regla empírica, que tiene sus raíces en el mundo de la programación. Mi fuente de inspiración fue el [Wiki de C2](http://www.c2.com/cgi/wiki?ZeroOneInfinityRule) (una joya de la información, por cierto)

La regla, en su versión diseñosa, viene a decir:

> Cualquier elemento de diseño puede existir cero, una, o infinitas veces.

Destripemos la frase un poco:

**Cualquier elemento de diseño** se refiere a "cualquiera". Iconos, botoncillos, cajas de texto, elementos de menú...

**puede existir cero** quiere decir que no existe. Punto pelota. "El site no tiene menú a la izquierda". "No hay buscador". "Un post nunca llevará una imagen"

**una** quiere decir 1, la unidad, sólo uno de ese tipo. "El logo estará arriba a la izquierda". "La caja de búsqueda estará arriba la derecha".

**o infinitas veces** pasando del 1, el resto de los números no significan nada. Si el blog tendrá más de 1 post en portada, debería poder tener 5, ó 20, ó 500.

Un porcentaje muy importante de los problemas de diseño* que me encuentro tienen su raíz en no observar esta regla. No importa que hayas definido que tu portada de periódico tendrá 2 destacados. Mañana sucederán 5 cosas tan importantes que tendrán que destacarlas en portada.

\* "diseño" se usa aquí en su acepción más amplia, incluyendo arquitectura de información y HCI.

Mi consejo es bastante simple: el único número al que deberías cogerle cariño es el 1. Los demás no existen. Invierte tu tiempo diseñando sistemas flexibles que admitan crecimiento ilimitado, no en cuadrar pixels para que quepan las 3 promos en el ancho de la columna ;)