---
id: 51
title: RubyOnRails en Dreamhost
date: 2006-02-23T23:09:43+00:00
author: Ale Muñoz
excerpt: Un mini tutorial sobre cómo instalar Ruby On Rails en Dreamhost, un hosting bueno, bonito y barato... (y aún más barato si usas el Código de Descuento Sofá Naranja™)
layout: post
guid: http://www.sofanaranja.com/?p=51
permalink: /2006/02/23/rubyonrails-en-dreamhost/
categories:
  - Código
---
En el [Taller de Ruby On Rails del Hacklab Cielito Lindo][hl], se planteó la pregunta del millón:

> ¿Dónde alojar aplicaciones Rails?

De los 3 hostings que se mencionaron (TextDrive, Ferca y Dreamhost), uno de ellos resulta ser mi favorito: <a href="http://www.dreamhost.com/r.cgi?bomberstudios">Dreamhost</a>.

Aprovechando que en mi lista 'B' de tareas pendientes tenía lo de montar Rails en alguna parte, aquí va el proceso documentado por si a alguien le sirve.

## Requisitos previos ##

* Tener un dominio registrado en Dreamhost (parece una obviedad, pero ya veréis que no).
* Tener habilitado el acceso mediante Telnet (mal) o SSH (bien) a nuestro servidor.
* Un mínimo de habilidad con la línea de comandos.

## Habilitando el espacio web ##

Se puede hacer de mil maneras, pero lo más cómodo es usar un subdominio de tu site (es por ello que comentaba que necesitas un site funcionando)

Para dar de alta un subdominio (que a día de hoy es gratis total en Dreamhost), nos vamos al panel de control > Domains > Manage Domains y le damos a "[Add New Domain / Sub-Domain]"

Ponemos los datos del subdominio, prestando especial a estos detalles:

* Elegir "Fully Hosted" (para que nos cree un directorio nuevo para el site)
* Habilitar FastCGI

<img src='/wp-content/ror_dh_001_domain.png' alt='' />

Le damos a OK, esperamos un ratillo (10-15 minutos) y accedemos vía Telnet o SSH a nuestro servidor. Si vemos una carpeta en nuestra home llamada 'rails.tudominio.com' (o como sea que le hayas puesto a tu subdominio) ya podemos crear nuestra primera aplicación en Rails.

Prepárate, porque lo que viene ahora es bastante duro:

<img src='/wp-content/ror_dh_002_ssh.png' alt='' />

Y ya está... complicado, ¿eh?

Si ahora abres un navegador y te vas a http://rails.tudominio.com/nombre_de_aplicacion/public/ (ojo con la / final, sin ella a mí no me rula) verás una bonita pantalla de bienvenida:

<img src='/wp-content/ror_dh_003_welcome.png' alt='' />

Si es así, y todo funciona correctamente, es el momento de fortificar la instalación de Rails: si la dejas como está, cualquiera puede ir a la carpeta /blog/config/ y leer el nombre de usuario y contraseña de database.yml.

Para asegurarnos de que eso no ocurra (y para tener una URL un poco más breve, de paso) volvemos al panel de control de Dreamhost, en Domains > Manage Domains y le damos a "Edit" en nuestro flamante subdominio. Ahora cambiaremos la ruta del site ("Web Directory") por rails.tudominio.com/nombre_de_aplicacion/public/

Guardamos los cambios, y tras un tiempo prudencial (en mi caso, unos 20 segundos : ) abrimos la URL http://rails.tudominio.com comprobando que, efectivamente, Rails nos muestra la misma pantalla de antes.

Si es así, bienvenido al maravilloso mundo de Ruby On Rails!... :D

**Update:** Si quieres contratar un alojamiento en DreamHost (que es algo que recomiendo encarecidamente después de comprobar que se tarda menos en montar Rails allí que en mi ordenador), puedes usar este código de promo: **SNROR**, y te descontarán 20 pavos de tu factura por la cara...


[hl]: http://www.railes.net/?p=15