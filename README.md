# 🏁 Proyecto MotoGP: Base de Datos Relacional

Este proyecto contiene la implementación de una base de datos relacional para la gestión de resultados históricos de MotoGP. El diseño ha sido normalizado para eliminar redundancias y asegurar la integridad de los datos.

## 📁 Contenido del Repositorio
*   `entrega_motogp.sql`: Script autoejecutable que contiene la estructura (DDL) y los datos (DML) ya procesados y limpios.
*   `Informe_Proyecto.pdf`: Documentación detallada del modelo relacional y proceso de carga.

---

## 🚀 Instrucciones de Carga (Despliegue)

El archivo SQL es **autónomo**. No es necesario crear la base de datos previamente ni importar archivos CSV externos, ya que el script se encarga de todo el proceso.

### Opción A: Desde la Terminal (Recomendado)
Sitúese en la carpeta donde se encuentra el archivo y ejecute el siguiente comando:

```bash
mysql -u su_usuario -p < entrega_motogp.sql
```

### Opción B: Desde MySQL Workbench
1. Vaya a **Server** > **Data Import**.
2. Seleccione **Import from Self-Contained File** y busque `entrega_motogp.sql`.
3. Haga clic en **Start Import**.

---

## 📊 Estructura del Modelo
La base de datos se compone de **7 tablas normalizadas**:
*   **Maestras:** `Piloto`, `Equipo`, `Moto`, `Categoria`, `Circuito`.
*   **Relacionales:** `Carrera` y la tabla central **`Participa`**.

> **Nota técnica:** Se ha implementado la tabla `Participa` para resolver la relación **Muchos a Muchos (N:M)** entre Pilotos y Carreras, permitiendo almacenar atributos específicos de cada participación (puntos, posición, tiempos, etc.).

---


## 🛠️ Decisiones de Diseño e Ingeniería de Datos
*   **Limpieza de Nulos:** Se han gestionado los valores vacíos del dataset original en la columna `speed`, convirtiéndolos en valores `NULL` lógicos.
*   **Formatos Flexibles:** La columna `tiempo` se ha definido como `VARCHAR` para dar soporte a incidencias de carrera como "+5.234" o "9 Laps", manteniendo la fidelidad del historial.
*   **Integridad:** El script garantiza el cumplimiento de todas las **Claves Foráneas (FK)** y restricciones de integridad.

