# reto_2
Elija un problema de la vida real (sistema de gestión de biblioteca, negocio de compra-venta, automóvil, etc) que se pueda modelar a través de objetos y clases. Plantee las relaciones de clases, composiciones, propiedades y comportamientos del sistema en uno mas diagramas tipo UML.

## Ejemplo
El caso elegido fue el de una biblioteca, en este se pueden ver las diferentes subclases de biblioteca como: los recursos, las personas y contempla otro que seria prestamo interno.

```` mermaid
classDiagram
    class Biblioteca {
        +str nombre
        +str direccion
        +agregarLibro(): void
        +registrarUsuario(): void
        +agregarRecurso(): void
        +gestionarPrestamoInterno(): void
    }

    class PersonaRegistrada {
        +str nombre
        +int id
        +prestarRecurso(): void
        +devolverRecurso(): void
        +solicitarPrestamoInterno(): void
    }

    class RecursoBiblioteca {
        +str titulo
        +str autor
        +str genero
        +str seccion
        +prestar(): void
        +devolver(): void
    }

    class PrestamoInterno {
        +str computadora
        +str juego_de_mesa
        +prestar(duracion: int): void
        +devolver(): void
    }

    class Libro
    class AudioLibro

    Biblioteca *-- RecursoBiblioteca : contiene
    Biblioteca *-- PersonaRegistrada : contiene
    Biblioteca --> PrestamoInterno : gestiona
    RecursoBiblioteca <|-- Libro
    RecursoBiblioteca <|-- AudioLibro
    PersonaRegistrada --> PrestamoInterno : realiza

````
### Relacion entre Bilioteca y Recurso
La relacion entre biblioteca y recurso es de composicion ya que una biblioteca esta compuesta de diferentes recursos, ademas, recurso tiene 2 pequeñas subclases llamadas libro y audiolibro las cuales heredan sus diferentes atributos y metodos.

```` mermaid
classDiagram
    class Biblioteca {
        +str nombre
        +str direccion
        +agregarLibro(): void
        +registrarUsuario(): void
        +agregarRecurso(): void
        +gestionarPrestamoInterno(): void
    }
    class RecursoBiblioteca {
        +str titulo
        +str autor
        +str genero
        +str seccion
        +prestar(): void
        +devolver(): void
    }
    class Libro
    class AudioLibro

    Biblioteca *-- RecursoBiblioteca : contiene
    RecursoBiblioteca <|-- Libro
    RecursoBiblioteca <|-- AudioLibro
````
### Relacion entre Biblioteca y PersonaRegistrada
La relacion entre estas dos es de composición ya que la biblioteca esta conformada por personas registradas o usuarios, cabe mencionar que esta clase tiene diferentes metodos como prestar, devolver y solicitar prestamo interno.

```` mermaid
classDiagram
    class Biblioteca {
        +str nombre
        +str direccion
        +agregarLibro(): void
        +registrarUsuario(): void
        +agregarRecurso(): void
        +gestionarPrestamoInterno(): void
    }
    class PersonaRegistrada {
        +str nombre
        +int id
        +prestarRecurso(): void
        +devolverRecurso(): void
        +solicitarPrestamoInterno(): void
    }

    Biblioteca *-- PersonaRegistrada : contiene
````
### Relacion entre Biblioteca y PrestamoInterno
La relacion entre estas dos es que biblioteca se encarga de gestionar la clase PrestamoInterno la cual a su vez interactua con la clase PersonaRegistrada

```` mermaid
classDiagram
    class Biblioteca {
        +str nombre
        +str direccion
        +agregarLibro(): void
        +registrarUsuario(): void
        +agregarRecurso(): void
        +gestionarPrestamoInterno(): void
    }

    class PersonaRegistrada {
        +str nombre
        +int id
        +prestarRecurso(): void
        +devolverRecurso(): void
        +solicitarPrestamoInterno(): void
    }

    class PrestamoInterno {
        +str computadora
        +str juego_de_mesa
        +prestar(duracion: int): void
        +devolver(): void
    }

    Biblioteca *-- PersonaRegistrada : contiene
    Biblioteca --> PrestamoInterno : gestiona
    PersonaRegistrada --> PrestamoInterno : realiza

````
