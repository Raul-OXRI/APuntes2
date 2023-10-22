# Biblioteca

``` models.py biblioteca
class Biblioteca(models.Model):

    id = models.AutoField(primary_key=True)

    Nombre = models.CharField(max_length=50)

    Ubicacion = models.CharField(max_length=50)

    Region = models.CharField(max_length=50)

    Encargado = models.CharField(max_length=50)

    Horario = models.CharField(max_length=50)

    Numero_libros = models.IntegerField(default=200 )

    Created = models.DateTimeField(auto_now_add=True)

    Updated = models.DateTimeField(auto_now_add=True)

    class Meta:

        verbose_name='servicio'

        verbose_name_plural='servicios'

  

    def __str__(self):

        return self.Nombre
```

```admind.py
from .models import Biblioteca

# Register your models here.

  

#hacemos la accion de crear y subir al admin

class BiblioteccaAdmin(admin.ModelAdmin):

    readonly_fields=('Created' , 'Updated')

  

#registramos la base de datos al admin de django

admin.site.register(Biblioteca, BiblioteccaAdmin)
```

```settings.py
DATABASES = {

    'default': {

        'ENGINE': 'mssql',

        'NAME': 'umg_biblioteca',

        'USER': 'sa',

        'PASSWORD': 'clavedeacceso321$',

        'HOST': 'localhost',

        'PORT': '',

        'OPCIONS':{

            'driver': 'OBDC Driver 13 for SQL Server',

        },

    }

}
```
# Base_datos

```settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

---

# Nueva correcion de codigo

```python
from django.db import models

# Entidad Biblioteca
class Biblioteca(models.Model):
    id_biblioteca = models.AutoField(primary_key=True)
    nombre = models.CharField(max_length=100)
    ubicacion = models.CharField(max_length=100)
    horario = models.CharField(max_length=100)
    region = models.ForeignKey('Region', on_delete=models.CASCADE)
    encargado = models.OneToOneField('Encargado', on_delete=models.CASCADE)

# Entidad Encargado
class Encargado(models.Model):
    id_encargado = models.AutoField(primary_key=True)
    nombre = models.CharField(max_length=100)
    apellido = models.CharField(max_length=100)
    correo_electronico = models.EmailField()
    contrasena = models.CharField(max_length=100)

# Entidad Region
class Region(models.Model):
	id_region = models.AutoField(primary_key=True) 
	nombre = models.CharField(max_length=100)
```

