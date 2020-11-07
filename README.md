# Proyecto tutorial en Django

[Link al curso](https://learning.oreilly.com/videos/introduction-to-django/9781771375375/)

## Ejecución local:

Ejecuta localmente el proyecto y lo levanta en <localhost:8000>

`python manage.py runserver`

## Modelos

### Many to Many

```python
authors = models.ManyToManyField("Author", related_name="books")
```
`Author` es el nombre de la clase relacionada y `books` es el nombre del nuevo campo de relación en la otra tabla

## Crear migraciones

Las migraciones crean los pasos necesarios para crear la base de datos. Esto permite realizar wipes en bases de datos y recontruir las tablas. Tambien permite volver a migraciones antiguas y deshacer cambios.

`python manage.py makemigrations`
`python manage.py migrate`

## Cambiar nomble del campo a una tabla:

Simplemente cambiar el nombre en el model correspondiente y correr `makemigrations` y `migrate`
Asegurarse de cambiar los titulos a los métodos custom que se hayan creado

## Django Admin

Django admin es una GUI que permite realizar cambios en nuestra aplicacions como:
 * Crear entradas en las tablas de la BD

### Crear primer super usuario

`python manage.py createsuperuser`

### Registrar modelos para editarlos en /admin

En admin.py de la aplicación importar y registrar nuestro modelo

```python
from .models import Book
admin.site.register(Book)
```

## Django built-in shell

`python manage.py shell`

### Importar un modelo y crear una entrada

`from books.models import Book` Importa el modelo
`secondbook = Book(tittle="Second Book", author="Alan Moreno", review="Awesome!")` Creamos una entrada
`secondbook.save()` Guardamos la entrada
`Book.objects.all()` Consultamos las entradas de la tabla

### Queries

`Book.objects.filter(tittle__contains="Bo").filter(author__startswith="Al")` Filtra los titulos que contienen "Bo" y luego ese resultado lo filtra con los autores que comienzan con "Al"