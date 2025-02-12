Las definiciones contenidas en el catalogo MTX se encuntran en ingles.

En este prototipo se han adicionado attributos adicionales para poder acomodar la descripcion en otros lenguajes, manteniendo la descripción original en ingles.

![image](https://github.com/user-attachments/assets/84f8e9f6-0f71-489c-805a-395875b087c6)

Permite seguir buscando los terminos en ingles

![image](https://github.com/user-attachments/assets/080352b2-ea43-43b3-b7c2-d2c9d44607fb)

Como no es posible configurar el "catalogue browser" para seleccionar un idioma, el campo que principal de descripcion debe de ser actualizado manualemente.

El proceso es sencillo y puede ser realizado teniendo conocimientos basicos en Excel con simples Vlookup.

Pasos:
- Importar el caalogo opriginal, buscar la ultima version disponible en el sitio de EFSA.
- Exportar a Excel el catalogo, ie. MTX_16.0_ES.xlsx
- Crear un catalogo "local", ie. MTX_16.0_ES
- Importar el archivo exportado desde el original MTX_16.0
- Realizar la adaptaciones a los atributos, que permite la adicion e inclusive la modificacion de las etiquetas "Label"

![image](https://github.com/user-attachments/assets/65713fc6-6104-4cbd-91ac-b1dde6f95ae4)

**Adaptaciones adicionales**

**Scopenotes**

debe de tener cuidado si decide actualizar es campo, ya que en algunas partes del programa, existen condiciones especiales, como es el caso del attibuto "termType".

**Attributo - Term type: **
El atributo "termType", tiene una caracteristica que permite cambiar el texto desplegable en la pantalla.

![image](https://github.com/user-attachments/assets/2fa504f7-eb42-4574-8cd6-b6829a9f6b99)

´´
The type of the term, as derivative (state flag)$n=Fuentes Naturales$r=Productos Primarios Crudos (RPC)$d=RPC Derivados/ ingredientes$s=Alimentos compuestos simples$c=Alimentos compuestos agregados$g=Broad or mixed$f=Facets
´´

**Etiquetas**

Adicionalmente puede cambiar las etiquetas

Como las traducciones pueden tener diferentes interpretaciones en las diversas formas del mismo lenguaje, las traducciones podrian ser adaptadas, como el caso "Source" (Origen, Fuente)

![image](https://github.com/user-attachments/assets/f0832f55-f13e-4977-aec3-a6e1a2626088)

![image](https://github.com/user-attachments/assets/e145d75d-44c2-4443-a9e2-1ef00e3c74a7)

**Proceso Ajuste a Hoja de Excel**

- En la pestaña "term"
- Copie el contenido de la columna B "terExtendedName" a la columna donde se encuentra "terExtendedName_en" que es el texto original
- En la columna "terExtendedName_es", se aplica un VLookup a la hoja en donde se encuentran las traduccioon de los terminos, en este caso, solamente se realizo la traduccion de ciertos terminos (1,600) utilizanddo servicios AI.
- Ahora en la columna "terExtendedName" se ingresa una formula condicional para seleccionar la columna con la traduccion y si no existe, la columna original en ingles.

![image](https://github.com/user-attachments/assets/767c662d-5356-438e-8911-8a5173d3197d)
``
=SI(LARGO(AH2)=0,AG2,AH2)
``

![image](https://github.com/user-attachments/assets/b5678a1d-0503-4afe-b753-e827418a2355)

``
=SI.ERROR(BUSCARV(A7,[translated_Short_MTX_12.0_Sum.xlsx]Hoja1!A$2:B$1655,2,FALSO),"")
``

- Como el programa que importa las definiciones no puede transformar las "formulas", es necesario copiar y pegado especial VALORES, a las columnas correspondientes: "terExtendedName" y "terExtendedName_es"


