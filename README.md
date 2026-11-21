# Django Base

<div align="center">

![Django](https://img.shields.io/badge/Django-6.1.3-092E20?style=for-the-badge&logo=django&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![License](https://img.shields.io/badge/License-Pending-lightgrey?style=for-the-badge)

**Una base limpia y lista para comenzar proyectos con Django.**

</div>

---

## Acerca del proyecto

**Django Base** es un proyecto inicial construido con Django 6.1.3 y organizado siguiendo una estructura simple y escalable. Incluye una aplicación `pages` con una vista basada en clases y una plantilla HTML principal.

Actualmente ofrece una página de inicio accesible en la raíz del sitio y el panel administrativo de Django.

## Caracteristicas

- Proyecto Django configurado y listo para desarrollo.
- Aplicacion `pages` integrada desde el panel de configuracion.
- Vista basada en `TemplateView`.
- Plantillas centralizadas en el directorio `templates`.
- Base de datos SQLite incluida para desarrollo local.
- Panel administrativo disponible en `/admin/`.
- Configuracion preparada para `Debug`, `Internationalization` y zona horaria UTC.
- Entorno virtual localizado en `.venv`.

## Tecnologias

| Tecnologia | Uso |
|---|---|
| Django 6.1.3 | Framework web principal |
| Python | Lenguaje de programacion |
| SQLite | Base de datos de desarrollo |
| HTML | Plantilla de la pagina principal |
| ASGI / WSGI | Interfaces de despliegue |

## Estructura del proyecto

```text
Django2/
├── django_base/
│   ├── settings.py       # Configuracion global del proyecto
│   ├── urls.py           # Rutas principales
│   ├── asgi.py           # Entrada ASGI
│   └── wsgi.py           # Entrada WSGI
├── pages/
│   ├── migrations/       # Migraciones de la aplicacion
│   ├── admin.py          # Configuracion del administrador
│   ├── apps.py           # Configuracion de Pages
│   ├── models.py         # Modelos de datos
│   ├── tests.py          # Pruebas de la aplicacion
│   ├── urls.py           # Rutas de la aplicacion
│   └── views.py          # Vistas de la aplicacion
├── templates/
│   └── home.html         # Plantilla principal
├── .venv/                # Entorno virtual local
├── db.sqlite3            # Base de datos SQLite
├── manage.py             # Administracion de Django
├── requirements.txt      # Dependencias Python
└── README.md             # Documentacion del proyecto
```

## Requisitos

- Python 3.14 o compatible.
- `pip` para gestionar dependencias.
- Windows PowerShell, CMD o Git Bash.

> Las versiones fijadas en `requirements.txt` incluyen Django 6.1.3, ASGIRef 3.13.0, SQLParse 0.6.1 y TZData 2026.6.

## Instalacion

### 1. Clonar el repositorio

```powershell
git clone <URL_DEL_REPOSITORIO>
cd Django2
```

### 2. Crear y activar un entorno virtual

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

Si PowerShell bloquea la ejecucion del script, habilita temporalmente la ejecucion para la sesion actual:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

### 3. Instalar las dependencias

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Ejecutar el proyecto

### 1. Aplicar las migraciones

```powershell
python manage.py migrate
```

### 2. Iniciar el servidor de desarrollo

```powershell
python manage.py runserver
```

Abre el navegador en:

- Sitio principal: http://127.0.0.1:8000/
- Administracion: http://127.0.0.1:8000/admin/

## Rutas disponibles

| Ruta | Nombre | Descripcion |
|---|---|---|
| `/` | `home` | Renderiza `templates/home.html` |
| `/admin/` | Panel administrativo | Interfaz de gestion de Django |

La ruta principal se define en `pages/urls.py` y se incluye desde `django_base/urls.py`.

## Crear un superusuario

Para acceder al panel administrativo:

```powershell
python manage.py createsuperuser
```

Despues, inicia sesion en http://127.0.0.1:8000/admin/.

## Pruebas

Ejecuta la suite de pruebas incluida con:

```powershell
python manage.py test
```

Para comprobar el estado general del proyecto:

```powershell
python manage.py check
```

## Flujo de desarrollo

Cuando agregues una nueva funcionalidad:

1. Crea o modifica modelos en `pages/models.py`.
2. Genera las migraciones con `python manage.py makemigrations`.
3. Aplica los cambios con `python manage.py migrate`.
4. Agrega las rutas necesarias en `pages/urls.py`.
5. Implementa las vistas en `pages/views.py`.
6. Crea o modifica plantillas dentro de `templates/`.
7. Agrega pruebas en `pages/tests.py`.

Ejemplo para una nueva migracion:

```powershell
python manage.py makemigrations pages
python manage.py migrate
```

## Configuracion

La configuracion principal se encuentra en `django_base/settings.py`.

### Datos de desarrollo

- `DEBUG = True`
- Base de datos: SQLite
- Idioma: Ingles (`en-us`)
- Zona horaria: UTC
- Plantillas globales: `templates/`
- Aplicacion instalada: `pages`

### Antes de produccion

No utilices la configuracion de desarrollo tal como esta en produccion. Como minimo:

- Configura una `SECRET_KEY` segura mediante variables de entorno.
- Establece `DEBUG = False`.
- Incluye los dominios reales en `ALLOWED_HOSTS`.
- Configura HTTPS y cabeceras de seguridad.
- Sustituye SQLite por una base de datos adecuada al entorno.
- Cambia el backend de correo y otros servicios segun el despliegue.

## Variables y archivos sensibles

No publiques contrasenas, claves privadas ni claves secretas de Django. Se recomienda mover valores sensibles a variables de entorno antes de desplegar.

Los siguientes elementos ya estan excluidos habitualmente por `.gitignore`:

- `.venv/`
- `__pycache__/`
- Archivos `*.pyc`
- `db.sqlite3`
- Archivos de entorno y caches locales

## Contribuciones

Las contribuciones son bienvenidas:

1. Crea una rama desde `main`.
2. Implementa los cambios con una descripcion clara.
3. Ejecuta las pruebas y `python manage.py check`.
4. Abre un Pull Request con el contexto necesario.

## Licencia

Todavia no se ha definido una licencia para este proyecto. Agrega un archivo `LICENSE` antes de distribuirlo publicamente.

---

<div align="center">

Desarrollado como una base para construir aplicaciones Django.

</div>
