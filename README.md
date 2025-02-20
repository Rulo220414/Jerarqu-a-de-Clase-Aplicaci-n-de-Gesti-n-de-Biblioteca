class MaterialBiblioteca:
    def __init__(self, titulo, autor):
        self.titulo = titulo
        self.autor = autor

    def descripcion(self):
        return f'{self.titulo} por {self.autor}'
    
class Libro(MaterialBiblioteca):
    def __init__(self, titulo, autor, isbn):
        super().__init__(titulo, autor)
        self.isbn = isbn

    def descripcion(self):
        return f'Libro: {self.titulo}, Autor: {self.autor}, ISBN: {self.isbn}'
    
class Revista(MaterialBiblioteca):
    def __init__(self, titulo, autor, edicion):
        super().__init__(titulo, autor)
        self.edicion = edicion

    def descripcion(self):
        return f'Revista: {self.titulo}, Autor: {self.autor}, Edición: {self.edicion}'
    
class MiembroBiblioteca:
    def __init__(self, nombre):
        self.nombre = nombre

    def solicitar_material(self, material):
        raise NotImplementedError("Este método debe ser redefinido en las subclases.")

    def devolver_material(self, material):
        return f'{self.nombre} ha devuelto {material.titulo}'

class Alumno(MiembroBiblioteca):
    def solicitar_material(self, material):
        return f'El alumno {self.nombre} ha solicitado {material.titulo}'

class Docente(MiembroBiblioteca):
    def solicitar_material(self, material):
        return f'El docente {self.nombre} ha solicitado {material.titulo} con prioridad.'
    
# Creación de instancias
libro1 = Libro("Cien Años de Soledad", "Gabriel García Márquez", "1122334455")
revista1 = Revista("Science Today", "Editorial Científica", 12)

alumno = Alumno("Carlos")
docente = Docente("María")

# Mostrar información
print(libro1.descripcion())
print(revista1.descripcion())

# Solicitudes
print(alumno.solicitar_material(libro1))
print(docente.solicitar_material(revista1))
