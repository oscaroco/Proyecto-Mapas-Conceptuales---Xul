Proyecto-Mapas-Conceptuales---Xul
=================================
##Introducción##

Los mapas conceptuales son útiles en la representación y compresión de materia sobre algún tema o temas en específico, muchas veces usados por estudiantes o trabajadores para resumir información útil, la cual acomodada de cierta manera es representativa visualmente y puede ser comprendida y recordada de mejor manera.
El presente proyecto pertenece al curso de interfaces graficas de usuario, se busca conocer maneras de representar y desplegar diversos tipos de información (mapas conceptuales, gráficos, diagramas) mediante la herramienta xulRunner. Además, se pretende implementar librerías javascript mediante código coffeescript unido con xul y asi, contar con nuevas maneras de mostrar imágenes y datos en páginas web.
La herramienta xulRunner consiste en un entorno de tiempo de ejecución creado por la Fundación Mozilla para ofrecer un back-end común para las aplicaciones creadas mediante xul, aunque todavía se encuentra en etapa de desarrollo. 

##Descripcion del contenido a desplegar##

###Librería Joint.js###

JointJS es una librería de JavaScript utilizada para la creación de diagramas o mapas conceptuales, estos diagramas pueden ser creados completamente interactivos. Esta librería permite la implementación de herramientas de edición de mapas conceptuales o simplemente la visualización d estos.
Las principales características con las que cuenta la librería son:

* Conexión de objetos con varios tipos de líneas.
* Interacciones con conexiones y objetos.
* Controladores personalizados para diversos eventos.
* Líneas curvadas suavizadas.
* Elementos listos para usar de diagramas ya conocidos (ERD, FSA, UML, LDM).
* Diagramas jerárquicos.
* Serializacion.
* Extensible.
* Personalizable.

Dicha librería es soportada por los siguientes navegadores Firefox 3.0+, Safari 3.0+, Opera 9.5+, Google Chrome 4+ e Internet Explorer 6.0+.
JointJS hace uso de RaphaelJS, pequeña librería JavaScript que permite la simplificación de trabajo con vectores gráficos en el campo web.  Esta librería utiliza recomendaciones SVG W3C y VML como base en la creación de gráficos. Debido a esto, cada objeto grafico creado es también catalogado como un objeto DOM, de esta manera se pueden agregar eventos manejables    JavaScript o modificarlos luego. Esta librería también es compatible con los navegadores antes especificados.
Como se mencionó anteriormente, la librería JointJS puede ser utilizada para la creación de diversos diagramas relacionados con diferentes ámbitos que necesitan resumir o interpretar información. A continuación se presentan ejemplos de diagramas que pueden ser creados mediante la utilización de la librería:

####Ejemplos####

    http://www.ic-itcr.ac.cr/~osrodriguez/Interfaces/imagen1.jpg


Así, el diagrama anterior puede ser diseñado mediante figuras y líneas creadas mediante el siguiente código:
title('Entity-relationship diagram.');
description('Make your database structure visible.');
dimension(800, 250);

Definición del espacio en el que se dibujara el diagrama:

    var erd = Joint.dia.erd;
    Joint.paper("world", 800, 250);

Creación del cuadrado que tiene la etiqueta “Entity”

    var e1 = erd.Entity.create({
    rect: { x: 220, y: 70, width: 100, height: 60 },
    label: "Entity"
    });
    
Creación del rombo que contiene la etiqueta “Relationship”

    var e2 = erd.Entity.create({
    rect: { x: 520, y: 70, width: 100, height: 60 },
    label: "Weak Entity",
    weak: true
    });
    
Union de ambas figuras

    e1.joint(r1, erd.toMany);


    http://www.ic-itcr.ac.cr/~osrodriguez/Interfaces/imagen2.jpg


El diagrama anterior ha sido creado utilizando el siguiente código:

    title('Finite State Machines');
    description('Give light to your components state transitions.');
    dimension(800, 400);

Define el tamaño de la ventana en la que se dibujara el diagrama:

    var fsa = Joint.dia.fsa;
    Joint.paper("world", 800, 400);

Creación del círculo con la etiqueta “state 1”
    
    var s1 = fsa.State.create({
    position: {x: 120, y: 70},
    label: "state 1"
    });

Creación del círculo inicial

    var s2 = fsa.State.create({
    position: {x: 250, y: 100},
    label: "state 2"
    });

Creación del círculo con la etiqueta “state 1”
    
    var s0 = fsa.StartState.create({
    position: {x: 20, y: 20}
    });

Definición del arreglo con todas las variables

    var all = [s0, s1, s2];

Unión de los círculos de estados mediante las flechas
    
    s0.joint(s1, fsa.arrow).register(all);
    s1.joint(s2, (fsa.arrow.label = "a", fsa.arrow)).register(all);
    fsa.arrow.label = null;  


###Mapas Conceptuales###

####Historia ####

El Doctor Novak es un experimentado Investigador Científico que completó sus estudios superiores en la Universidad de Minnesota en 1958. Enseñó en las Universidades Estatal de Kansas y Purgue y desarrolló los Mapas Conceptuales, como ahora se los conoce, siendo profesor de Educación y Ciencias Biológicas en la Universidad de Cornell, donde realizó investigaciones en educación, aprendizaje, creación y representación del conocimiento. (NOVAK, 2007)

####Concepto####
Los mapas conceptuales (también denominados organigramas) constituyen un eficaz medio para representar gráficamente ideas o conceptos que están relacionados jerárquicamente. El objetivo principal de un mapa conceptual es representar vínculos entre distintos conceptos que adquieren la forma de proposiciones. Mediante este procedimiento aprovecharemos el poder conceptual de las imágenes, facilitando el aprendizaje y el recuerdo de un tema. Desde luego no se trata de memorizar los mapas y reproducirlos en todos sus detalles, sino de utilizarlos para organizar el contenido de estudio. La técnica de elaboración de mapas conceptuales es un medio didáctico poderoso para organizar información, sintetizarla y presentarla. Puede servir para exponer y desarrollar oralmente un tema de manera lógica y ordenada.

####Elementos####

Los mapas conceptuales están compuestos de dos elementos principalmente, los cuales son:
  * Ideas o Conceptos: El mapa conceptual esta hecho de conceptos o ideas, suelen representarse estando encerradas en círculos, óvalos, rectángulos u otra figura geométrica. 
  * Conectores: La conexión o relación entre dos ideas se representa por medio de una línea inclinada, vertical u horizontal llamada conector o línea ramal que une ambas ideas, en muchas ocasiones los conectores van acompañados de palabras de enlace para ayudar  a comprender mejor la relación entre conceptos.

####Usos####

Los mapas conceptuales son muy usados para mostrar información con diferentes propósitos, algunos ejemplos son:
  * Organigramas Corporativos
  * Árboles Lógicos (Binarios, K-arios, etc.)
  * Árboles Genealógicos
  * Resúmenes de Información.




##Definición de estructuras de datos (formato) utilizadas##

Decidimos utilizar archivos xml para lo que son la definición de la estructura ya que el formato de tab que este presenta nos pareció indicado para mostrar la relaciones entre los nodos, para identificar que es un archivo de mapa conceptual la primera etiquita que vamos a utilizar es “<mapa>”, luego cada nivel del mapa conceptual tendrá un nodo numerado, el cual a su vez tendrá un atributo nombre el cual es el texto de ese elemento en el mapa, la línea que unen a los nodos se trazaran por niveles, por ejemplo se trazaran todas las líneas desde el “nodo 1” hacia todos los elementos que sean “nodo 2” que estén dentro la etiqueta de nodo 1, y se trazara otra línea de cada elemento “nodo 2” a cada elemento “nodo 3” que este dentro de él y así sucesivamente.
Para mostrar mejor la definición de esta estructura presentamos el siguiente ejemplo:


    :::xml
    <mapa>
      <nodo1 nombre="Escuela de Computación">
        <nodo2 nombre="Carreras">
           <nodo3 nombre="ATI"/>
           <nodo3 nombre="CE"/>
           <nodo3 nombre="IC"/>
        </nodo2>
        <nodo2 nombre="Personal">
           <nodo3 nombre="Profesores"/>
           <nodo3 nombre="Secretaria"/>
        </nodo2>
      </nodo1>
    </mapa>


    http://www.ic-itcr.ac.cr/~osrodriguez/Interfaces/imagen3.jpg

##Ejemplos de datos a utilizar como pruebas##

###Organigrama###
  
    <mapa>
      <nodo1 nombre="Gerente General">
        <nodo2 nombre="Gerente Ventas">
        <nodo3 nombre="Vendedores"/>
    	  <nodo3 nombre="Telefonistas"/>
    	</nodo2>
    	<nodo2 nombre="Gerente Recursos Humanos">
    	  <nodo3 nombre="Contratacion"/>
    	  <nodo3 nombre="Dimiciones"/>
    	  <nodo3 nombre="Relaciones"/>
    	</nodo2>
    	<nodo2 nombre="Gerente Contabilidad">
    	  <nodo3 nombre="Contador"/>
    	  <nodo3 nombre="Cobros"/>
    	  <nodo3 nombre="Pagos"/>
    	</nodo2>
      </nodo1>
    </mapa>


###Arbol Binario Ordenado###

    <mapa>
      <nodo1 nombre="20">
    	<nodo2 nombre="10">
    		<nodo3 nombre="5">
    			<nodo4 nombre="3"/>
    			<nodo4 nombre="8"/>
    		</nodo3>
    		<nodo3 nombre="15">
    			<nodo4 nombre="13"/>
    			<nodo4 nombre="18"/>
    		</nodo3>
    	</nodo2>
    	<nodo2 nombre="30">
    		<nodo3 nombre="25">
    			<nodo4 nombre="23"/>
    			<nodo4 nombre="28"/>
    		</nodo3>
    		<nodo3 nombre="35">
    			<nodo4 nombre="33"/>
    			<nodo4 nombre="38"/>
    		</nodo3>
    	</nodo2>
      </nodo1>
    </mapa>


###Escuela de Computacion###

    <mapa>
      <nodo1 nombre="Escuela de Computación">
        <nodo2 nombre="Carreras">
           <nodo3 nombre="ATI"/>
           <nodo3 nombre="CE"/>
           <nodo3 nombre="IC"/>
        </nodo2>
        <nodo2 nombre="Personal">
           <nodo3 nombre="Profesores"/>
           <nodo3 nombre="Secretaria"/>
        </nodo2>
      </nodo1>
    </mapa>


##Limitaciones observadas y posibles mejoras##

###Limitaciones###


Debido a problemas con la librería JointJs, no se logró implementar por completo dicha librería junto con coffeescript y xul para el despliegue y edición de mapas conceptuales. Esto debido a que algunas de las funciones de la librería Raphael.js específicamente fueron implementadas, sin embargo algunas otras de estas funciones presentaron errores en el momento de ejecución del código en xul.

###Posibles Mejoras###

Para futuras implementaciones se busca agregar la funcionalidad de permitir al usuario la posibilidad de especificar el tipo de figura que se desea utilizar en el mapa conceptual (rombos, cuadrados, rectángulos, triángulos), así como el color que tendrán cada  uno de estos.

###Apendice###

Para descargar el proyecto:
    http://www.ic-itcr.ac.cr/~osrodriguez/Interfaces/

##Bibliografia##

Definicion.de . (2008). Definicion.de . Recuperado el 29 de setiembre de 2012, de http://definicion.de/mapa-conceptual/

Clases Historia. (s.f.). Claseshistoria. Recuperado el 29 de setiembre de 2012, de http://www.claseshistoria.com/general/confeccionmapaconceptual.htm
Figurepool. (2012). Joint, JavaScript diagramming library. Recuperado el 01 de Octubre de 2012, de http://www.jointjs.com/

NOVAK, J. D. (18 de mayo de 2007). PSICOGOGOS. Recuperado el 29 de setiembre de 2012, de http://psicopiedragogogos.blogspot.com/2007/05/historia-de-los-mapas-conceptuales.html

Raphaeljs. (s.f.). Raphael-Javascript library. Recuperado el 29 de Setiembre de 2012, de http://raphaeljs.com/