Plugins
#######

Como cargar uno nuevo?
======================

Si tienes un plugin en un archivo ZIP, sigue estas instrucciones:

- Entra a tu panel de administracion
- Ve a la pagina de Extensiones > Plugins
- Identifica el link de Cargar en la parte superior. Este te llevara a una pagina nueva donde podras cargar el archivo ZIP.

Carga manual
============

- Pon tu plugin en ``/app/Plugin/NombreDelPlugin``


Como activar y desactivar?
==========================

Despues de cargar tu plugin, necesitaras activarlo.

- Desde tu panel de administracion, ve a Extensiones > Plugins.
- Da click en el icono de tacha/palomita para activar o desactivar el plugin.

Migraciones
===========

Cuando subas un nuevo plugin, un vinculo de "Migrar" puede aparecer en la parte izquierda del link de "Desactivar". Este vinculo te permitira crear o actualizar la base de datos de este plugin.

En la mayoria de los casos esta operaciones es aplicada atuomaticamente cuando se activa un plugin. Pero en otros casos, el desarrollador del plugin puede requerir una migracion manual para mejor control o si se requieren pasos adicionales antes de activar la migracion. En este caso deberas leer la documentacion del manual antes de dar click en el vinculo de "Migrar" para conocer las posibles consecuencias.