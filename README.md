# 📚 Proyectos Informáticos – MySQL (CRUD, Función y Triggers)

**Estudiante:** Hanna Jineth Contreras Salinas  
**Curso:** Bases de Datos – IUDigital de Antioquia  

---

## 🎯 Objetivo
El propósito de este proyecto es implementar en **MySQL** distintos objetos de programación que fortalezcan la gestión de la base de datos `proyectos_informaticos`.  

Se desarrollaron:  
- **CRUD** (Create, Read, Update, Delete) mediante procedimientos almacenados para las tablas `docentes` y `proyectos`.  
- Una **función definida por el usuario (UDF)** para calcular el promedio de horas de los proyectos.  
- **Triggers** de auditoría que permiten guardar el historial de registros **actualizados** y **eliminados** en tablas de respaldo.  

---

## 📂 Estructura del proyecto

```bash
mysql-database-management-system/
├─ README.md
├─ TallerPractico_Hanna.txt     # documentación del taller
├─ sql/
│  ├─ 00_create_database.sql   # creación de la base de datos
│  ├─ 01_schema.sql            # tablas de auditoría (copia_*)
│  ├─ 02_seed.sql              # inserciones y pruebas
│  └─ 03_queries.sql           # procedimientos, triggers y función
└─ docs/
   └─ diagrama_logico.md       # descripción del modelo lógico
```

---

## ⚠️ Requisito previo

Los scripts **no crean** las tablas principales `docentes` y `proyectos`: el taller partía de una base de datos `proyectos_informaticos` que ya las tenía. Antes de ejecutar los pasos de abajo, esas dos tablas deben existir con un `id` autoincremental y las columnas que usan los procedimientos:

- `docentes`: `numero_documento`, `nombres`, `titulo`, `anios_experiencia`, `direccion`, `tipo_docente`
- `proyectos`: `nombre`, `descripcion`, `fecha_inicial`, `fecha_final`, `presupuesto`, `horas`

---

## 🚀 Ejecución en MySQL

Para ejecutar el proyecto en **MySQL** (Workbench, DBeaver o CLI):

1. Crear la base de datos (o usar la existente):
   ```sql
   SOURCE sql/00_create_database.sql;
   ```

2. Crear las tablas de auditoría:
   ```sql
   SOURCE sql/01_schema.sql;
   ```

3. Cargar procedimientos, triggers y función:
   ```sql
   SOURCE sql/03_queries.sql;
   ```

4. Insertar y validar con datos de prueba:
   ```sql
   SOURCE sql/02_seed.sql;
   ```

---

## 🧩 Solución implementada

**Tablas de respaldo:**
- `copia_actualizados_docentes`, `copia_eliminados_docentes`
- `copia_actualizados_proyectos`, `copia_eliminados_proyectos`

**Procedimientos almacenados:**
- `insertar_docente`, `listar_docentes`, `actualizar_docente`, `eliminar_docente`
- `insertar_proyecto`, `listar_proyectos`, `actualizar_proyecto`, `eliminar_proyecto`

**Función definida por el usuario:**
- `promedio_horas_proyectos()` → devuelve el promedio de horas registradas en los proyectos.

**Triggers:**
- `trg_docentes_update`, `trg_docentes_delete`
- `trg_proyectos_update`, `trg_proyectos_delete`

---

## 🧪 Pruebas realizadas

- Inserción de docentes y proyectos con procedimientos.
- Listado completo de registros.
- Actualización y eliminación de datos para verificar los triggers.
- Consulta de las tablas de respaldo (`copia_actualizados_*`, `copia_eliminados_*`).
- Ejecución de la función `promedio_horas_proyectos()` para validar la operación matemática.

---

## 📄 Licencia

[MIT](LICENSE)
