File structure
##############

For example, if you want to translate Croogo into Bengali (whose ISO 639-2 language code is ben), the file structure will be:

  - app/Locale/ben/
    - LC_MESSAGES/
      - default.po

Best way to do it is by copying the default.pot file, and then translating it using a software like Poedit. Do not forget to rename the .pot file as .po.