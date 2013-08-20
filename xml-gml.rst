###
XML
###

Qué es el XML
#############
El XML (eXtensible Markup Language = Lenguaje de Marcas Extensible) no es un lenguaje de marcas, sino un metalenguaje, es decir, el XML define las reglas generales que debe cumplir un lenguaje de marcas y la manera de definir un lenguaje de marcas.
El XML fue creado por el W3C a finales de los 90. El W3C se creó en 1994 para tutelar el crecimiento y organización de la web. Su primer trabajo fue normalizar el HTML, el lenguaje de marcas con el que se escriben las páginas web. Al crecer el uso de la web, crecieron las presiones para ampliar el HTML. El W3C decidió que la solución no era ampliar el HTML, sino crear unas reglas para que cualquiera pudiera crear lenguajes de marcas adecuados a sus necesidades, pero manteniendo unas estructuras y sintaxis comunes que permitieran compatibilizarlos y tratarlos con las mismas herramientas. Ese conjunto de reglas es el XML, cuya primera versión se publicó en 1998.
Lógicamente, el HTML no cumple las normas del XML ya que el HTML es anterior al XML. El creador del HTML, Tim Berners-Lee, se basó en el SGML, otro conjunto de reglas para la creación de lenguajes de marcas creado en los años 80 y más complejo que el XML. Una vez creado el XML, el W3C aprobó en el año 2000 el XHTML, una versión del HTML que sí que cumple las reglas del XML. El W3C pretendió sin éxito que el HTML dejara de utilizarse y sólo se utilizara XHTML. Al no conseguirlo, el W3C decidió retomar el desarrollo del HTML (incluyendo en él una versión XHTML). No se espera que la próxima versión de HTML, el HTML 5, esté terminada antes del 2014, pero los navegadores ya incorporan muchas de sus características.
Por su parte, el éxito del XML ha sido enorme y cada vez es más utilizado como sistema de intercambio y almacenamiento de información. El W3C ha desarrollado alrededor del XML numerosas tecnologías para sacar provecho del XML.

Conceptos y vocabulario
#######################

* Documento XML Un documento XML es un documento de texto plano (sin formato).
* Procesador XML (XML processor) y aplicación (application) Cuando una aplicación necesita leer un documento XML, la aplicación recurre a un procesador XML. El procesador XML (o analizador XML, en inglés XML **parser**) es el que lee el documento, analiza el contenido y le pasa la información en un formato estructurado a la aplicación. La recomendación XML especifica lo que debe hacer el procesador, pero no entra en lo que hace después la aplicación con esa información.
* Caracteres (**character encoding**) Los documentos XML pueden estar codificados en distintos juegos de caracteres (iso-8859-1, utf-8, etc).
* Marcas (mark-up) y contenido (content) El texto que contiene un documento XML se divide en marcas y contenido. Las marcas pueden ser de dos tipos: etiquetas o referencias a entidades. Todo lo que no son marcas es contenido.
* Etiquetas (tags) Una etiqueta es una marca que empieza con el caracter "<" y termina con ">". Existen tres tipos de etiquetas:
	1. las etiquetas de apertura (start-tag). Por ejemplo: <apartado>
	2. las etiquetas de cierre (end-tag), que empiezan por "/". Por ejemplo: </apartado>
	3. las etiquetas vacías (empty tag), que terminan por "/". Por ejemplo: <salto-de-linea />
* Elementos (elements) Un elemento es un componente lógico de un documento que o bien comienza por una etiqueta de apertura y termina por la etiqueta de cierre correspondiente o que consiste en una única etiqueta vacía. El contenido de un elemento es todo lo que se encuentra entre las etiquetas de apertura y cierre, incluso si estos son también elementos en cuyo caso se llaman elementos hijos.
* Atributos (attributes) Un atributo es un componente de las etiquetas que consiste en una pareja nombre (name) / valor (value). Se puede encontrar en las etiquetas de apertura o en las etiquetas vacías, pero no en las de cierre. En una etiqueta no puede haber dos atributos con el mismo nombre. La sintaxis es siempre nombreAtributo="valorAtributo". Por ejemplo::

	<profesor nombre="Bartolomé" apellidos="Sintes Marco" />

* Instrucciones de procesamiento (PI, processing instruction) Una instrucción de procesamiento en una etiqueta que empieza por "<?" y acaba por "?>" y que contiene instrucciones dirigidas a las aplicaciones que leen el documento. Pueden aparecer en cualquier lugar del documento. Por ejemplo::

	<?xml-stylesheet type="text/xsl" href="estilo.xsl" ?>

* Declaración XML (XML declaration) La declaración XML es una etiqueta que comienza por "<?xml " y termina por "?>" y que proporciona información sobre el propio documento XML. Aunque no es obligatoria es conveniente que aparezca, y debe aparecer siempre al principio del documento. No es una instrucción de procesamiento, pero tiene la misma sintaxis (empieza por <? y acaba por ?>). Es importante que el juego de caracteres que aparece en la declaración sea el juego de caracteres en que realmente está guardado el documento, porque si no el procesador XML puede tener problemas leyendo el documento.Por ejemplo::

	<?xml version="1.0" encoding="iso-8859-1"?>
	<?xml version="1.0" encoding="utf-8"?>

* Definición de tipo de documento (DTD, Document Type Definition) Una DTD es un documento que define la estructura de un documento XML: los elementos, atributos, entidades, notaciones, etc, que pueden aparecer, el orden y el número de veces que pueden aparecer, cuáles pueden ser hijos de cuáles, etc. El procesador XML la utiliza para verificar si un documento es válido, es decir, si el documento cumple las reglas del DTD.
* Declaración de tipo de documento (DOCTYPE, Document type declaration) Una declaración de tipo de documento es una etiqueta que comienza por "<?DOCTYPE" y acaba por "?>" y que indica la(s) DTD(s) que debe utilizar el procesador XML para validar el documento. La DTD puede estar incluida en el propio documento o ser un documento externo. Por ejemplo, el sigueinte ejemplo muestra la declaración de documento que se debe incluir en los documentos xhtml de tipo strict::

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

* Comentarios (comments) Un comentario es una etiqueta que comienza por "<!--" y acaba por "-->". Los comentarios no pueden estar dentro de otras marcas y no pueden contener los caracteres "--". Dentro de un comentario las entidades de carácter no se reconocen, es decir, sólo se pueden utilizar los caracteres del juego de caracteres del documento. Por ejemplo::

	<!-- Esto es un comentario -->

* Secciones CDATA (CDATA section) Una sección CDATA es una etiqueta que comienza por "<![CDATA[" y termina por "]]>" y cuyo contenido el procesador XML no interpreta como marcas sino como texto. Es decir que si aparecen los caracteres especiales (< & " ') en una sección CDATA, el procesador XML no interpreta que empieza un marca sino lo considera un carácter más. Se suele utilizar en documentos en los que aparecen muchas veces esos caracteres especiales para no tener que estar utilizando las referencias a entidades (&lt; &amp; &quot &apos;) que hacen el texto bastante incómodo de leer.

Sintaxis de XML
###############

La finalidad de XML es marcar información —describir datos— de una forma sencilla e independiente de la aplicación que requiera esa información. Un mismo XML se podría utilizar para presentar un contenido en un navegador, importarlo a una base de datos, o intercambiar información entre diversas aplicaciones.
Como todos los lenguajes de marcado, el aspecto que presenta el código XML es el de elementos que engloban texto y que se pueden anidar. Sin embargo, a diferencia de HTML, los elementos no están definidos, sino que se crean en el momento de aplicarlos, adaptados al contenido que se va a recoger. Por ejemplo, este sería un XML con la lista de los discos de TOOL::

    <discografía_tool>
        <lp>Opiate</lp>
        <lp>Undertow</lp>
        <lp>AEnima</lp>
        <lp>Salival</lp>
        <lp>Lateralus</lp>
        <lp>10,000 Days</lp>
    </discografía_tool>
            
Para ampliar la información contenida, se podrían anidar distintos elementos dentro de los elementos iniciales::

    <discografía_tool>
        <lp>
            <título>Opiate</título>
            <año>1992</año>
            <discográfica>Zoo/BMG/Volcano</discográfica>
            <temas>
                <tema>Sweat</tema>
                <tema>Hush</tema>
                <tema>Part of Me</tema>
                <tema>Cold and Ugly (live)</tema>
                <tema>Jerk-Off (live)</tema>
                <tema>Opiate</tema>
                <tema>The Gaping Lotus Experience</tema>
            </temas>
        </lp>
        <lp>
            <título>Undertow</título>
            <año>1993</año>
            <discográfica>Zoo/BMG/Volcano</discográfica>
            <temas>
                <tema>Intolerance</tema>
                <tema>Prison Sex</tema>
                <tema>Sober</tema>
                <tema>Bottom</tema>
                <tema>Crawl Away</tema>
                <tema>Swamp Song</tema>
                <tema>Undertow</tema>
                <tema>4º</tema>
                <tema>Flood</tema>
                <tema>Disgustipated</tema>
            </temas>
        </lp>
        …
    </discografía_tool>
            
Por último, cada elemento acepta atributos —siempre que su valor vaya entrecomillado—, que como los primeros son definidos según las necesidades del autor y de los contenidos. Supongamos que posteriormente vamos a utilizar el XML anterior como un archivo de datos. Para poder procesar cada disco por separado, se podría buscar por el título dentro de cada elemento lp, pero resulta más efectivo añadir un identificador a cada uno::

    <discografía_tool>
        <lp identificador="01">
            <título>Opiate</título>
            <año>1992</año>
            <discográfica>Zoo/BMG/Volcano</discográfica>
            <temas>
                <tema>Sweat</tema>
                …
            </temas>
        </lp>
        <lp identificador="02">
            <título>Undertow</título>
            <año>1993</año>
            <discográfica>Zoo/BMG/Volcano</discográfica>
            <temas>
                <tema>Intolerance</tema>
                …
            </temas>
        </lp>
        …
    </discografía_tool>


Con esto queda descrita la sintaxis de XML. Sólo hay que tener en cuenta una serie de reglas sencillas que se deben aplicar a la hora de crear un documento:

* Ningún elemento puede aparecer sin su correspondiente cierre.
* XML es sensible al caso, por lo que lp y LP se considerarían elementos distintos.
* Los elementos deben estar anidados correctamente. Así, <elemento_1><elemento_2> contenido </elemento_2></elemento_1> es correcto, pero <elemento_1><elemento_2> contenido </elemento_1></elemento_2> genera un error en un analizador sintáctico (parser) de XML.
* Todo documento XML debe tener un elemento raíz que no puede duplicarse, y que es el primero que se abre y el último que se cierra. En nuestro ejemplo es discografía_tool.
* Los atributos siempre deben ir entrecomillados.
* Para los atributos que sean booleanos1, su valor debe explicitarse de manera redundante.
* Los espacios en blanco se preservan.
* Los comentarios se marcan como en HTML (<!-- comentario -->).
* Los nombres de los elementos pueden contener letras, números y tres signos de puntuación: guión (-), guión bajo (_) y punto (.).
* Los nombres de los elementos no pueden empezar por un número o un signo de puntuación (excepto el guión bajo).
* Los nombres de los elementos no pueden empezar por las letras «xml» (ni cualquier combinación de caso, como XML, Xml,etc.).
* Los nombres de los elementos no pueden contener espacios.

XML bien formado y XML válido
#############################

Un documento XML puede estar bien formado y puede que además sea válido.
Un documento XML está bien formado si se aplican las reglas definidas anteriormente. En caso de que no sea así, el analizador sintáctico de turno generará un mensaje de error y detendrá el análisis del documento, como puede comprobarse con este ejemplo en un simple navegador.
Un documento XML es además válido si se ajusta a las limitaciones que le imponga una DTD, o un esquema:

* Una DTD es un documento escrito en un lenguaje creado a partir de SGML, gracias al cual se pueden especificar nombres de elementos concretos —por ejemplo, los elementos de XHTML—, y asignarles los atributos que aceptan y los valores legales para estos, los elementos que se pueden anidar en ellos y con qué frecuencia pueden o deben aparecer, y, en definitiva, todas las restricciones que convierten XML en una aplicación XML, término con el que se designa a un subconjunto de este lenguaje delimitado a una serie de elementos y dirigido a marcar un tipo de datos concreto1. En nuestro caso, XHTML sería la aplicación XML dirigida a marcar contenidos para la web.

* Un esquema es un documento creado en un lenguaje que sí está basado en XML, y cuya finalidad es la misma que la de una DTD: especificar restricciones para un documento XML. El W3C ha creado un documento explicativo sobre esquemas (inglés), y ha desarrollado una recomendación sobre sus estructuras (inglés), otra sobre los tipos de datos (inglés), y un boceto sobre sus componentes (inglés).
Como veremos más adelante al tratar los conceptos básicos de XHTML, lo que más nos incumbe como desarrolladores se sitios web es la primera, que se ajusta mejor a lo que es un documento narrativo2, como lo son los creados en XHTML.
Así, al comienzo de un documento XML se debe incluir la declaración XML, que tiene este aspecto::

    <?xml version="1.0" encoding="utf-8" standalone="no"?>
            
Por partes, lo que se especifica es lo siguiente:

* **version**: Indica la versión de XML que se está empleando. En el momento en que escribo esto, sólo hay dos: 1.0 y 1.1. Las diferencias no son muy relevantes para nosotros.
* **encoding**: Especifica el juego de caracteres con el que se ha codificado el documento. Por defecto es UTF-8, así que, a menos que se especifique algún otro como ISO-8859-1, es opcional.
* **standalone**: Especifica si la validez del documento depende de otro documento externo -bien una DTD, bien un esquema-, en cuyo caso el valor es no, o si depende de una DTD incluida en el mismo documento, en cuyo caso se especifica yes. Este atributo no tiene valor por defecto, por lo que si no se especifica, el documento XML no puede validarse.