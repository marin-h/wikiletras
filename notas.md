## Mediawiki
* Requiere: php, mysql y apache.
* Crear previamente la base de datos en mysql y tener acceso al usuario administrador de base de datos.
  https://www.mediawiki.org/wiki/Manual:Installing_MediaWiki

### Importar archivos csv u hojas de cálculo:

#### Extension Data transfer
* Página en mediawiki: https://www.mediawiki.org/wiki/Extension:Data_Transfer#Importing_CSV_files
* Instalar siguiendo los pasos.
* Agregar en LocalSettings:
```php
// Para activar la extensión
wfLoadExtension( 'DataTransfer' );
// Para que todos los usuarios puedan importar archivos
$wgGroupPermissions['user']['datatransferimport'] = true;
```
Requiere:
	- PHPExcel para importar hojas de cálculo (instalar con composer* como dice en
	https://www.mediawiki.org/w/index.php?oldid=2515889)

* descargar e instalar composer: https://getcomposer.org/download/

### Páginas especiales
Las extensiones instaladas y el acceso a distintas cuestiones administrativas es en:
http://localhost/wiki_proyectos/index.php/Especial:PáginasEspeciales

### Importar csv
Formato del archivo csv para importar:
* Campo Title es obligatorio
* Resto de los campos tienen que tener como formato de nombre: nombre_plantilla[nombre_campo]
* Campos deben ir entre comillas dobles (para esto se debe exportar a csv desde libreoffice calc o excel)
* Palabras o frases que contengan comillas en un texto deben tener comillas duplicadas, por ej `era un día ""especial""`.
* csv de ejemplo:

```
"Title","Publicaciones_especializadas[Organismo_responsable]","Publicaciones_especializadas[ISSN-L]","Publicaciones_especializadas[Ciudad]","Publicaciones_especializadas[Bases_de_datos]","Publicaciones_especializadas[Directrices_para_autores]"
"Abyssinia","Instituto de Literatura Hispanoamericana; Facultad de Filosofía y Letras; Universidad de Buenos Aires",15148025,"Buenos Aires","Latindex","http://catalogosuba.sisbi.uba.ar/vufind/Record/20160317044339891"
"Adquisición y didáctica de lenguas materna y extranjeras","Instituto de Investigaciones Lingüísticas y Literarias; Facultad de Filosofía y Letras; Universidad Nacional de Tucumán. ",23625058,"San Miguel de Tucumán","Latindex",,
"AdVersus","Istituto Italo-argentino de Ricerca Sociale",16697588,"Buenos Aires","Latindex,  Dialnet, Linguistics & Language Behavior Abstracts","http://www.adversus.org/sumario/pautas_publi.htm"
```

### Plantillas
Por ejemplo para usar como variable el campo Organismo responsable en la plantilla `Publicaciones_especializadas`:
` {{{Organismo_responsable}}} `

### Proceso de importación
* Se hace desde http://wikiletras.staberman.com.ar/index.php?title=Especial:ImportCSV
* Una vez hecha la importación no es inmediato el proceso.
* Si se modifica la plantilla que usa un artículo podés "refrescar" el cambio hecho haciendo un Save desde el mismo artículo.

### Git-MediaWiki (para investigar)
* Herramienta para sincronizar el contenido de una wiki usando git desde la consola
https://github.com/Git-Mediawiki/Git-Mediawiki/blob/master/docs/User-manual.md
https://meng6.net/pages/computing/installing_and_configuring/installing_and_configuring_git-mediawiki/
