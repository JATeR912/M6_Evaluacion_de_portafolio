# TravelPoint 🌏

TravelPoint es una aplicación web desarrollada en Django que permite explorar y gestionar información sobre festivales y lugares turísticos en Japón.  
La plataforma combina contenido dinámico, autenticación de usuarios, favoritos y administración de datos, siendo escalable para cubrir otros países o tipos de destinos turísticos en el futuro.

Usuarios y administradores interactúan con la aplicación según sus permisos, y los administradores gestionan lugares turísticos mediante un CRUD completo.

---

## 🌟 Características Principales

- Exploración de lugares turísticos con información básica y detalles completos para usuarios registrados.
- CRUD de lugares turísticos para administradores con control de permisos.
- Registro, login y logout de usuarios.
- Mensajes de feedback sobre acciones del usuario (éxito, error, advertencia).
- Control de acceso con páginas 403 y 404 personalizadas.
- Interfaz administrativa con Django Admin.
- Plantillas responsivas con Bootstrap 5.

---

## 📁 Estructura del Proyecto

```bash
.
├─ manage.py
├─ travelpoint/        # Configuración del proyecto
├─ turismo/            # App principal
│  ├─ models.py
│  ├─ views.py
│  ├─ forms.py
│  ├─ urls.py
│  ├─ admin.py
│  ├─ templates/turismo/
│  └─ static/turismo/
├─ templates/          # Templates globales
├─ static/             # Archivos estáticos globales
└─ media/              # Imágenes subidas
```

## Tecnologías Utilizadas
- **Python 3.x** – Lenguaje principal de programación.
- **Django 5.x** – Framework web para desarrollo rápido, seguro y escalable.
- **HTML5 / CSS3 / Bootstrap 5** – Para la creación de interfaces web responsivas y modernas.
- **JavaScript** – Para funcionalidades dinámicas en el frontend.
- **Pillow** – Para manejo de imágenes en la aplicación.
- **Whitenoise** – Para servir archivos estáticos de manera eficiente.
- **Gunicorn** – Servidor WSGI para despliegue en producción.
- **PyMySQL** – Para conexión con bases de datos MySQL si se requiere.

## 🔹 Por qué Django

Django es un framework web basado en Python para aplicaciones rápidas, seguras y escalables. Sus principales ventajas son:

- **Arquitectura MTV (Model-Template-View)**: separa la lógica de negocio, la presentación y la gestión de datos.
- **ORM integrado**: permite interactuar con la base de datos sin escribir SQL manualmente.
- **Autenticación y autorización**: manejo de usuarios, permisos y grupos de forma nativa.
- **Django Admin**: interfaz administrativa automática para gestionar datos.
- **Seguridad incorporada**: protecciones contra CSRF, XSS, SQL Injection y Clickjacking.
- **Desarrollo rápido**: incluye servidor de desarrollo, rutas, plantillas, formularios y validaciones listas para usar.

---

## 🔄 Comparación con Otros Frameworks

| Aspecto          | Django       | Flask        | Ruby on Rails |
|-----------------|-------------|-------------|---------------|
| Enfoque          | Completo     | Micro       | Completo      |
| ORM              | Integrado    | No incluido | Integrado     |
| Admin automático | Sí ✔         | No ❌       | Parcial       |
| Seguridad        | Integrada    | Depende dev | Integrada     |
| Ideal para       | Apps CRUD, auth, dashboards | APIs pequeñas | Apps web completas |

**Conclusión:** Django es ideal para aplicaciones empresariales como TravelPoint, por su seguridad, escalabilidad y rapidez.

---

## 🧱 Modelos y Formularios

### Modelo principal: `LugarTuristico`

```python
class LugarTuristico(models.Model):
    nombre = models.CharField(max_length=200)
    descripcion = models.TextField()
    imagen = models.ImageField(upload_to='lugares/')
    fecha_evento = models.DateField()
```

#### Formularios
Formulario de registro de usuario:

```python

from django import forms
from django.contrib.auth.forms import UserCreationForm
from .models import LugarTuristico

class RegistroForm(UserCreationForm):
    email = forms.EmailField(required=True)
```

Formulario para CRUD de lugares turísticos:

```python

class LugarForm(forms.ModelForm):
    class Meta:
        model = LugarTuristico
        fields = ['nombre', 'descripcion', 'imagen', 'fecha_evento']
```

## 🔐 Autenticación y Permisos
Registro, login y logout implementados con Django Auth.

Solo administradores (staff) pueden crear, editar o eliminar lugares.

Usuarios autenticados ven detalles completos.

Decoradores y redirecciones manejan accesos no autorizados (403).

## 🚀 Cómo Ejecutar el Proyecto

### Crear entorno virtual
```bash
python -m venv myenv
```

### Activar entorno virtual (Windows)
```bash
myenv\Scripts\activate
```

### Activar entorno virtual (Linux/Mac)
```bash
source env/bin/activate
```

### Instalar dependencias
```bash
pip install -r requirements.txt
```

### Aplicar migraciones
```bash
python manage.py makemigrations
python manage.py migrate
```

### Crear superusuario
```bash
python manage.py createsuperuser
```

### Ejecutar servidor de desarrollo
```bash
python manage.py runserver
```
## 📝 Licencia MIT