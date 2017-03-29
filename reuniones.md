# 2017-03-29 20:00 - 20:50

problemillas con los navegadores: hay que elegir todos uno, esta vez ha sido chromium/chrome.

**presentación de motivaciones**

chk (ribaguifi): web de guifi es un dolor de cabeza, facilitarla al máximo. que la realidad se plasme mejor en la web

lluna (elx): queremos mejorar los servicios de funcionamiento interno. tener un fichero local/información local
volem millora de serveis de funcionament intern. tindre fitxer en local/info local

guifipedro (exo): que esto sea un punto de partida, que empecemos a trabajar en herramientas de guifi; nos va a beneficiar a todos

**situación**

sobre la situación en guifi es que la base de datos está desparramada en ficheros PHP: no está separado el modelo de datos del resto del código; esto lo hace difícil si lo que buscamos es un ORM

**proyección**

chk ha hecho una abstracción de la base de datos (ORM) a partir de un mysqldump de la web de desarrollo de guifi. Ha usado una herramienta de importación del ORM de symphony: doctrine. De esta forma tenemos muy buena base de proyecto symphony para empezar, según doctrine, el 80% del código generado corresponde con la base de datos original.

El fichero más importante es el de [Entity](https://github.com/guifi-org/guifi-api/tree/master/src/AppBundle/Entity), aquí en cada fichero se define una estructura.

Hemos propuesto empezar por el API REST de [GuifiZone](https://github.com/guifi-org/guifi-api/blob/master/src/AppBundle/Entity/GuifiZone.php). Crear, destruir zona...

Los tutoriales de symphony son asequibles. Symphony como proyecto está muy bien.

Chk ha recomendado usar un módulo de Symfony específico para crear la API REST llamado [Bundle](http://symfony.com/doc/master/bundles/FOSRestBundle/index.html)

**modelo de desarrollo**

cada uno tiene su rama (con copia en el remoto) y cuando tenemos resultados, hacemos pull request

![https://github.com/guifi-org/wiki/raw/master/git-model.png]()

hemos propuesto vernos por meet jitsi cada dos semanas: 15-30min
