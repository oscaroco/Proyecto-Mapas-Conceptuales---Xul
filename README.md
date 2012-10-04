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




