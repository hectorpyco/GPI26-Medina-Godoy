# Sistema de Control y Analítica de Egresados

Aplicación web para consultar y administrar información de egresados y cohortes de ingreso de la Facultad de Ciencias y Tecnologías de la Universidad Nacional de Caaguazú (FCyT-UNCA).

## Propósito

El proyecto busca ofrecer estadísticas sobre la graduación de forma rápida y clara. Reúne los datos institucionales en tableros y reportes que permiten observar tendencias, comparar carreras y cohortes, y apoyar el seguimiento académico y la toma de decisiones.

Entre otros indicadores, permite consultar:

- Cantidad de egresados por año, carrera, sexo y lugar de nacimiento.
- Distribución y promedio de la duración de los estudios, además de edad al egreso cuando hay fecha de nacimiento disponible.
- Tasas de graduación por cohorte de ingreso, tanto generales como desglosadas por sexo.
- Tasas históricas ponderadas: se suman los ingresantes y egresados de las cohortes que ya registran al menos un egresado, y la tasa se calcula sobre esos totales. Así, las cohortes se ponderan por su tamaño.
- Filtros por carrera, sexo, años de ingreso y egreso, y lugar de nacimiento.

## Origen y contexto académico

Este repositorio es un fork del trabajo de **César Medina y Lucas Godoy**, desarrollado para la materia **Gestión de Proyectos Informáticos**, del **5.º año de Ingeniería Informática, año 2026**, con el **Prof. Ing. Héctor Estigarribia**.

El fork continúa ese trabajo con mejoras orientadas a presentar las estadísticas de graduación de forma práctica y oportuna.

| Recurso | Enlace |
|---|---|
| Este fork | [hectorpyco/GPI26-Medina-Godoy](https://github.com/hectorpyco/GPI26-Medina-Godoy) |
| Repositorio original | [cmmedina918/GPI-Project](https://github.com/cmmedina918/GPI-Project) |
| GitHub de César Medina | [cmmedina918](https://github.com/cmmedina918) |
| GitHub de Lucas Godoy | [LucasGe8](https://github.com/LucasGe8) |

## Tecnologías

- Python y Django
- PostgreSQL
- Bootstrap y plantillas Django

## Probar localmente sin la base institucional

La configuración de demostración usa SQLite y una base local vacía. No requiere instalar PostgreSQL ni disponer del respaldo institucional.

1. Instalar Python.
2. Crear un entorno virtual e instalar las dependencias:

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\python.exe -m pip install -r requirements.txt
   ```

3. Crear las tablas locales:

   ```powershell
   .\.venv\Scripts\python.exe manage.py migrate --run-syncdb --settings=gpiproject.settings_demo
   ```

4. Crear un usuario para iniciar sesión:

   ```powershell
   .\.venv\Scripts\python.exe manage.py createsuperuser --settings=gpiproject.settings_demo
   ```

5. Iniciar el servidor:

   ```powershell
   .\.venv\Scripts\python.exe manage.py runserver --settings=gpiproject.settings_demo
   ```

6. Abrir [http://127.0.0.1:8000](http://127.0.0.1:8000) e iniciar sesión con el usuario creado. La base empieza vacía; se pueden cargar carreras, egresados y cohortes desde la aplicación.

La configuración normal del proyecto continúa usando PostgreSQL. El respaldo local `Recovery_gpi_project_v1` no se distribuye y está excluido de Git.

## Estructura principal

```text
analitica/   Indicadores, cálculos y vistas analíticas
egresados/   Modelos, formularios y gestión de egresados, carreras y cohortes
gpiproject/  Configuración y rutas del proyecto Django
templates/   Plantillas HTML
static/      Hojas de estilo y recursos estáticos
```
