# Introducción

QGIS (también conocido como Quantum GIS) es un software de código abierto y gratuito que permite la visualización, edición, proceso y distribución de datos geográficos. Al ser un software de código abierto, cualquier persona puede modificar el núcleo del programa para mejorarlo o añadirle nuevas funcionalidades. Un ejemplo claro de este tipo de licencia es el software [NextGIS](http://nextgis.com/nextgis-qgis/), el cual es una versión modificada de QGIS, que a diferencia del original, incluye diversos complementos por defecto, un proceso de instalación diferente e integración con servicios web.

QGIS es un software multi-plataforma, por lo tanto puede ser utilizado diversos sistemas operativos (Windows, MacOS, Linux y Android), a diferencia de softwares comerciales los cuales funcionan casi únicamente en Windows. Además, posee una activa comunidad de usuarios que dan soporte a la resolución de dudas en torno a su uso y de potenciar su uso mediante la creación de complementos.

El último lanzamiento e largo plazo de este software es la versión 3.4, la cual será la distribución a a utilizar por el presente manual (Figura  1).

<div class="figure" style="text-align: center">
<img src="logo.png" alt="Figura  1: Cuadro de bienvenida de QGIS" width="70%" />
<p class="caption">Figura  1: Cuadro de bienvenida de QGIS</p>
</div>

QGIS presenta ventajas comparativas y competitivas en relación a otros softwares SIG de libre acceso presentes en el mercado ya que incorpora dentro de su estructura de procesamiento las funciones de otros softwares populares de libre distribución (como GRASS, SAGA o TauDEM) o la posibilidad de incorporar procesos propios o de terceros mediante un complemento programado en Python o C++.

## Interfaz gráfica

QGIS es un software intuitivo y fácil de utilizar. Su interfaz gráfica (o **GUI** por sus siglas en inglés) está compuesta por (Figura  2): A: pestañas de opciones generales; B: barra de herramientas; C: panel izquierdo (generalmente usado para organizar la información cargada); y D: panel derecho, donde por defecto se aloja la barra de herramientas.

<div class="figure" style="text-align: center">
<img src="base.png" alt="Figura  2: Interfaz gráfica de QGIS" width="100%" />
<p class="caption">Figura  2: Interfaz gráfica de QGIS</p>
</div>


Los elementos de los distintos componentes que conforman el GUI variarán dependiendo de las opciones seleccionadas, las herramientas activadas y los complementos descargados. Realizando un click derecho en los elementos B, C y D se pueden activar o desactivar los paneles y herramientas (Figura  3).

<div class="figure" style="text-align: center">
<img src="activ.png" alt="Figura  3: Activar o desactivar paneles y herramientas" width="80%" />
<p class="caption">Figura  3: Activar o desactivar paneles y herramientas</p>
</div>

# Importación de datos y primeros pasos

Existen múltiples formas de importar archivos a QGIS, y a su vez, múltiples formatos admitidos por QGIS en la importación de archivos. Las maneras formas más utilizadas son las siguientes

 - **Método *drag and drop***: Consiste en simplemente arrastrar desde un directorio un archivo para ser soltado en el panel central de QGIS. Cabe señalar que para utilizar este método hay que conocer cuál es la extensión correcta para vincular el conjunto de archivos que pueden conformar una capa. El ejemplo más común es el formato ESRI Shapefile, el cual almacena datos vectoriales. Una capa consta de mínimo 3 archivos: `*.shp`, `*.shx` y `*.dbf`, de los cuales hay que arrastrar el archivo cuya extensión sea `*.shp`.
 
 - **Utilizar el Administrador de fuentes de datos**: el `Administrador de fuentes de datos` es una herramientas que permite cargar archivos de diferentes extensiones desde un menú de selección. Para acceder a ella se debe presionar sobre el botón ![](boton.png){width=2%} directo en la barra de herramientas o ir a la pestaña `Capa / Administrador de fuentes de datos`. Se abrirá una ventana emergente en al cual se debe seleccionar la naturaleza del archivo, ya sea vectorial, ráster, GeoPackage, SpatiaLite, PostgreSQL, etc (Figura  4).

<div class="figure" style="text-align: center">
<img src="adminis.png" alt="Figura  4: Administrador de fuentes de datos" width="70%" />
<p class="caption">Figura  4: Administrador de fuentes de datos</p>
</div>

## Modelo vectorial

A modo de ejemplo, se cargará una capa vectorial del conjunto de datos facilitado para el presente curso. La capa tiene por nombre `Limite_Cuencas_BNA.shp`, nótese que al señalar la extensión `*.shp` de inmediato asociamos este archivo a una cobertura vectorial de formato ESRI Shapefile, el cual fue mencionado en párrafos anteriores. El archivo se encuentra en la carpeta `ArchivosSIG / Datos vectoriales / DGA / Limite_cuencas_BNA` (Figura  5).

<div class="figure" style="text-align: center">
<img src="ruta.png" alt="Figura  5: Ruta de acceso al archivo" width="60%" />
<p class="caption">Figura  5: Ruta de acceso al archivo</p>
</div>

Una vez cargado el archivo, proceder a cerrar el Administrador de fuentes de datos y observar la capa cargada. En este caso, el modelo de datos es de tipo vectorial y cuya geometría es del tipo líneas (Figura  6):

<div class="figure" style="text-align: center">
<img src="capa.png" alt="Figura  6: Archivo vectorial cargado" width="70%" />
<p class="caption">Figura  6: Archivo vectorial cargado</p>
</div>

Para poder navegar por la capa se utilizan los botones que aparecen en la barra de herramienta ![](navegar.png){width=20%} o con el tercer botón del mouse y el scroll del mismo.

Por lo general, la creación de archivos vectoriales está asociado a la administración de información de variada naturaleza asociada a límites geográficos. Estos vectores tienen en su estructura un base de datos denominada tabla de atributos.

La tabla de atributos está compuesta por filas y columnas, donde cada fila corresponde a una observación y cada columna a una variable. Todas las capas vectoriales incluyen un campo denominado FID (*Feature ID*) u OID (*Object ID*), los cuales están destinados a numerar cada una de las características de la capa vectorial. Muchas veces este campo está oculto en algunos softwares SIG, pero siempre está presente.

Para acceder a la tabla vectorial se debe clickear el botón ![](tab.png){width=2%} o clickear con el botón derecho del mouse sobre el nombre de la capa en panel de la izquierda y seleccionar `Abrir tabla de atributos`.

La tabla de atributos de las capas vectoriales muchas veces puede críptica y difícil de descifrar, ya que los nombres de la columnas no pueden exceder los 10 caracteres, deben comenzar con una letra, no puede repetirse el nombre en la misma tabla y no hay un lugar donde incorporar una descripción de la variable en el formato estándar de ESRI Shapefile.

<div class="figure" style="text-align: center">
<img src="tab2.png" alt="Figura  7: Tabla de atributos de la capa cargada" width="60%" />
<p class="caption">Figura  7: Tabla de atributos de la capa cargada</p>
</div>

En el ejemplo se aprecian dos variables, `TIPO_ID` y `TIPO`. La variable `TIPO_ID` hace referencia a el código de cada tipo de límite hidrográfico, mientras que `TIPO` informa la descripción de dicho código, en el Cuadro  1 se presentan las posibles observaciones para esta capa vectorial.

<table class="table" style="margin-left: auto; margin-right: auto;">
<caption>Cuadro  1: Código y descripción del tipo de límite</caption>
 <thead>
  <tr>
   <th style="text-align:center;"> Código </th>
   <th style="text-align:right;"> Descripción </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:center;"> 1 </td>
   <td style="text-align:right;"> Cuenca </td>
  </tr>
  <tr>
   <td style="text-align:center;"> 2 </td>
   <td style="text-align:right;"> Subcuenca </td>
  </tr>
  <tr>
   <td style="text-align:center;"> 3 </td>
   <td style="text-align:right;"> Subsubcuenca </td>
  </tr>
</tbody>
</table>

Al cargar una capa vectorial, esta tendrá asignado un color aleatorio por defecto. Para modificar el color de la capa, se debe acceder a las propiedades de esta misma ejecutando un click con el botón derecho del mouse sobre el nombre de la capa en el panel de capas (Figura  8).

<div class="figure" style="text-align: center">
<img src="prop.png" alt="Figura  8: Menú desplegable" width="30%" />
<p class="caption">Figura  8: Menú desplegable</p>
</div>

Esto abrirá las propiedades de la capa. La acción de modificar el color, tamaño y patrón de las líneas se ejecuta desde la pestaña de `Simbología`. La simbología, al igual que otros términos dentro del contexto de los Sistemas de Información Geográfica, se encuentra definida en la sección **Glosario**.  La pestaña `Información` muestra algunos datos de la capa cargada, por ejemplo el nombre, ruta, driver (o formato), codificación, tipo de geometría, SRC (Sistema de coordenadas de referencia), extensión (X máximo, X mínimo, Y máximo y Y mínimo), la unidad del sistema de referencia de la capa y el número de entidades de la capa (Figura  9).

<div class="figure" style="text-align: center">
<img src="prop2.png" alt="Figura  9: Propiedades de la capa vectorial" width="50%" />
<p class="caption">Figura  9: Propiedades de la capa vectorial</p>
</div>

En la pestaña de Simbología se configura la manera de cómo se representa cada entidad. Se puede configurar el ancho, diseño de las líneas, comportamiento entre las intersecciones de diferentes líneas, el color, entre otras cosas. También, algo muy útil es el uso de símbolos complejos, por ejemplo: en vez de utilizar un único estilo de simbología para todas las entidades se pueden realizar diferenciaciones en base a categorías, graduaciones (de color o tamaño) o mezclar ambos tipos de clasificación (Figura  10). En este caso se realiza una clasificación por categoría usando el campo `TIPO` para modificar el color de las líneas en base al tipo de límite hidrográfico.

<div class="figure" style="text-align: center">
<img src="simbo.png" alt="Figura  10: Opciones de simbología de una capa vectorial de lineas" width="70%" />
<p class="caption">Figura  10: Opciones de simbología de una capa vectorial de lineas</p>
</div>

Una vez aplicado el nuevo estilo de simbología, se puede apreciar la variedad de límites que posee la capa vectorial (Figura  11). Sin referencia extra, es muy difícil ubicar los límites con alguna cuenca conocida sin tener el conocimiento o entrenamiento visual apropiado para identificar fácilmente las cuencas por su forma. Por ello, la utilización de un **mapa base** es útil para poder tener una referencia espacial de lo que nuestros ojos observan.

<div class="figure" style="text-align: center">
<img src="simbo2.png" alt="Figura  11: Resultado de la aplicación de una simbología categorizada" width="70%" />
<p class="caption">Figura  11: Resultado de la aplicación de una simbología categorizada</p>
</div>

Tal como se mencionó en la introducción del presente documento, QGIS es un software que posibilita la instalación múltiples *plug-ins*. Hay más de un *plug-in* que permite integrar mapas base al panel de capas. De todos los existentes, el más estable y con más opciones es **QuickMapServices**, el cual permite cargar mapas base desde Google Earth, Bing, OpenStreetMap, entre otros.

Para acceder a los *plug-ins* o complementos hay que dirigirse a a la pestaña `Complementos / Administrar e instalar complementos`. En el cuadro que se abre aparece la descripción de esta herramientas para la instalación, actualización y desinstalación de complementos (Figura  12).

<div class="figure" style="text-align: center">
<img src="comple.png" alt="Figura  12: Ventana de complementos" width="70%" />
<p class="caption">Figura  12: Ventana de complementos</p>
</div>

En la barra de buscador, escribir `QuickMapServices`, seleccionar el complemento filtrado e instalar. Luego de la instalación, debiera aparecer un panel similar al de la Figura  13. En la barra `Search string...` se teclea el mapa base que uno desea añadir. A modo de ejemplo escribir `Google Satellite Hybrid` y añadir el mapa base pulsando el botón `Add`.

<div class="figure" style="text-align: center">
<img src="qms.png" alt="Figura  13: Panel de QuickMapServices" width="25%" />
<p class="caption">Figura  13: Panel de QuickMapServices</p>
</div>

La capa añadida con etiqueta incluida permite tener una referencia del territorio Figura  14. Así es posible vincular los límites de la cuencas del Banco Nacional de Aguas de la DGA con el espacio.

<div class="figure" style="text-align: center">
<img src="base2.png" alt="Figura  14: Mapa base añadido al panel de capas" width="70%" />
<p class="caption">Figura  14: Mapa base añadido al panel de capas</p>
</div>

## Modelo ráster

Para ejemplificar la importación de archivos ráster se importará un modelo de elevación digital, el SRTM de 90 m de resolución de pixel reproyectado. El procedimiento es el mismo que se debe realizar con la importación de datos vectoriales, sólo hay que elegir la pestaña adecuada (botón ![](ras.png){width=5%}) y seleccionar la ruta de `ArchivosSIG / Datos ráster / DEM.tif` en la carpeta del curso.

Lo más probable es que la capa se cargue por sobre las demás, obstaculizando la visualización de la capa vectorial antes cargada. Para poder modificar el orden de las capas, se debe arrastrar dicho elemento desde el panel de capas hacia una ubicación que permita la comprensión de las múltiples capas hasta ahora cargadas. Esta sería (Figura  15):

1. Capa vectorial de los límites de las cuencas
2. Modelo de elevación digital
3. Mapa base

<div class="figure" style="text-align: center">
<img src="ordn.png" alt="Figura  15: Orden de capas" width="30%" />
<p class="caption">Figura  15: Orden de capas</p>
</div>

El procedimiento para verificar la información de la capa ráster, como también para cambiar la simbología, es el mismo que para una capa vectorial. Sí hay diferencias por el modelo de datos.

Las capas ráster no contienen tabla de atributos (en casos excepcionales las hay) ya que cada imagen representa una variable y cada pixel una observación. 

Existen archivos ráster denominados multi-banda que están compuestos por dos o más imágenes apiladas. Para este caso, cada banda representa una variable diferente. Puede ser que cada banda represente un canal de un espectro electromagnético de la teledetección, un índice espectral, una fecha de análisis, etc.

Existe una herramienta que funciona tanto para rásters como para vectores que se denomina `Identificar objetos espaciales`. Para acceder a ella hay que clickear el botón ![](ras.png){width=2%}) en la Barra de herramientas. **Se debe tener seleccionada la capa a consultar en el panel de capas (el subrayado del nombre de la capa indica la selección)**.

En la Figura  16 se utilizó esta herramienta para identificar el valor de un pixel cercano al faro monumental. El resultado de la consulta es `Banda 1  4.317021`, esto significa que el valor de elevación del pixel consultado es de 4 m.s.n.m. con una gran cantidad de decimales y que la banda consultada es la número 1 (es de esperar, ya que no es un archivo multibanda). El DEM inicialmente estaba en un sistema de coordenadas geográficas (WGS 84 Long/Lat) el cual fue reproyectado a un sistema de coordenadas cartesiano (SIRGAS 2000 UTM Huso 19 Sur) mediante el método de remuestreo de pixel Bilinear, el cual interpola valores entre varios pixeles (para conocer más de los métodos disponibles visitar [https://gisgeography.com/raster-resampling/](https://gisgeography.com/raster-resampling/)) y genera valores con una gran cantidad de valores, a pesar de que originalmente el set de datos es tipo numérico entero.

<div class="figure" style="text-align: center">
<img src="sele.png" alt="Figura  16: Consulta del valor de un pixel" width="70%" />
<p class="caption">Figura  16: Consulta del valor de un pixel</p>
</div>

Algo muy interesante para utilizar en archivos ráster que representan modelos de elevación o superficie digital es el mapa de sombras (o *Hillshade*) el cual se puede calcular mediante un geoproceso o aplicar como simbología sobre una capa ráster. La segunda opción es la más práctica cuando sólo se pretende visualizar el set de datos y no relacionar el valor del mapa de sombras con algún fenómeno (como la cuantificación de horas luz en un terreno agrícola, pensando en el posible sombreamiento en los meses de invierno).

Para la aplicación de este tipo e simbología, ir a `Propiedades / Simbología / Tipo de renderizador / Mapa de Sombras (Hillshade)` (Figura  17). Dentro de esta ventana se configura el ángulo de altura solar (que tan elevado está con respecto al horizonte), el ángulo de acimut solar (la dirección en grados sexagesimales con respecto al norte), el factor Z (en este caso es 1 ya que la altitud está en metros y el sistema de coordenadas de referencia también lo está, este factor es un conversor de unidades entre la el eje horizontal y vertical).

<div class="figure" style="text-align: center">
<img src="hill.png" alt="Figura  17: Propiedades de la capa - Simbología" width="70%" />
<p class="caption">Figura  17: Propiedades de la capa - Simbología</p>
</div>

El resultado se aprecia en la Figura  18. Nótese que ya no está presente la capa de los límites de la cuenca, ya que se desactivo deseleccionado la casilla que está a la izquierda del nombre de la capa en el Panel de capas.

<div class="figure" style="text-align: center">
<img src="hill2.png" alt="Figura  18: Resultado aplicación mapa de sombras" width="70%" />
<p class="caption">Figura  18: Resultado aplicación mapa de sombras</p>
</div>

Una de la novedades de QGIS 3 es la creación de vistas 3D, herramienta muy útil para ver el relieve de los modelos de elevación digital. Cabe mencionar que al ser una característica relativamente nueva, QGIS puede fallar (ya que es un software gratuito, la puesta a punto de las herramientas recientemente incorporadas demora un tiempo razonable antes de ser herramientas estables). Para no perder ningún avance, hay que salvar el proyecto clickeando el botón ![](salvar.png){width=1.7%} o ir a la pestaña `Proyecto / Guardar`. Se debe especificar nombre y ruta (la que usted desee) y el proyecto guardará la ruta y simbología de las capas abiertas en él, mas no los archivos (para evitar duplicidad de archivos).

Para crear una nueva vista hay que ir a la pestaña `Ver / Nueva vista de mapa 3D` e ir a la configuración de la ventana clickeando el botón ![](llave.png){width=2%}. La configuración puede ser similar a la mostrada en la Figura  19, es utilizó una escala vertical de 5 para exagerar el relieve del territorio y diferenciar cerros y quebradas a nivel regional.

<div class="figure" style="text-align: center">
<img src="3d.png" alt="Figura  19: Ventana de configuración de la ventana 3D" width="50%" />
<p class="caption">Figura  19: Ventana de configuración de la ventana 3D</p>
</div>

La navegación dentro de la capa se realiza con el botón derecho y el tercer botón del mouse (por lo general, botón ubicado junto con el scroll). Ya que se puede modificar la cámara del usuario en relación a este mapa 3D, se puede visualizar un panorama general de la región y parte de Argentina (Figura  20)

<div class="figure" style="text-align: center">
<img src="3d2.png" alt="Figura  20: Vista del mapa 3D" width="80%" />
<p class="caption">Figura  20: Vista del mapa 3D</p>
</div>

## Análisis multitemporal

Otro *plug-in* muy interesante es `MUTANT` (por las siglas de *MUlti Temporal ANalysis Tool*). Es una herramienta muy similar a `Identificar objetos espaciales`, pero a diferencia de aquella herramienta, es posible obtener el valor de múltiples capas al mismo tiempo e incluso graficar dichos valores.

Para instalar el complemento se debe seguir el mismo paso descrito anteriormente. Además, cargar todas las capas ráster ubicadas en la carpeta `ArchivosSIG / Datos ráster / SnowIndex /` (un total de 48, con extensión `*.tif`). Cada una de estas capas corresponde al máximo valor de el índice de nieve estandarizado (*NDSI*) para cada mes desde enero del 2015 a diciembre del 2018 (hasta los primeros días de este mes).

Los datos fueron generados en la plataforma de webGIS Google Earth Engine, plataforma que se enfoca en el manejo de datos satelitales en la nube (utilizando los servidores globales de Google) mediante la utilización del lenguaje de programación JavaScript (Figura  21).

<div class="figure" style="text-align: center">
<img src="gee.png" alt="Figura  21: Plataforma Google Earth Engine" width="90%" />
<p class="caption">Figura  21: Plataforma Google Earth Engine</p>
</div>

Las capas tienen por nombre `NDSI_15_MM_YYYY.tif`, siendo `NDSI` por el nombre del índice, `_15` por el día central del mes, `_MM` por el mes en formato numérico, `_YYYY` por el año en formato numérico y `.tif` por el formato del archivo ráster. Para probar el complemento, guardar el proyecto, quitar la capa vectorial, la del modelo de elevación vectorial y activar el *plug-in* (si no aparece el cuadro del complemento, activar desde los paneles).

Dentro del cuadro del *plug-in*, ir a la pestaña `Time`, activar la casilla `Enable multi-temporal analysis`, tener activa sólo la casilla `Filename` en el recuadro blanco, cortar los primeros 5 caracteres y en `Datepattern` escribir `%d_%m_%Y` para configurar el formato de fecha de cada imagen (Figura  22).

<div class="figure" style="text-align: center">
<img src="mut.png" alt="Figura  22: Complemento MUTANT" width="70%" />
<p class="caption">Figura  22: Complemento MUTANT</p>
</div>

Luego, cambiar a la pestaña `Graph` y pasar el mouse por sobre las imágenes. El resultado debe ser una tabla como la que se muestra en la Figura  23. También se puede ver la tabla de datos desde la pestaña `Table`.

<div class="figure" style="text-align: center">
<img src="mut2.png" alt="Figura  23: Gráfico multitemporal de NDSI" width="90%" />
<p class="caption">Figura  23: Gráfico multitemporal de NDSI</p>
</div>

El complemento MUTANT está en etapa de adaptación a la versión de QGIS 3, por lo tanto puede que falle en algún proceso. Para la versión de QGIS 2.x, el complemento funciona sin fallas. Ante cualquier falla, se recomienda la utilización de QGIS 2.18 LTR para este tipo de consultas espaciales.

# Composición cartográfica

Para crear una cartografía digital se debe ir a la pestaña `Proyecto / Nueva composición de impresión` o presionar el botón ![](compo.png){width=1.7%}. Se abrirá un cuadro emergente en donde se debe indicar el nombre que se le dará a esa composición, ingresar el que usted desee y presionar en `OK`. 

Se abrirá una ventana emergente muy parecida al navegador de capas de QGIS. También contiene pestañas en la zona superior. Pero además contiene (Figura  24): A) Barra de herramientas superior; B) Barra de herramientas lateral; C) Panel de opciones; D) Composición.

<div class="figure" style="text-align: center">
<img src="disenador.png" alt="Figura  24: Diseñador de impresión" width="100%" />
<p class="caption">Figura  24: Diseñador de impresión</p>
</div>

Para añadir gran parte de los elementos basta con utilizar la barra de herramientas lateral. Lo primero que se debe realizar es añadir una vista de mapa presionando el botón ![](mapa.png){width=1.7%}. Se realiza un primer click donde se pretende colocar uno de los vértices del mapa (en la composición) y se mantiene presionado hasta posicionar el segundo vértice del rectángulo, para soltar el botón del mouse y que se incorpore el mapa. Una vez que se añade el mapa, se activarán las propiedades de este elemento en el panel de opciones al lado derecho Figura  25.

<div class="figure" style="text-align: center">
<img src="mapp.png" alt="Figura  25: Añadir mapa a la composición" width="100%" />
<p class="caption">Figura  25: Añadir mapa a la composición</p>
</div>

Para el ejemplo mostrado en la figura anterior, se seleccionó solo un mes de la serie temporal de nieve en la cuenca y se configuró la simbología para que se excluyeran de la visualización los valores inferiores a 40 (<0.4 NDSI).

Diversas propiedades pueden ser configurables desde este panel. Entre ellas se destacan:

 - **Escala**: de referencia, por el número 1000 equivale a una escala de 1:1000
 - **Capas**: para bloquear capas o sus estilos de capa, ya que si se cambia alguna propiedad en el panel de capas esta se ve reflejada en el diseñador de impresión
 - **Extensión**: para definir las coordenadas del rectángulo del mapa.
 - **Controlado por Atlas**: para configurar la generación de múltiples cartografías de manera automatizada.
 - **Cuadrículas**: para crear una grilla o marcas de referencia en algún sistema de coordenadas sobre el mapa.
 - **Vistas generales**: si es que hay más de un mapa en la composición, para señalar con un rectángulo la extensión de uno o más en referencia al que se está configurando.
 - **Posición y tamaño**: ajuste de posición del mapa y el tamaño de este (en unidad de longitud).
 - **Rotación**: rotación del mapa con respecto a la posición definida en la opción anterior.
 - **Marco**: para añadir un marco que delimite el rectángulo del mapa.
 - **Fondo**: para incorporar un fondo en el mapa (sólo visible si no hay mapa base y si las entidades no cubren la extensión del rectángulo)
 - **Otras opciones**: para definir ID o revisar las propiedades del mapa.

Para agregar una escala gráfica, se debe presionar el botón de la herramienta `Añadir nueva barra de escala` ![](escala.png){width=1.7%} y personalizar en base a las opciones que esta incorpora, por ejemplo la unidad de longitud, etiqueta, unidades de mapa por unidad de barra (si se utiliza kilómetro, debe ser 1000 por ejemplo), la cantidad de segmentos, tamaño, altura, color etc.

Para añadir una flecha de norte se debe incorporar una imagen presionando el botón ![](imagen.png){width=1.7%}, desplegar la pestaña de `Directorios de búsqueda` y seleccionar la flecha de norte que desee (Figura  26).
 
<div class="figure" style="text-align: center">
<img src="mapp2.png" alt="Figura  26: Mapa con algunos elementos básicos" width="100%" />
<p class="caption">Figura  26: Mapa con algunos elementos básicos</p>
</div>

Para mejorar la comprensión del mensaje que se quiere transmitir con la cartografía, es muy útil utilizar polígonos invertidos sobre una capa vectorial de polígonos como simbología para centrar la vista en el objeto de análisis Figura  27. Para ello se debe configurar la simbología en las propiedades de la capa de cuencas del BNA, se puede utilizar un filtro o `Definition query` para excluir el resto de cuencas de Chile y sólo centrar la visualización en la cuenca de Rio Limarí:

<div class="figure" style="text-align: center">
<img src="inv.png" alt="Figura  26: Mapa con algunos elementos básicos" width="70%" />
<p class="caption">Figura  26: Mapa con algunos elementos básicos</p>
</div>

El resultado (Figura  28) se verá reflejado en el mapa añadido a la cartografía. Hay otros elementos que deben ser añadidos, como la grilla de las coordenadas, leyenda, título o referencia cartográfica. Queda en vuestras manos la exploración de la herramienta y cualquier consulta posterior puede ser realizada a mi persona mediante un correo a `aatapia@userena.cl`.

<div class="figure" style="text-align: center">
<img src="carto.png" alt="Figura  28: Aplicación de polígonos invertidos como simbología" width="70%" />
<p class="caption">Figura  28: Aplicación de polígonos invertidos como simbología</p>
</div>


# Glosario

 - **Arcos**: línea recta o curva que une dos puntos. 
 - **Buffer**: termino en inglés, es una herramienta que aplica una función de proximidad creando un polígono a una distancia dada sobre una característica seleccionada o varias características. 
 - **Cartas**: son mapas especialmente diseñados para cubrir las necesidades de los navegantes tanto náuticos como aéreos. Sobre ellas se determinan posiciones, se trazan trayectorias, se señalan rumbos, etc.
 - **Cartografía**: Es la ciencia que estudia los diferentes métodos o sistemas que permiten representar en un plano, una parte o la totalidad de la superficie terrestre. 
 - **Cartogramas**: es un mapa o diagrama que muestra datos de cantidad asociados a sus respectivas áreas, mediante la modificación de los tamaños de las unidades de enumeración. La información es aportada mediante la distorsión de las superficies reales, utilizando cada superficie de enumeración como un símbolo proporcional, el cual aumenta o disminuye en función de los valores correspondientes.
 - **Centroide**: punto central de un polígono, puede decirse que es el punto donde si una recta lo atraviesa, queda dividido en dos segmentos de idéntico momento respecto a la recta en cuestión.
 - **Coropletas**: un mapa de coropletas es un mapa temático, en el que las regiones se colorean de un motivo, para representar y facilitar la comparación de una medida estadística de una región, como por ejemplo la densidad de población. 
 - **Coordenadas geográficas**: son los valores de latitud y longitud que permiten determinar la posición de un punto sobre una superficie básicamente esférica, como puede ser La Tierra.
 - **Coordenadas cartesianas**: valores de abscisas y ordenadas, X e Y respectivamente que permiten determinar la posición de un punto sobre una superficie plana.
 - **Dátum**: es el punto donde coinciden las verticales del geoide y el elipsoide, así como las coordenadas astronómicas y geodésicas y sirve de referencia para la determinación del recto de los vértices.
 - **Elipsoide**: Es una superficie curva cerrada cuyas tres secciones ortogonales principales son elípticas, es decir, son originadas por planos que contienen dos ejes cartesianos. Un elipsoide se obtiene al *deformar* una esfera, mediante una transformación homológica, en la dirección de sus tres diámetros ortogonales. 
 - **Entidad**: pueden ser puntos, líneas o polígonos con posición geográfica que representa una característica del mundo real. 
 - **Escala (barra)**: relación de semejanza que se establece entre las dimensiones reales de un objeto y su imagen sobre el mapa.
 - **Geodesia**: es la ciencia que tiene por objeto el estudio de la forma, dimensiones y campo gravitatorio de La Tierra.
 - **Geoide**:  es un cuerpo de forma casi esférica, aunque con un ligero achatamiento en los polos, definido por la superficie equipotencial del campo gravitatorio terrestre, que considera la variación de la gravedad debida a la distribución irregular de la masa terrestre, este es perpendicular en cada uno de sus puntos a la dirección de la gravedad.
 - **Impedancia**: de un arco, se define como la resistencia puesta para ser recorrido, desde uno de sus extremos (nodo) a otro. 
 - **Isolíneas**: líneas que representan puntos del espacio donde el fenómeno adquiere el mismo valor, ejemplo curvas de nivel.
 - **Líneas automecoicas**:  líneas que conservan las longitudes en determinadas direcciones. 
 - **Mapa**: representación gráfica, sobre una superficie plana, de una parte, o el total de la superficie terrestre. Poseen gran diversidad de tamaños y tipos según su escala, tema a tratar, etc.
 - **Nodo**: un punto de intersección o unión de varios elementos que confluyen en el mismo lugar. 
 - **Planos**: son mapas realizados a una escala relativamente grande y sin utilizar proyección geográfica. Usualmente están emplazados en coordenadas cartesianas arbitrarias o bajo un sistema de coordenadas de referencia cuya unidad sea metro o pie.
 - **Proyección cartográfica**: es el método usado para realizar una representación de una parte o el total de la superficie terrestre obtenida por transformación de una superficie básicamente esférica (como puede ser La Tierra) en una superficie plana (como puede ser un mapa).
 - **Simbología**: técnica para representar una entidad o característica mediente patrones gráficos.
 - **Sinuosidad**: de las líneas, es el índice que determina que tanto se aleja el trazado de una línea con respecto a la ruta más corta; el cociente entre la longitud de la línea y la distancia que separa sus dos puntos extremos.
 - **Teledetección**: es la técnica que permite obtener información a distancia de objetos (situados en la superficie terrestre, marina o en la atmósfera), sin que exista un contacto material. Para ello, es necesario que, aunque sin contacto material, exista algún tipo de interacción entre los objetos observados y un sensor situado en una plataforma (satélite, avión, etc.). 
 - **Tesela**: o celdilla, es la entidad mínima de una capa ráster.
 - **Topología**: conjunto de reglas que dicta las propiedades espaciales de las características de punto, línea o área, tales como conectividad adyacencia y contigüidad.
