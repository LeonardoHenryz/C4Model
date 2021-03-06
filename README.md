# C4 Model

## Modelo C4 para Visual Studio Code

El modelo C4 es una forma sencilla de comunicar la arquitectura del software en diferentes niveles de abstracción, de modo que se pueden contar diferentes historias a diferentes audiencias. También es una manera de introducir (a menudo reintroducir) algo de rigor y modelado ligero para los equipos de desarrollo de software. [Enlace: C4 Model](https://c4model.com "")

> Una recomendacion de los desarrolladores del modelo C4 es no utilizar herramientas genericas para generar diagramas, ya que al ser muy genericas dificultan la estandarizacion. Un aspecto que facilita la estandarizacion, es que los diagramas son generados ? automaticamente a partir de instrucciones de codigo. Los usuarios no crean los diagramas graficamente, los usuarios definen sus modelos utilizando codigo el cual es interpretado para generar los diagramas automaticamente, esto ayuda a que los usuarios se enfoquen en definir los modelos y no en la creacion de diagramas.

## Plant UML
**Plant UML** es un software que permite crear una gran variedad de diagramas. Por si solo este software no permite crear diagramas del modelo C4, pero puede generar diagramas automaticamente, y al ser de codigo abierto es posible utilizar librerias adicionales para extender sus capacidades y crear otros tipos de diagramas con distintos formatos. En VisualStudioCode se puede encontrar una extension de PlantUML desarrollada por "jebbs". [Enlace: PlantUML](https://plantuml.com/ "")

**C4-PlantUML** es una libreria que trabaja con la extension de PlantUML que permite crear los diagramas utilizados comunmente en el modelo C4. Estas dos herramientas, tanto la libreria C4-PlantUML como la extension PlantUML nos pueden ayudar a generar documentacion de proyectos de forma estandarizada, dado que ambas trabajan dentro del entorno de VisualStudioCode, ademas es facil diferenciar una de la otra porque usan diferentes estilos visuales.

**Prerrequisitos**
>- VisualStudioCode
>- Extension de PlantUML
>- Java
>- GraphViz

**Instalacion de GraphViz**
Ir a la siguiente pagina de [Enlace: GraphViz](https://graphviz.gitlab.io/ "")

> Ir a la seccion "Download", ir al instalador de windows que empieza con la palabra "Stable" (en la seccion de Windows), descargar el archivo instalador con extension "msi", instalar GraphViz. Una vez instalado, hay que configurar la variable de entorno desde el panel de control de windows o escribiendo en el buscador de windows la palabra "environment" o "ambiente". La variable de entorno debe llevar por nombre "GRAPHVIZ_DOT" y debe apuntar al archivo "dot.exe" que se encuentra en la carpeta "bin" que a su vez se ubica dentro del directorio de instalacion de GraphViz. Las variables de entorno se pueden administrar en la pestaña "Advanced" dando click en el boton "Environment Variables".
    
**Instalacion de C4-PlantUML**    
    
La libreria C4-PlantUML se debe incluir en cada proyecto, los archivos de la libreria se encuentran en la siguiente pagina [Enalce: C4-PlantUML](https://github.com/RicardoNiepel/C4-PlantUML "")
            
Para poder crear cualquier tipo de diagrama C4 hay que incluir los cuatro archivos con extension "puml" en forma de cascada, empezando por el archivo "C4_Component.puml", es recomendable crear un directorio llamado C4lib para estos archivos. En el archivo C4lib.zip se encuentran los archivos ya configurados, solo hay que incluir el archivo "C4_Component.puml" escribiendo la instruccion: "!include C4lib/C4_Component.puml".

## Creación de diagramas con C4-PlantUML
Los diagramas de **PlantUML**, independientemente de que sean o no del modelo **C4**, empiezan con **@startuml** (seguido puede ir el nombre del diagrama: **@staruml "nombre del diagrama"**) y terminan con **@enduml**. 
También se puede establecer el titulo del diagrama con: **title titulo del diagrama**.

Para poder hacer diagramas del modelo **C4** es necesario importar la librería necesaria con **!import directorio/C4_Context.puml**. 
Si el diagrama es de contenedores o componentes se puede reemplazar **Context** por **Container** o **Component** respectivamente.

Los elementos que se pueden crear en un diagrama son:
**Person**: Un usuario, puede ser externo (**Person_Ext**).
**System**: Un sistema, puede ser externo (**System_Ext**).
**Container**: Un contenedor de un sistema, puede ser una base de datos (**ContainerDb**).
**Component**: Un componente de un contenedor.

La sintaxis para cualquier elemento es **System(nombre, "titulo", "tecnologias", "descripcion")**.

Los sistemas, contenedores y componentes se pueden agrupar con **Enterprise_Boundary**, **System_Boundary** y **Container_Boundary** respectivamente. La sintaxis para cualquier agrupamiento es **System_Boundary(nombre, "titulo") {...elementos pertenecientes al agrupamiento...}**.

Para relacionar los elementos entre si se escribe **Rel(elementoA, elementoB, "tipo de relación", "tecnologias")**. Se puede relacionar en reversa con **Rel_Back**, a un vecino con **Rel_Neighbor** y a un vecino en reversa con **Rel_Back_Neighbor**. También se puede establecer la posición relativa del primer elemento con respecto al segundo elemento con **Rel_D** (arriba de), **Rel_U** (abajo de), **Rel_R** (a la izquierda) y **Rel_L** (a la derecha).

En caso de que haya que cambiar la posición de algunos elementos se puede hacer directamente con **Lay_D**, **Lay_U**, **Lay_R** y **Lay_L**. Estas instrucciones son similares a las que empiezan con **Rel** pero solo modifican la posición de los elementos, y se usan de la siguiente manera: **Lay_R(elementoA, elementoB)**.

## C4Builder
Informacion para instalar C4Builder
```
$ npm install c4builder
```
[Enlace: C4Builder](https://github.com/adrianvlupu/C4-Builder "")

