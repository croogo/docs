Instalacion
###########

Instalacion web
===================

- Extrae el archivo. Carga tu contenido al servidor.
- Crea una nueva base de datos MySQL (utf8_unicode_ci collation)
- Visita http://tu-sitio.com/ desde tu navegador y sigue las instrucciones.

Instalacion manual
==================


- Extrae el archivo. Carga tu contenido al servidor.
- Crea una nueva base de datos MySQL (utf8_unicode_ci collation) y usa los 2 dumps de SQL en el siguiente orden:
  - app/Config/Schema/sql/croogo.sql
  - app/Config/Schema/sql/croogo_data.sql
- Renombra:
  - app/Config/database.php.install a database.php, y edita los detalles.
  - app/Config/croogo.php.install a croogo.php, y edita los detalles.
  - app/Config/settings.yml.install a settings.yml
- Puedes acceder a tu panel de administracion en http://tu-sitio.com/admin. El instalador debera mostrar una pagina para crear el usuario administrativo.

Se recomienda que instales Croogo usando el instalador web por motivos de seguridad.