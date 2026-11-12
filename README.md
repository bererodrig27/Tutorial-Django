# Tutorial de Django 6.0 — App de encuestas (polls)

Proyecto completo del tutorial oficial: https://docs.djangoproject.com/en/6.0/intro/tutorial01/

Incluye el resultado final de las partes 1 a 7 y las instrucciones de la parte 8.

## Requisitos

- Python 3.12 o superior (Django 6.0 no corre en versiones anteriores)
- pip

## Puesta en marcha

```bash
# 1. Entorno virtual
python -m venv .venv

# Windows (PowerShell):  .venv\Scripts\Activate.ps1
# Windows (cmd):         .venv\Scripts\activate.bat
# Linux / macOS:         source .venv/bin/activate

# 2. Instalar Django
pip install -r requirements.txt

# 3. Crear las migraciones y la base de datos (parte 2)
python manage.py makemigrations polls
python manage.py migrate

# 4. Crear un superusuario para el admin (parte 2)
python manage.py createsuperuser

# 5. Levantar el servidor (parte 1)
python manage.py runserver
```

Abrí:

- http://127.0.0.1:8000/polls/ — la app
- http://127.0.0.1:8000/admin/ — el panel de administración (cargá ahí tus preguntas y opciones)

> Las preguntas con fecha de publicación futura no se muestran en `/polls/`.

## Tests (parte 5)

```bash
python manage.py test polls
```

## Estructura y relación con el tutorial

| Parte | Tema | Archivos |
|------|------|----------|
| 1 | Proyecto, vistas y URLs | `manage.py`, `mysite/urls.py`, `polls/urls.py`, `polls/views.py` |
| 2 | Modelos y admin | `polls/models.py`, `polls/admin.py`, `mysite/settings.py` |
| 3 | Vistas y templates | `polls/templates/polls/*.html` |
| 4 | Formularios y vistas genéricas | `polls/views.py` (`IndexView`, `DetailView`, `ResultsView`, `vote`) |
| 5 | Tests automatizados | `polls/tests.py` |
| 6 | Archivos estáticos | `polls/static/polls/style.css` |
| 7 | Personalizar el admin | `polls/admin.py`, `templates/admin/base_site.html` |
| 8 | Paquetes de terceros | ver abajo |

## Parte 8 (opcional): django-debug-toolbar

```bash
pip install django-debug-toolbar
```

Seguí la guía de instalación oficial (https://django-debug-toolbar.readthedocs.io/en/latest/installation.html): agregar `"debug_toolbar"` a `INSTALLED_APPS`, el middleware `debug_toolbar.middleware.DebugToolbarMiddleware`, `INTERNAL_IPS = ["127.0.0.1"]` y la URL `path("__debug__/", include("debug_toolbar.urls"))` en `mysite/urls.py`.

## Notas

- Las migraciones no vienen incluidas a propósito: se generan con `makemigrations` como en el tutorial.
- La imagen de fondo de la parte 6 (`background.png`) no está incluida; la línea de CSS está comentada en `style.css`.
- `SECRET_KEY` y `DEBUG = True` son solo para desarrollo.
- Idioma y zona horaria están en `es-ar` / `America/Argentina/Buenos_Aires` en `settings.py`.

## Subir a GitHub

```bash
git init
git add .
git commit -m "Tutorial Django 6.0: app polls"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
git push -u origin main
```
