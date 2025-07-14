# Investigación y Desarrollo de un CRUD con Django

## 1 Parte teórica

## Índice

1. [¿Qué es un CRUD y cuál es su propósito en aplicaciones web?](#qué-es-un-crud-y-cuál-es-su-propósito-en-aplicaciones-web)
2. [Patrones de arquitectura en desarrollo de software](#patrones-de-arquitectura-en-desarrollo-de-software)
3. [Estructura básica de un proyecto Django](#estructura-básica-de-un-proyecto-django)
4. [Flujo de datos entre formularios y la base de datos en Django](#flujo-de-datos-entre-formularios-y-la-base-de-datos-en-django)
5. [Herramientas y comandos de Django para desarrollo CRUD](#herramientas-y-comandos-de-django-para-desarrollo-crud)
6. [¿Cómo funciona el Admin de Django?](#cómo-funciona-el-admin-de-django)

---

## ¿Qué es un CRUD y cuál es su propósito en aplicaciones web?

**CRUD** (Create, Read, Update, Delete) es el conjunto de operaciones básicas para manipular datos en una base de datos a través de una aplicación web. Su propósito es facilitar una interacción eficiente entre el frontend y backend, permitiendo manejar los datos fácilmente.

**Ejemplos de aplicaciones que usan CRUD:**

* **Redes sociales**: Facebook, Instagram, Twitter.
* **Tableros Kanban**: Trello, Jira, Odoo.

Estas aplicaciones dependen en gran medida de operaciones CRUD para gestionar perfiles, tareas, publicaciones, etc.

---

## Patrones de arquitectura en desarrollo de software

### ¿Qué son los patrones de arquitectura?

Son esquemas que definen cómo dividir y organizar una aplicación en componentes claros, estableciendo la comunicación entre ellos. Esto ayuda a separar responsabilidades, facilitar el mantenimiento, mejorar la escalabilidad y permitir la reutilización de código.

### Patrón MVC (Modelo–Vista–Controlador)

| Componente      | Responsabilidad principal                         |
| --------------- | ------------------------------------------------- |
| **Modelo**      | Gestiona datos y reglas de negocio.               |
| **Vista**       | Presenta datos al usuario (HTML, JSON, GUI).      |
| **Controlador** | Procesa las peticiones y coordina modelo y vista. |

### Patrón MVT (Modelo–Vista–Template) – Django

Es una adaptación del MVC realizada por Django:

| Componente   | Equivalente en MVC | Rol en Django                                               |
| ------------ | ------------------ | ----------------------------------------------------------- |
| **Modelo**   | Modelo             | Igual, define lógica de negocio y acceso a datos (ORM).     |
| **Vista**    | Controlador        | Procesa peticiones HTTP y define lógica para mostrar datos. |
| **Template** | Vista              | Genera la interfaz visual (HTML, CSS, JS).                  |

Django maneja automáticamente parte del controlador (rutas).

---

## Estructura básica de un proyecto Django

Un proyecto Django está organizado principalmente en:

* **Modelos (`models.py`)**: Clases de Python que representan tablas de la base de datos.
* **Vistas (`views.py`)**: Funciones o clases Python que gestionan la lógica al recibir peticiones HTTP.
* **Plantillas (Templates)**: Archivos HTML que presentan datos usando etiquetas especiales de Django (`{% %}` para lógica y `{{ }}` para variables).
* **URLs (`urls.py`)**: Definen rutas claras y amigables, asociadas a vistas específicas.

### Uso del `{% %}` en plantillas:

Se usa para lógica condicional, bucles o cargar bloques de código:

```django
{% if usuario %}
  Hola, {{ usuario.nombre }}
{% endif %}
```

---

## Flujo de datos entre formularios y la base de datos en Django

1. Usuario llena un formulario HTML y lo envía.
2. Django recibe estos datos mediante una vista (función o clase).
3. La vista valida y usa los datos para crear o actualizar un objeto del modelo.
4. Django guarda ese objeto en la base de datos.
5. Django retorna una respuesta (página de confirmación o redirección).

---

## Herramientas y comandos de Django para desarrollo CRUD

### Comandos:

* `startproject`: Crea estructura inicial del proyecto Django.
* `startapp`: Crea la estructura básica de una aplicación dentro del proyecto.
* `makemigrations`: Detecta cambios en los modelos y genera migraciones.
* `migrate`: Aplica migraciones para sincronizar la base de datos.
* `runserver`: Ejecuta servidor local de desarrollo.
* `shell`: Consola interactiva para probar código y consultas ORM.

### Componentes clave:

* **Model**: Define estructura de datos en la base de datos.
* **ModelForm**: Formularios generados automáticamente desde modelos.
* **Vistas Genéricas (CBV)**:

  * `ListView`, `DetailView`, `CreateView`, `UpdateView`, `DeleteView`

Estas vistas aceleran significativamente la implementación CRUD.

* **Admin**: Interfaz web automática para gestión directa de datos.
* **createsuperuser**: Crea usuario administrador.

---

## ¿Cómo funciona el Admin de Django?

El Admin de Django es una interfaz web generada automáticamente para administrar los datos del proyecto.

### Funcionamiento:

1. **Modelos como base**: Usa los modelos para generar la estructura de tablas y formularios.
2. **Registro en panel (`admin.py`)**:

```python
from django.contrib import admin
from .models import MiModelo

admin.site.register(MiModelo)
```

3. **Autenticación y permisos**:

   * Acceso solo para usuarios staff.
   * Creación de superusuarios con control total.

4. **Interfaz Automática**:

   * CRUD sencillo.
   * Búsqueda, filtrado y ordenación integrados.
   * Personalizable mediante configuraciones en `admin.py`.

### Beneficios del Admin:

* Acelera la gestión administrativa sin programar frontend.
* Autogestión sencilla para administradores y editores.

---


* [Artículo de Medium para crear tu primer CRUD](https://medium.com/@gutundbose/aplicaci%C3%B3n-crud-con-django-82bb217493ea)
