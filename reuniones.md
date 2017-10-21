<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [2017-10-12 19:00](#2017-10-12-1900)
- [2017-09-04 19:30 - 20:30](#2017-09-04-1930---2030)
  - [Situación](#situaci%C3%B3n)
  - [Avances en septiembre](#avances-en-septiembre)
  - [TODO](#todo)
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

# 2017-10-12 19:00

Nota: no pot assistir cap voluntari de guifi.net

Reunió desenvolupament 11-10-2017 (Ajornada 12-10-2017)
Assistents: Ramon Roca (as PO), Arnau Panicot, Roger Garcia (as developers de la Fundació)

SCRM

1. Product Backlog   (d) => desenvolupat, (p) = provat
    1. -Entorn de desenvolupament: Contenidors/Dockerització
        1. D6 (d)
        2. Fiberfy (d)
        3. Mapserver (d)
        4. D8 (d)
        5. LDAP / SSO
        6. D7 (d)
    2. Readme
        1. Etherpads / Ordre de  dia de reunions
        2. Readme/Landing page per carregar/sincronitzar-se amb l'entorn de desenvolupament
    3. Implementació metodologia, orientada a SCRUM / CI / DevOps
        1. Implementació d'eina de gestió de projectes / SCRUM. Candidat principal: Openproject
        2. Revisió Clusterització / Proxmox
        3. Kubernetes per a pas a PROD
    4. Integració de dades Fiberfy al que ara està a D6
        1. Extensió del model de dades del D6
        2. D8 a D6 + RestAPI
        3. Directe Fierfy -> D6
    5. SSO entre drupals
    6. Migració D6 a D7
    7. Integració NEBA
2. RETROSPECTIVA - Review
    2. Posar sobre la taula la feina feta aquest últim mes:
            1. Contenidors Drupal 6, 7 i 8 funcionant correctament (Drupal 6 i 7 amb mòduls de guifi i Drupal 8 verge)
            2. Contenidor fiberfy funcionant correctament (amb model de dades actual)
            3. Adaptació del servei guifimaps al funcionament de Docker creant una branca nova a github
            4. Contenidor guifimaps acabat i funcionament no testejat del tot (?)
3. Sprint PLANNING / Backlog (A=Arnau, RG=Roger Garcia, RR=Ramon Roca )
    1. Testejar tots els Containers desenvolupats (A)
    2. Landing page del nou entorn de desenvolupament (Backlog 1.2.2) (RG+A)
    3. Resoldre bug al mapserver
    4. Fiberfy a BD consolidada (Backlog 1.4)
        1. Extensió del model de dades
        2. PoC
            1. Fiberfy -> D8 -> D6 -> Rest API (PRIORITARY de provar)
            2. Fiberfy -> D6
4. Proxima reunió (Retrospectiva+Sprint plan) 16-Nov

# 2017-09-04 19:30 - 20:30

Asistentes:

- Roger Garcia (Fundación)
- Santiago (Ribaguifi)
- Edgar (hacklab valls)
- Kero (hacklab valls)
- Guifipedro (eXO)

## Situación

- Pruebas de migración durante el SAX de Drupal entre versiones: de 6 a 7 + de 7 a 8 y de 6 a 8 directamente.
- Problema: los modulos específicos de guifi se han de reescribir para ser compatibles con Drupal 8.
    - Comentario: los datos estarán gestionados por módulos de Core, almacenados nativamente en la BBDD y, por lo tanto, accesibles directamente mediante la API de D8.
- El punto fuerte de Drupal es la gestión de permisos sobre los contenidos (entre otros).
- Propuesta: ir por partes, centrar nos en el módulo personalizado de guifi en el Drupal 8, y una vez funcione, migrar los otros módulos. Existe una rama en desarrollo con la migración parcial del módulo de guifi a D7.
- La gestión de IPs, probablemente, es la funcionalidad más importante y, quizá, la única que se utiliza actualmente.

Coincidimos en que:

- Se expondrá el modelo de datos de Drupal8 usando su API REST.
- La tarea más relevante es actualizar el codigo del módulo de guifi para que funcione en PHP7/Drupal8.

Nota: https://github.com/mailhog/MailHog puede ser útil como SMTP local (en el entorno de desarrollo).

## Avances en septiembre

Roger tendrá todos los contenedores a punto:

- Contenedores de drupal7 i drupal8.
- docker mapservices (la aplicación que permite dibujar los mapas de guifi).
- Comenzarán a trabajar en un diagrama del modelo de datos.

roger i guifipedro: estudiar openproject como entorno de planificación de desarrollo.

guifipedro: implementación progresiva de les tablas de la DB SQL drupal6 en la guifi-api de Symfony

esaumell i Kero: estudiar los módulos de guifi y budgets, listar los campos que será necesario especificar en la definición de nodos de Drupal 8.

kero: acabar de arreglar el problema de la API KEY del mapa.

Santiago: analizar funcionalidades web guifi de cara a exponer las en la API.

## TODO
- Especificación de la API REST (¿usar herramientas tipo swagger.io?).

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
