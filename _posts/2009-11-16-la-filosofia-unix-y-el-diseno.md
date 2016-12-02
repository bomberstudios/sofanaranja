---
id: 402
title: La filosofía UNIX y el diseño
date: 2009-11-16T18:29:42+00:00
author: Ale Muñoz
layout: post
guid: http://sofanaranja.com/?p=402
permalink: /2009/11/16/la-filosofia-unix-y-el-diseno/
onswipe_thumb:
  - SKIP
categories:
  - Diseño
tags:
  - Diseño
  - fundamentos
  - metodología
---
Preparando un documento de análisis para un cliente, me he encontrado en mi fondo de armario un enlace a [las bases de la filosofía UNIX](http://www.faqs.org/docs/artu/ch01s06.html) y no puedo dejar de pensar en lo bien que aplican estas reglas al mundo del diseño de interacción.

Las 17 reglas en versión resumida vienen a decir (perdón por la traducción al vuelo):

1. Regla de **Modularidad**: Escribe partes simples, conectadas por interfaces simples.

2. Regla de **Claridad**: ser Claro es mejor que ser ingenioso.

3. Regla de **Composición**: Diseña programas para que se conecten a otros programas.

4. Regla de **Separación**: Separa las reglas del funcionamiento; separa los interfaces de los mecanismos.

5. Regla de **Simplicidad**: Diseña para la simplicidad; añade complejidad sólo donde sea estrictamente necesario.

6. Regla de **Parsimonia**: Escribe un programa complejo sólo cuando sea evidente que no existe otra solución posible.

7. Regla de **Transparencia**: Diseña para la visibilidad, para hacer más fácil la inspección y la corrección de fallos.

8. Regla de **Robustez**: la Robustez es hija de la transparencia y la simplicidad.

9. Regla de **Representación**: Convierte el conocimiento en datos, para que la lógica de los programas pueda ser estúpida y robusta.

10. Regla de **Mínima Sorpresa**: En diseño de interfaces, haz siempre lo menos sorprendente.

11. Regla de **Silencio**: Cuando un programa no tenga nada sorprendente que decir, no debería decir nada.

12. Regla de **Reparación**: Cuando tengas que mostrar un error, falla estridentemente y lo antes posible.

13. Regla de **Economía**: el tiempo del programador es caro; consérvalo sobre el tiempo de la máquina.

14. Regla de **Generación**: Evita hacer cosas a mano; escribe programas que escriban programas siempre que puedas.

15. Regla de **Optimización**: Prototipa antes de pulir. Haz que funcione antes de optimizarlo.

16. Regla de **Diversidad**: Desconfía de todo lo que diga "esta es la única forma correcta".

17. Regla de **Extensibilidad**: Diseña para el futuro, porque estará aquí antes de lo que piensas.

El único cambio que creo necesario para añadirlo a mi arsenal de Fundamentos de Diseño es reescribir la regla 13 como "el tiempo del usuario es caro; consérvalo sobre el tiempo del diseñador" (pensando en la [Ley de Tesler](http://sofanaranja.com/2009/11/10/la-ley-de-la-conservacion-de-la-complejidad-de-tesler/)).