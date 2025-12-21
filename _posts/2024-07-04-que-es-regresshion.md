---
title: CVE-2024-6387, "RegreSSHion", ¿qué es?
date: 2024-07-04
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, regresshion, cve-2024-6387]
image:
  path: /assets/img/posts/que-es-regresshion/cover.png
---

_Quiero empezar aclarando que no soy un experto en esta clase de vulnerabilidades, no sé programar en C, y no tengo experiencia trabajando con estructuras de bajo nivel del sistema operativo (como el heap). Sin embargo, escribo este blog porque me parece fascinante la cadena de técnicas, la investigación y la gran creatividad usadas en el descubrimiento de esta vulnerabilidad, y me gustaría compartir los detalles importantes de la misma._

La vulnerabilidad CVE-2024-6387, nombrada "RegreSSHion" y descubierta por investigadores de Qualys, es un bug en OpenSSH entre la versión 8.5p1 y superiores hasta antes de la versión 9.8p1. OpenSSH es un software ampliamente usado en una gran cantidad de sistemas operativos para administración y autenticación remota, o sea, un software que permite usar una shell segura de forma remota. Esta vulnerabilidad, en caso de ser explotada exitosamente, podría ser utilizada para hacer un ataque de tipo RCE (Remote Code Execution) con privilegios elevados, sin necesidad de autenticarse.

A primera vista la gravedad pareciera ser evidente, especialmente si se tiene en cuenta que es común encontrar este software directamente expuesto al Internet.

## Detalles técnicos

En términos técnicos simples, la vulnerabilidad funciona de la siguiente manera:
1. El atacante inicia el proceso de login, enviando datos maliciosos a la víctima, pero omitiendo el último byte, para que el servicio `sshd` en el dispositivo de la víctima se quede "esperando" a que el proceso de login se complete.
2. Momentos antes de que `sshd` cierre la conexión debido al intento de login "erróneo", el atacante envía el último byte de la data de login.
3. Si este último byte llega justo antes de que se cierre la conexión, pero después de que `sshd` haya empezado el proceso para cerrarla, es posible que la data maliciosa que el atacante envió se ejecute como si fuera código con privilegios elevados (con el usuario `root`).

Es importante notar que en las versiones más recientes de OpenSSH, es posible realizar 100 intentos de conexión (`MaxStartups`) cada 120 segundos (`LoginGraceTime`) con la configuración por defecto.

Expuesto de esta manera el ataque podría parecer simple, pero para que tenga éxito es necesario:
- Enviar data especialmente creada para realizar el ataque. Esta data puede ser un nombre de usuario malicioso, o una llave pública maliciosa.
- Calcular el tiempo que le toma a los paquetes llegar del atacante a la víctima, para poder enviar el último byte en el momento exacto.
- Que cuando el último byte llegue a la víctima, el programa esté ejecutando las funciones vulnerables que eventualmente ejecutarían el código malicioso.
- Que la data maliciosa se haya guardado en la ubicación de memoria correcta.

Además, es importante notar que:
- El atacante es remoto y no tiene ni acceso ni conocimiento del estado interno de la memoria de la víctima.
- La más mínima variación en la latencia de red cambia el proceso del ataque. Entre más "saltos" (dispositivos de red intermedios) haya entre el atacante y la víctima, más variación podría haber en los tiempos de envío y recepción de paquetes.
- La velocidad (IPC y frecuencia) del procesador también influye en el proceso del ataque.
- La versión, distribución y arquitectura (32/64bits) del sistema operativo puede hacer el ataque exponencialmente más complicado, o inclusive imposible. Por ejemplo, OpenBSD y Ubuntu 24.04 no son vulnerables a este ataque. Aún no se confirma si MacOS y Windows son afectados por esta vulnerabilidad.
- Los controles de seguridad como allowlists, hardening de SSH, IDS, IPS, EDR, etc., pueden imposibilitar este ataque.
- En este momento no hay ningún exploit público, y debido a la naturaleza de la vulnerabilidad, opino que hay pocas probabilidades que alguien desarrolle un "exploit universal", fácil de ejecutar y que funcione para cualquier sistema operativo.

## Recomendaciones

A pesar de que el ataque es altamente complejo y hasta impráctico en este momento, es posible que en un futuro no muy lejano se encuentren formas de normalizar las variables necesarias para llevarlo a cabo, y que se vuelva trivial. Además, debido a que el resultado de una explotación exitosa es la ejecución de código de forma remota con privilegios elevados, esto es suficiente motivación para actores maliciosos sofisticados para dedicar una gran cantidad de recursos para perfeccionar este ataque.

Es por esto que la principal recomendación es instalar la [versión 9.8p1 de OpenSSH](https://www.openssh.com/releasenotes.html#9.8p1) (o superior), la cual contiene el parche para esta vulnerabilidad. Más allá de esto, esta versión contiene cambios importantes en la estructura interna del código de OpenSSH, por lo que cualquier mejora de seguridad o funcionalidad que se implemente después de esta será difícil de llevar a versiones anteriores. En otras palabras, sería ideal tomar esta oportunidad para actualizar sus instalaciones de OpenSSH.

## Notas adicionales

En mi opinión, este ataque es mucho más viable como vector para escalación local de privilegios: si el atacante logra tener acceso a la víctima con un usuario de bajos privilegios, esto eliminaría la mayoría de variables e incertidumbre que conlleva el ataque remoto, haciéndolo más fácil de llevar a cabo de forma local, en teoría.

### Fuentes
- [https://www.qualys.com/2024/07/01/cve-2024-6387/regresshion.txt](https://www.qualys.com/2024/07/01/cve-2024-6387/regresshion.txt)
- [https://www.youtube.com/watch?v=Rj3sTAMYNQk](https://www.youtube.com/watch?v=Rj3sTAMYNQk)
- [https://www.youtube.com/watch?v=2Ig05_aL4Xg](https://www.youtube.com/watch?v=2Ig05_aL4Xg)