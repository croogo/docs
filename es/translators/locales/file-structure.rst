Estructura de archivos
######################

Por ejemplo, si quieres traducir Croogo al Bengali (que el codigo ISO 639-2 de ese lenguaje es ben), entonces la estructura de archivos seria:

  - app/Locale/ben/
    - LC_MESSAGES/
      - default.po

La mejor manera de hacer esto es copiar el archivo default.pot, y despues traducirlo utilizando un software como Poedit. No ovlides renombrar los archivos .pot a .po