# examen-base-de-datos

![Captura Tabla](/image/a.png)


NORMALIZACION

**(1FN)**

Todos los atributos deben ser atómicos y no deben existir grupos repetitivos.
Al revisar la tabla se observa que un cliente puede realizar varias compras y que 
un mismo libro puede aparecer en diferentes ventas. Por eso se debe organizar mejor la 
información para evitar repetir datos.

En esta etapa se utiliza un identificador de venta para diferenciar cada compra realizada.

**VENTAS**

|ISBN|Título|Autor|Fecha Publicación|Editorial|Categoría|Precio|Stock|Cliente|Correo|Dirección|Teléfono|Método Pago|Monto|

Justificación

Cumple 1FN porque:

Cumple con la Primera Forma Normal porque cada campo contiene un solo dato y no existen valores repetidos dentro de una misma celda.


**(2FN)**

Se eliminan las dependencias


Los datos del libro dependen solamente del ISBN

**(ISBN)**
Título
Autor
Fecha Publicación
Editorial
Categoría
Precio
Stock

Los datos del cliente dependen solamente del cliente.

**(Cliente)**
Correo
Dirección
Teléfono

**(Ventas)**
ISBN + Cliente 
MétodoPago
Monto

Justificación
Los datos del libro dependen únicamente de ISBN.
Los datos del cliente dependen únicamente de IdCliente.
La información de la compra permanece en VENTAS.


**(3FN)**
En la Tercera Forma Normal se separan los datos que se repiten en diferentes registros para evitar información duplicada.

**AUTORES**
--------
IdAutor (PK)
NombreAutor
Se crea una tabla de autores porque un autor puede tener varios libros y así evitamos repetir su nombre.

**EDITORIALES**
-----------
IdEditorial (PK)
NombreEditorial
Se separa la editorial porque una misma editorial puede publicar varios libros.

**CATEGORIAS**
----------
IdCategoria (PK)
NombreCategoria
Se crea una tabla de categorías para guardar cada categoría una sola vez.

**LIBROS**
-------
ISBN (PK)
Titulo
FechaPublicacion
Precio
Stock
IdAutor (FK)
IdEditorial (FK)
IdCategoria (FK)

**CLIENTES**
---------
IdCliente (PK)
CorreoCliente
DireccionCliente
TelefonoCliente

**VENTAS**
-------
IdVenta (PK)
ISBN (FK)
IdCliente (FK)
MetodoPago
Monto



**Parte 2: Diagrama Conceptual de Entidad-Relación**
![Captura Tabla](/image/B.png)

En este diagrama se organizó toda la información de la tienda de libros para mostrar cómo se relacionan los datos entre sí. En lugar de tener toda la información en una sola tabla, se dividió en varias entidades, haciendo que la base de datos sea más ordenada y fácil de administrar.

¿Qué representa cada figura?
Rectángulos: representan las entidades, Por ejemplo: Libro, Autor, Cliente, Pedido, etc.
Óvalos: representan los atributos, que son los datos que guarda cada entidad.
Rombos: representan las relaciones entre las entidades. Indican cómo interactúan entre si.

El objetivo fue organizar correctamente la información de la tienda de libros, evitando datos repetidos y mostrando claramente cómo se relacionan todas las tablas. Esto facilita la creación de la base de datos y permite que el sistema funcione de forma más eficiente al registrar libros, clientes, pedidos y pagos.


**Parte 3: Diagrama UML E-R**

**Claves Primarias (PK)**
Autor → id_autor
Libro → ISBN
Editorial → id_editorial
Categoría → id_categoria
Cliente → id_cliente
Pedido → id_pedido
Detalle_Pedido → id_detalle
Pago → id_pago


**Claves Foráneas (FK)**
Libro.id_autor → Autor.id_autor
Libro.id_editorial → Editorial.id_editorial
Libro.id_categoria → Categoria.id_categoria
Pedido.id_cliente → Cliente.id_cliente
Detalle_Pedido.id_pedido → Pedido.id_pedido
Detalle_Pedido.ISBN → Libro.ISBN
Pago.id_pedido → Pedido.id_pedido

