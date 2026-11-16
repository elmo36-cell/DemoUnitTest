# 📱 OmniCell — Sistema de Importación y Venta de Pantallas y Repuestos

**OmniCell** es una aplicación de escritorio desarrollada en **C# con Windows Forms**, orientada a la gestión integral de un negocio dedicado a la importación y comercialización de pantallas y repuestos para teléfonos celulares.

El sistema tiene como propósito facilitar la administración de las principales actividades comerciales y logísticas del negocio, permitiendo gestionar **productos, proveedores, compras, ventas e inventario** de manera organizada sobre una base de datos relacional en **SQL Server (`LabOmnicell`)**. Asimismo, incorpora un sistema de autenticación basado en roles para controlar el acceso de los usuarios según sus funciones dentro de la empresa.

Una de las principales funcionalidades del sistema es el **módulo de ventas**, mediante el cual se registran las operaciones de comercialización de pantallas y repuestos, se calculan automáticamente los subtotales y montos totales, se registra el sello o número de serie de garantía (`observacionGarantia`) y se actualizan en tiempo real las existencias disponibles en el inventario por sucursal.

---

## 🚀 Funcionalidades Principales

* **Módulo de Ventas (Punto de Venta):** Registro ágil de ventas a clientes minoristas, técnicos mayoristas y consumidor final, con cálculo automático de totales, selección de método de pago (`Efectivo`, `QR`, `Transferencia`), control de garantías seriadas y descuento inmediato en el inventario.
* **Gestión de Compras e Importaciones:** Registro maestro-detalle (`Compra` / `CompraDetalle`) de abastecimiento proveniente de proveedores internacionales y locales (`China`, `EE.UU.`, `Corea del Sur`, `Perú`, `Chile`, `Panamá`, `Bolivia`).
* **Catálogo Técnico y Compatibilidad:** Administración de marcas, modelos y pantallas (tecnologías `OLED Original`, `AMOLED`, `pOLED`, `IPS` e `Incell`) vinculadas mediante compatibilidad cruzada (`Compatibilidad`).
* **Control de Inventario Multi-Sucursal:** Monitoreo de `stockActual` y `stockMinimo` en 10 sucursales a nivel nacional, con alertas automáticas de reposición (`paInventarioStockBajo`).
* **Autenticación y Control de Acceso (RBAC):** Inicio de sesión con contraseñas cifradas que restringe las operaciones según el rol asignado (**Administrador** o **Vendedor**), además de auditoría completa (`usuarioRegistro`, `fechaRegistro`, `estado`) en las 15 entidades del sistema.

---

## 🗄️ Arquitectura de la Base de Datos (`LabOmnicell`)

Implementada en SQL Server con **15 tablas normalizadas** y **13 procedimientos almacenados**:

1. **Seguridad y Personal:** `Rol`, `Empleado`, `Usuario`
2. **Productos y Compatibilidad:** `Marca`, `Modelo`, `Pantalla`, `Compatibilidad`
3. **Proveedores, Compras e Inventario:** `Proveedor`, `Compra`, `CompraDetalle`, `Sucursal`, `Inventario`
4. **Clientes y Ventas:** `Cliente`, `Venta`, `VentaDetalle`

---

## 🛠️ Requisitos e Instalación

1. **Base de Datos:**
   * Ejecutar el script `ddl_dml_labomnicell.sql` en **SQL Server Management Studio (SSMS)**.
   * El script crea la base de datos `LabOmnicell`, el usuario `usromnicell` (`db_owner`), las tablas, procedimientos almacenados y datos iniciales.
2. **Aplicación de Escritorio:**
   * Abrir la solución `Omnicell.slnx` en **Visual Studio**.
   * Verificar la cadena de conexión en `App.config` apuntando a su servidor SQL Server con el usuario `usromnicell`.
   * Compilar y ejecutar el proyecto de inicio `CpOmnicell`.

---

## 🔐 Credenciales de Acceso (Entorno de Pruebas)

| Perfil / Componente | Usuario | Contraseña | Funciones Habilitadas |
| :--- | :--- | :--- | :--- |
| **Administrador** | `admin` | `123456` | Gestión total de productos, proveedores, compras, inventario, sucursales y personal. |
| **Vendedor** | `tperez` | `123456` | Módulo de ventas, cálculo de totales, registro de garantías y gestión de clientes. |
| **SQL Server Login** | `usromnicell` | `123456` | Usuario propietario (`db_owner`) de la base de datos `LabOmnicell`. |
