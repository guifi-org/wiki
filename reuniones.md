<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [2017-09-04 19:30 - 20:30](#2017-09-04-1930---2030)
  - [Situación](#situaci%C3%B3n)
  - [Avances en septiembre](#avances-en-septiembre)
  - [Convocatoria](#convocatoria)
- [2017-08-01 18:30 - 20:00](#2017-08-01-1830---2000)
  - [Acuerdos](#acuerdos)
  - [Notas](#notas)
- [2017-03-29 20:00 - 20:50](#2017-03-29-2000---2050)
  - [presentación de motivaciones](#presentaci%C3%B3n-de-motivaciones)
  - [situación](#situaci%C3%B3n)
  - [avances](#avances)
  - [futuros](#futuros)
  - [modelo de desarrollo](#modelo-de-desarrollo)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 2017-09-04 19:30 - 20:30

Asistentes:

- Roger Garcia (Fundación)
- Santiago (Ribaguifi)
- Edgar (hacklab valls)
- Kero (hacklab valls)
- Guifipedro (eXO)

## Situación

- proves de migració durant el SAX de 6 a 7, de 7 a 8, de 6 a 8
- problema: són els mòduls específics de guifi que s'han d'adaptar el codi a drupal 8
    - comentari: les dades estaran gestionades per mòduls de Core i enmagatzemades nativament en la BBDD i per tant exposades directament amb la API de D8
- el punt fort de drupal és la gestió de permisos amb continguts (entre d'altres)
- proposta: tot a l'hora no. centrar-nos en el mòdul customitzat de guifi en el drupal 8, i un cop funciona, migrar els altres mòduls

estem d'acord que:

- el model de dades a drupal8 s'accedirà a través d'API REST
- la tasca més rellevant és actualitzar el codi del mòdul de guifi per funcionar en php7/drupal8

apunt: https://github.com/mailhog/MailHog pot ser útil com a SMTP local en l'entorn de desenvolupament

## Avances en septiembre

Roger tindrà tots els contenidors a punt:

- contenidors de drupal7 i drupal8
- docker mapservices (l'aplicatiu que permet dibuixar els mapes de guifi)
- començaran a treballar en un diagrama del model de dades

roger i guifipedro: estudiar openproject com entorn de planificació de desenvolupament

guifipedro: implementació progressivament de les taules de la DB SQL drupal6 en la guifi-api de synfony

esaumell i Kero: estudiar els mòduls de guifi i budgets, i llistar camps que caldrà especificar en la definició de node de Drupal 8

## Convocatoria

Principios de octubre, lo acabamos de decidir por el [chat](https://riot.im/app/#/room/#guifi-dev:matrix.org)

# 2017-08-01 18:30 - 20:00

Asistentes:

- Roger y Ramon (Fundación Guifi)
- Santiago (Ribaguifi)
- Eduard, Montse y Guifipedro (eXO)

El principal objetivo de la reunión era que la Fundación explicara su plan de trabajo para el desarrollo de la web de guifi, presentase las novedades y así poder coordinar sus acciones con las de la comunidad de desarrolladores.

## Acuerdos
* Diseñar el particionado del gigante drupal6 en pequeños servicios.
* Garantizar la interoperabilidad entre las aplicaciones (microservicios) frente al actual modelo monolítico.
* Proporcionar entornos de desarrollo de guifi: creación de contenedores [Docker](https://www.docker.com/) y agruparlos mediante [docker-compose](https://docs.docker.com/compose/). Este trabajo está publicado en el proyecto [docker-drupal-guifi](https://github.com/guifi/docker-drupal-guifi).
* Prescindir del [gdk de vagrant](https://github.com/guifi-org/gdk) en favor del docker. El entorno basado en Docker ya está operativo (aunque falten retoques). Artículo relacionado [Docker vs Vangrant](https://www.upguard.com/articles/docker-vs-vagrant).
* Desarrollar usando frameworks actuales **sin perder la coherencia de los datos**.

## Notas
La web actual se basa en una versión de Drupal discontinuada (versión 6).

El Fiberfly (herramienta para la gestión de despliegues de fibra óptica) utiliza su propia base de datos (independiente y desvinculada de la de guifi).

El reto está en cómo compartir entre diferentes aplicaciones las bases de datos que describen guifi y que son de uso común.

Queda pendiente hablar sobre sostenibilidad y mantenimiento del servicio (quizá sea demasiado pronto).

[El próximo SAX](https://sax2017.hacklabvalls.org/) es una gran ocasión para intercambiar ideas, puntos de vista y replantear. Mientras tanto, este Agosto, hay intención de avanzar tanto en el desarrollo de la API, como en una propuesta de dirección (cómo subdividir el drupal6 de guifi en microservicios)

# 2017-03-29 20:00 - 20:50

problemillas con los navegadores: hay que elegir todos uno, esta vez ha sido chromium/chrome.


## presentación de motivaciones

santiago (ribaguifi): gestionar los nodos híbridos en web de guifi es complejo y la documentación es escasa. Mejorar la experiencia del usuario simplificando y haciendola más intuitiva. Que la realidad se plasme más fielmente en la web.

lluna (elx): queremos mejorar los servicios de funcionamiento interno. tener un fichero local/información local
volem millora de serveis de funcionament intern. tindre fitxer en local/info local

guifipedro (exo): que esto sea un punto de partida, que empecemos a trabajar en herramientas de guifi nos va a beneficiar a todos

## situación

sobre la situación en guifi es que las consultas a la  base de datos están diseminadas en múltiples ficheros PHP. Todo el código está acoplado a la base de datos. Planteamos usar un ORM como capa de abstracción de la base de datos: [Doctrine](http://www.doctrine-project.org/) (ORM de Symfony).

## avances

santiago ha hecho una abstracción de la base de datos (ORM) a partir de un mysqldump de la web de desarrollo de guifi. Ha usado una herramienta de importación del ORM de symfony: doctrine. De esta forma tenemos muy buena base de proyecto symfony para empezar, según doctrine, el 80% del código generado corresponde con la base de datos original.

Los ficheros creados son las [entidades (modelos)](https://github.com/guifi-org/guifi-api/tree/master/src/AppBundle/Entity). En cada fichero se define un modelo de datos.

Hemos propuesto empezar por el API REST de [GuifiZone](https://github.com/guifi-org/guifi-api/blob/master/src/AppBundle/Entity/GuifiZone.php). CRUDL (Create, Read, Update, Delete, List) zonas de guifi.

La documentación de symfony es bastante completa y el framework es maduro y cuenta con el respaldo de una amplia comunidad. Además de que Drupal 8 integra algunos de sus módulos.

santiago ha recomendado usar un módulo (bundle) de Symfony específico para crear la API REST llamado [FOSRestBundle](http://symfony.com/doc/master/bundles/FOSRestBundle/index.html)

## futuros

hemos propuesto dedicar cada uno 2 horas a la semana y vernos por meet jitsi cada dos semanas: 15-30min

## modelo de desarrollo

cada uno tiene su rama (con copia en el remoto) y cuando tenemos resultados, hacemos pull request

![modelo desarrollo](https://github.com/guifi-org/wiki/raw/master/git-devel-branch-model.png)
