Permisos
########

Croogo usa el sistema ACL de CakePHP para administrar los permisos de los usuarios. Para ser honestos puede ser un poco complicado explicar ACL para los principiantes. Pero Croogo se encarga de quitar el sufrimiento de esto al proveer una interfaz simple y utilizable para administrar los permisos.

Como la aplicacion se construyo con un frameworks MVC, para cualquier URL (que no sea de archivos como CSS e imagenes) se accede en realidad a la salida de una accion de controlador. Por ejemplo si se visita la publicacion "Hola mundo", lo que esta mostrando es la accion View del controlador de Nodos.

Ahora para administrar esa accion:
- Ingresa a tu panel de administracion
- Ve a Usuarios > Permisos
- Click en Nodos y mostrara todas sus acciones

Despues da click en el icono de la fila de View (vista) para permitir o denegar el acceso para distintos roles de usuarios.