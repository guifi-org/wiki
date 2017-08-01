<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [2017-08-01 18:30 - 20:00](#2017-08-01-1830---2000)
- [2017-03-29 20:00 - 20:50](#2017-03-29-2000---2050)
  - [presentación de motivaciones](#presentaci%C3%B3n-de-motivaciones)
  - [situación](#situaci%C3%B3n)
  - [avances](#avances)
  - [futuros](#futuros)
  - [modelo de desarrollo](#modelo-de-desarrollo)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 2017-08-01 18:30 - 20:00

asistentes:

- roger y ramon (fundación guifi)
- chk (ribaguifi)
- eduard, montse y guifipedro (eXO)

El principal motivo de la reunión era para que la fundación guifi nos comentara novedades en cuanto a coordinación del desarrollo entorno a la web de guifi. Facilitar los entornos de desarrollo de guifi, facilitar que las aplicaciones interoperables (no monolíticas): microservicios, trabajar el particionado del gigante drupal6 en pequeños servicios gracias a la tecnología docker, docker-compose que ha empezado a través del proyecto [docker-drupal-guifi](https://github.com/guifi/docker-drupal-guifi)

Estamos de acuerdo, que dado que a todos nos gusta docker, y que está a punto de estar listo; podemos prescindir del [gdk de vagrant](https://github.com/guifi-org/gdk)

El reto está en cómo compartir entre diferentes aplicaciones las bases de datos que describen guifi y que son de uso común

Lamentablemente no hemos hablado sobre sostenibilidad, mantenimiento del servicio (quizá es demasiado pronto, pero era buena ocasión)

[El próximo SAX](https://sax2017.hacklabvalls.org/) es una gran ocasión para intercambiar ideas, puntos de vista y replantear. Mientras tanto, este Agosto, hay intención de avanzar tanto en el desarrollo de la API, como en una propuesta de dirección (cómo subdividir el drupal6 de guifi en microservicios)

# 2017-03-29 20:00 - 20:50

problemillas con los navegadores: hay que elegir todos uno, esta vez ha sido chromium/chrome.


## presentación de motivaciones

chk (ribaguifi): gestionar los nodos híbridos en web de guifi es complejo y la documentación es escasa. Mejorar la experiencia del usuario simplificando y haciendola más intuitiva. Que la realidad se plasme más fielmente en la web.

lluna (elx): queremos mejorar los servicios de funcionamiento interno. tener un fichero local/información local
volem millora de serveis de funcionament intern. tindre fitxer en local/info local

guifipedro (exo): que esto sea un punto de partida, que empecemos a trabajar en herramientas de guifi nos va a beneficiar a todos

## situación

sobre la situación en guifi es que las consultas a la  base de datos están diseminadas en múltiples ficheros PHP. Todo el código está acoplado a la base de datos. Planteamos usar un ORM como capa de abstracción de la base de datos: [Doctrine](http://www.doctrine-project.org/) (ORM de Symfony).

## avances

chk ha hecho una abstracción de la base de datos (ORM) a partir de un mysqldump de la web de desarrollo de guifi. Ha usado una herramienta de importación del ORM de symfony: doctrine. De esta forma tenemos muy buena base de proyecto symfony para empezar, según doctrine, el 80% del código generado corresponde con la base de datos original.

Los ficheros creados son las [entidades (modelos)](https://github.com/guifi-org/guifi-api/tree/master/src/AppBundle/Entity). En cada fichero se define un modelo de datos.

Hemos propuesto empezar por el API REST de [GuifiZone](https://github.com/guifi-org/guifi-api/blob/master/src/AppBundle/Entity/GuifiZone.php). CRUDL (Create, Read, Update, Delete, List) zonas de guifi.

La documentación de symfony es bastante completa y el framework es maduro y cuenta con el respaldo de una amplia comunidad. Además de que Drupal 8 integra algunos de sus módulos.

chk ha recomendado usar un módulo (bundle) de Symfony específico para crear la API REST llamado [FOSRestBundle](http://symfony.com/doc/master/bundles/FOSRestBundle/index.html)

## futuros

hemos propuesto dedicar cada uno 2 horas a la semana y vernos por meet jitsi cada dos semanas: 15-30min

## modelo de desarrollo

cada uno tiene su rama (con copia en el remoto) y cuando tenemos resultados, hacemos pull request

![modelo desarrollo](https://github.com/guifi-org/wiki/raw/master/git-devel-branch-model.png)
