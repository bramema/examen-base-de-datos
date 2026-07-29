# examen-base-de-datos

![Captura Tabla](/image/a.png)


NORMALIZACION

**(1FN)**

Todos los atributos deben ser atómicos y no deben existir grupos repetitivos.
Se identifica que un cliente puede comprar varios libros y un libro puede venderse muchas veces.

La clave candidata podría ser:

(ISBN, Cliente)

aunque realmente haría falta un identificador de pedido.

La tabla queda igual:

**VENTAS**

|ISBN|Título|Autor|Fecha Publicación|Editorial|Categoría|Precio|Stock|Cliente|Correo|Dirección|Teléfono|Método Pago|Monto|

Justificación

Cumple 1FN porque:

No existen listas dentro de una celda.
Todos los campos contienen un solo valor.


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
Se eliminan las dependencias transitivas separando las entidades que se repiten.

**AUTORES**
--------
IdAutor (PK)
NombreAutor

**EDITORIALES**
-----------
IdEditorial (PK)
NombreEditorial

**CATEGORIAS**
----------
IdCategoria (PK)
NombreCategoria

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