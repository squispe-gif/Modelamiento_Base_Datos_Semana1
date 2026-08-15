# ✈️ Modelamiento de Bases de Datos - Semana 1
## Caso de Negocio: Línea Aérea BT&Airways

* **Institución:** Instituto Profesional Duoc UC
* **Asignatura:** Modelamiento de Bases de Datos (PRY2204)
* **Evaluación:** Evaluación Formativa - Semana 1: *Aplicando conceptos de modelamiento inicial*

---

## 📌 Resumen Ejecutivo del Proyecto

La línea aérea **BT&Airways** cuenta con más de 25 años en el mercado del transporte internacional de pasajeros. Debido al alto crecimiento de sus operaciones (alrededor de 35,000 vuelos actuales con proyección a triplicarse), requiere diseñar e implementar una Base de Datos robusta de alta calidad.

En esta primera etapa, se identifican las entidades del negocio, sus atributos, claves primarias/foráneas, opcionalidad y tipos de datos (dominios) en notaciones **Barker** y **Bachman / Ingeniería de la Información (IE)**.

---

## 🏗️ 1. Clasificación de Entidades

| Entidad | Tipo | Descripción |
| :--- | :--- | :--- |
| **`PASAJERO`** | **Fuerte** | Cliente que realiza reservas y viaja en la aerolínea. |
| **`EMPLEADO`** | **Fuerte** | Personal de la compañía que atiende y registra las reservas. |
| **`VUELO`** | **Fuerte** | Itinerarios y trayectos de vuelo programados. |
| **`RESERVA`** | **Débil / Dependiente** | Transacción comercial que vincula a un Pasajero, un Vuelo y al Empleado que realiza la atención. |

---

## 📊 2. Especificación del Modelo de Datos

### 🔹 Notación Barker (Modelo Lógico)
* `#` = Identificador Único (Primary UID)
* `*` = Atributo Obligatorio
* `o` = Atributo Opcional

* **`PASAJERO`**: `# * num_pasaporte`, `* nombre_completo`, `* fecha_nacimiento`, `* nacionalidad`, `o telefono`, `o email`
* **`EMPLEADO`**: `# * rut_empleado`, `* nombre_completo`, `* direccion`, `* sueldo_base`, `* fecha_ingreso`, `* genero`, `* telefono_movil`, `o telefono_contacto`
* **`VUELO`**: `# * num_vuelo`, `* fecha_salida`, `* fecha_llegada`, `* hora_salida`
* **`RESERVA`**: `# * num_reserva`, `* fecha_reserva`, `* fecha_viaje`, `* estado`

---

### 🔹 Dominios y Tipos de Datos (Modelo Relacional / Bachman)

| Tabla | Atributo | Tipo de Dato | Clave | Obligatoriedad |
| :--- | :--- | :--- | :--- | :--- |
| **`PASAJERO`** | `num_pasaporte` | `VARCHAR2(20)` | **PK** | NOT NULL |
| | `nombre_completo` | `VARCHAR2(100)` | | NOT NULL |
| | `fecha_nacimiento`| `DATE` | | NOT NULL |
| | `nacionalidad` | `VARCHAR2(50)` | | NOT NULL |
| | `telefono` | `VARCHAR2(20)` | | NULL (Opcional) |
| | `email` | `VARCHAR2(100)` | | NULL (Opcional) |
| **`EMPLEADO`** | `rut_empleado` | `VARCHAR2(12)` | **PK** | NOT NULL |
| | `nombre_completo` | `VARCHAR2(100)` | | NOT NULL |
| | `direccion` | `VARCHAR2(150)` | | NOT NULL |
| | `sueldo_base` | `NUMBER(10,2)` | | NOT NULL |
| | `fecha_ingreso` | `DATE` | | NOT NULL |
| | `genero` | `VARCHAR2(15)` | | NOT NULL |
| | `telefono_movil` | `VARCHAR2(20)` | | NOT NULL |
| | `telefono_contacto`| `VARCHAR2(20)` | | NULL (Opcional) |
| **`VUELO`** | `num_vuelo` | `VARCHAR2(10)` | **PK** | NOT NULL |
| | `fecha_salida` | `DATE` | | NOT NULL |
| | `fecha_llegada` | `DATE` | | NOT NULL |
| | `hora_salida` | `VARCHAR2(8)` | | NOT NULL |
| **`RESERVA`** | `num_reserva` | `NUMBER(10)` | **PK** | NOT NULL |
| | `fecha_reserva` | `DATE` | | NOT NULL |
| | `fecha_viaje` | `DATE` | | NOT NULL |
| | `estado` | `VARCHAR2(15)` | | NOT NULL |
| | `num_pasaporte` | `VARCHAR2(20)` | **FK** | NOT NULL |
| | `rut_empleado` | `VARCHAR2(12)` | **FK** | NOT NULL |
| | `num_vuelo` | `VARCHAR2(10)` | **FK** | NOT NULL |

---

## 🔄 3. Relaciones y Cardinalidades

1. **`PASAJERO` — `RESERVA` (1:N):** Un Pasajero puede realizar una o muchas reservas. Una reserva pertenece a un solo pasajero.
2. **`EMPLEADO` — `RESERVA` (1:N):** Un Empleado atiende cero, una o muchas reservas. Una reserva es atendida por un solo empleado.
3. **`VUELO` — `RESERVA` (1:N):** Un Vuelo contiene cero, una o muchas reservas asignadas. Una reserva corresponde a un solo vuelo.

---

## 📁 4. Estructura del Repositorio

* 📄 `Encargo_Semanal.docx`: Documento oficial Word con las evidencias fotográficas de los modelos Lógico (Barker) y Relacional (Bachman/IE).
* 📦 `Encargo_Semanal.zip`: Archivo comprimido con el diseño original de **Oracle SQL Developer Data Modeler** (`.dmd` y su subcarpeta de configuración).
* 📄 `README.md`: Resumen técnico del encargo.
