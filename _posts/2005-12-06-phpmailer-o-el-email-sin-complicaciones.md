---
id: 35
title: 'PHPMailer, o el email sin complicaciones&#8230;'
date: 2005-12-06T00:30:08+00:00
author: Ale Muñoz
layout: post
guid: http://www.sofanaranja.com/?p=35
permalink: /2005/12/06/phpmailer-o-el-email-sin-complicaciones/
onswipe_thumb:
  - /images/mailer_004.png
categories:
  - Código
  - PHP
---
Si te dedicas al diseño web, antes o después tendrás que enfrentarte con el siguiente marrón: "email en HTML".

Para un proyectillo que tenía entre manos (un mini-gestor de listas de correo) me ha tocado revisitar el tema. En principio, pensaba usar algún proyecto OpenSource de los miles que hay por ahí, pero ninguno me servía porque:

* Eran increíblemente complejos de usar
* Eran increíblemente complejos de instalar
* Eran increíblemente feos
* Todas las anteriores

Con lo cual, he acabado fabricándome mi propio gestor de listas de correo, con soporte para plantillas, base de datos de destinatarios, y archivo de los emails enviados (y de paso con un poquito de AJAX : )

![Mailer001](/images/mailer_004.png)

Investigando gestores de listas OpenSource me he encontrado con [PHPMailer][1], una clase PHP que se encarga de gestionar *todo* lo que convierte al envío de emails en HTML en una pesadilla, para dejarte pensar en cosas más interesantes (como, por ejemplo, el contenido de tus boletines de noticias : )

A modo de ejemplo, aquí va el código para enviar los mails en HTML de mi gestor:

	<?php
		require("phpmailer/class.phpmailer.php");
		$mail = new PHPMailer();
		$mail->IsSMTP();
		$mail->Host = "mail.flumo.com";
		$mail->Username = "usuario";
		$mail->Password = "password";
		$mail->SMTPAuth = true;
		$mail->CharSet = "UTF-8";
		$mail->From = "info@flumo.com";
		$mail->FromName = "Flumo.com";
		$mail->IsHTML(true);
		$mail->Subject = $_POST['subject'];
		$mail->AltBody = $_POST['header']."\n\n".$_POST['body'];
		$mail->AddEmbeddedImage('logo.gif','my-logo');
		$mail->AddEmbeddedImage('bg.gif','my-bg');
		/* Destinatarios */
		$mail->AddAddress('info@flumo.com','Lista de correo de Flumo.com');
		if($_POST['database'] == 1){
			$usuarios = $db->get_results("SELECT * FROM usuarios");
			foreach($usuarios as $usuario){
				$mail->AddBCC($usuario->email,$usuario->name);
			}
		}
		if($_POST['destinatarios']){
			$to = explode(",",$_POST['destinatarios']);
			foreach($to as $tos){
				$mail->AddBCC($tos);
			}
		}
		/* Plantilla */
		$template = file_get_contents('templates/flumo.tpl','r');
		$display = str_replace("%%header%%",$_POST['header'],$template);
		$display = str_replace("%%body%%",$_POST['body'],$display);
		/* Imagenes */
		$display = str_replace("logo.gif","cid:my-logo",$display);
		$display = str_replace("bg.gif","cid:my-bg",$display);
		$mail->Body = $display;
		/* Envio del mensaje */
		if(!$mail->Send()) {
			echo "El mensaje no pudo ser enviado.";
			echo "Error: " . $mail->ErrorInfo;
		} else {
			echo "El mensaje ha sido enviado.";
		}
	?>

En el código hay un par de cosillas que usan [ezSQL][2], pero de esa otra maravilla ya hablaremos otro día...

El resultado, una cosilla así:

![Mailer002](/images/mailer_002.png)

Si tu próximo proyecto tiene algo que ver con email y usas PHP, te debes a tí mism@ echarle un vistazo a PHPMailer.

**Update:** Un artículo bastante bueno en cristiano sobre PHPMailer en [programacion.com][tut]

[1]: http://phpmailer.sourceforge.net/
[2]: http://justinvincent.com/home/articles.php?articleId=2
[tut]: http://www.programacion.com/php/articulo/phpmailer/