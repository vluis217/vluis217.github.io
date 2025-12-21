---
title: STEMJobsCR - Qué, Cómo y Por Qué.
date: 2023-01-22
categories: [EMPLEO]
tags: [python, web scraping, costa rica]
image:
  path: /assets/img/posts/stemjobs-faq/cover.png
---

Mi nombre es Luis Vargas, soy Ingeniero en Ciberseguridad, y soy la (única) persona detrás de los canales de Telegram [@STEMJobsCR](https://t.me/s/STEMJobsCR) y [@STEMJobsLATAM](https://t.me/s/STEMJobsLATAM), de WhatsApp ([CR](https://whatsapp.com/channel/0029Vb8j98vIiRp29WtW8N32) y [LATAM](https://whatsapp.com/channel/0029Vb4IaaN545uneyEqGH1T)), y del servidor de Discord [EmpleoKB](https://empleokb.com), de ofertas de empleo en STEM.

Recientemente, debido a la ola de despidos, a que llegamos a los mil miembros en el canal de ofertas de Costa Rica, y a que me han llegado mensajes y preguntas _curiosas_ sobre los canales, decidí escribir este blog para presentarme y explicar algunos detalles sobre esta iniciativa.

## ¿Qué son estos canales?
STEMJobsCR es un canal de Telegram donde se publican automáticamente ofertas de empleo en tecnología de empresas de Costa Rica (o de empresas transnacionales con sede en CR).

STEMJobsLATAM es similar, pero se diferencia en que las ofertas que se publican son para trabajar para empresas **ubicadas fuera de Costa Rica** en modalidad de teletrabajo.

O sea, las ofertas de STEMJobsCR son para trabajar en Costa Rica para una empresa o subsidiaria costarricense, en modalidad presencial o teletrabajo; y las de STEMJobsLATAM dan la posibilidad de trabajar desde Costa Rica (o países en zonas horarias similares) para empresas fuera del país en modalidad de teletrabajo.

En el servidor de Discord se publican las mismas ofertas de empleo que en Telegram.

## ¿Cómo funcionan?
Utilizando Python, programé un bot que mediante el uso de APIs, web requests y web scraping, monitorea periódicamente bolsas de empleo. Cuando el bot detecta nuevas ofertas, las publica en el canal respectivo usando webhooks. El bot se ejecuta cada 20 minutos en un servidor gratuito en OCI (Oracle Cloud Infrastructure).

## ¿Por qué los hice?
Por varias razones:

- Quería aprender Python, y como ya sé programar en otros lenguajes, no era muy eficiente empezar con un curso de Python desde cero, por lo que decidí aprender haciendo este proyecto.
- Tengo una idea de negocio que involucra web scraping y monitoreo de páginas web desde la nube, así que este proyecto me sirve para aprender esas técnicas y tecnologías.
- En el pasado yo también he estado desempleado, pero más importante que eso, he estado en trabajos y empresas que no cumplían mis expectativas, y que además me drenaban toda la energía que podría utilizar para buscar otro puesto. Teniendo alertas automáticas de ofertas de empleo directamente en el celular, el esfuerzo requerido para buscar otra oportunidad se reduce bastante.
- El mundo de la tecnología se mueve muy rápido, por lo que me parece importante estar enterado de qué empresas están contratando, para qué áreas, qué conocimientos piden, e inclusive cuál es el rango salarial dependiendo de la empresa o área.

En resumen: hice los canales para mí, para aprender sobre varias cosas, pero los comparto públicamente porque creo que le pueden ser útiles a otras personas.

## Otras preguntas
**Q**: ¿Qué gana con esto?  
**A**: Aprender Python, sobre la nube, web scraping, tendencias del mercado laboral, etc (leer arriba).

**Q**: ¿Tiene o quiere tener alguna ganancia monetaria con esto?  
**A**: No tengo ganancias monetarias y no es mi objetivo. Afortunadamente. en este momento tengo trabajo fijo y no tengo la necesidad de monetizar este proyecto. El servidor en el cual funciona el bot está en el free tier de OCI, por lo que aparte del uso de mi tiempo libre, este proyecto no me produce ningún otro gasto.

**Q**: ¿Puedo ofrecer mis "servicios de empleabilidad" en sus canales?  
**A**: **<u>NO.</u>** Intentar sacarle dinero a personas que están en búsqueda de empleo, inclusive desempleadas, me parece algo bastante inmoral y no pienso ser parte de eso.
  
**Q**: Si tuviera la necesidad, ¿monetizaría este proyecto en el futuro?  
**A**: Tal vez, si me tomara poco o nulo esfuerzo extra y la ganancia valiera la pena. Habiendo dicho esto, **JAMÁS** le sacaría dinero a los miembros de los canales. Incluiría publicidad o le cobraría a **las empresas** por promover sus ofertas, pero nada que empeore el uso de los canales o tome ventaja de sus miembros.

**Q**: Quiero comprar su proyecto.  
**A**: Ok, vale USD$1m 😉

**Q**: ¿Usted tiene contactos o convenios con alguna de las empresas?  
**A**: Por el momento no. La única empresa con la que tuve contacto fue con `remote.io`, sus dueños me dieron un feed especial el cual usaba* para monitorear y sacar las ofertas de ahí.
\**`remote.io` bajó la calidad de las ofertas que publicaba, por lo que la desactivé en el bot*

**Q**: ¿Qué empresas monitorea?  
**A**: [Lista completa y actualizada de bolsas de empleo.](https://docs.google.com/spreadsheets/d/1wl7edAy6TcVuFh13LQ4FtvCZgPUb3ETFcQp8jlfuanM/)

**Q**: ¿Puede publicar/dejar de publicar las ofertas de mi empresa?  
**A**: ¡Sí!, nada más envíeme el link de la bolsa de empleo o nombre de la empresa por DM a [mi LinkedIn](https://www.linkedin.com/in/vluis/) o Telegram (`@vluis`), y apenas tenga tiempo la agrego/quito del bot.

**Q**: ¿Usted cree que puedo aplicar a `[X trabajo]`?  
**A**: Las únicas personas que pueden responder esa pregunta son los reclutadores y hiring managers del puesto específico. Buscar y encontrar trabajo ya es bastante difícil, cansado y tedioso, y si uno se descalifica a uno mismo porque "le falta X habilidad/conocimiento", uno solo se impone un nivel adicional de dificultad. En resumen, ¡¡simplemente aplique!!

**Q**: ¿Cómo puedo ayudar o contribuir con la iniciativa?  
**A**: La mejor forma de ayudarme es dándome feedback sobre cómo puedo mejorar los canales (qué agregar, cambiar, quitar, etc), y sobre cómo le han ayudado o le ayudan los canales.

**Q**: ¿Cuál es su Patreon/Ko-Fi/etc?  
**A**: Link en mi Linktree: [linktr.ee/vluis217](https://linktr.ee/vluis217/)

**Q**: ¿Por qué los logos de los canales son tan feos?  
**A**: Todo lo relacionado a los canales lo he hecho yo mismo, y desafortunadamente solo soy ingeniero y no diseñador gráfico. Si usted sabe diseñar y quiere aportar nuevos logos, ¡se lo agradecería bastante!

**Q**: ¿Tiene página web?  
**A**: No, pero [stemjobscr.com](https://stemjobscr.com) y [empleokb.com](https://empleokb.com) redireccionan al discord.

Por el momento éstas son las preguntas o dudas más frecuentes que me han llegado, pero voy a actualizar este blog periódicamente cuando sea necesario.

## Stream del tercer aniversario del proyecto
{% include embed/youtube.html id='_UnoUGCJK9M' %}