# SIGI – Prototipo Mobile

**Sistema Integral de Gestión de Inventario (SIGI)** para un supermercado.
Este repositorio corresponde al **prototipo de la aplicación móvil** (vista de celular) del sistema.

- **Curso:** Innovación Tecnológica – Universidad ECCI
- **Docente:** Juan Sebastian Sanchez Gomez
- **Integrantes:**  Andres Felipe Arias Hernandez, Lina Fernanda Andrade, Laura Valentina Castiblanco Puentes, Ana Maria Leal Martinez, Yeimmy Alejandra Sandoval Arias

---

## Objetivo

Agilizar la operación diaria en caja y bodega desde el celular: registrar ventas por código de barras, controlar el inventario por lotes con fecha de vencimiento, registrar la entrada de mercancía y consultar alertas. La meta del proyecto es **reducir en un 30 % las mermas por vencimiento**.

## Sobre el prototipo

> La aplicación es **responsive**: el mismo código se adapta a PC y a celular. Para ver la vista móvil, abrir el sistema desde un celular o activar el modo dispositivo del navegador (F12 → icono de celular). En móvil el menú lateral se compacta y muestra solo íconos.

## Usuarios de prueba

| Rol | Correo | Contraseña |
|---|---|---|
| Administrador | admin@sigi.com | admin123 |
| Cajero | cajero1@sigi.com | cajero123 |
| Bodeguero | bodega1@sigi.com | bodega123 |

## Pantallas del prototipo

| N.º | Pantalla | Rol | Ruta |
|---|---|---|---|
| 01 | Inicio de sesión | Todos | `index.php` |
| 02 | Dashboard | Administrador | `views/admin/dashboard.php` |
| 03 | Gestión de Productos | Administrador | `views/admin/productos.php` |
| 04 | Nuevo Producto | Administrador | `views/admin/productos.php` (ventana modal) |
| 05 | Editar Producto | Administrador | `views/admin/productos.php` (ventana modal) |
| 06 | Punto de Venta (POS) | Cajero y Administrador | `views/cajero/pos.php` |
| 07 | Venta Registrada | Cajero y Administrador | `views/cajero/pos.php` (ventana modal) |
| 08 | Reportes de Ventas (PEPS) | Administrador | `views/admin/reportes.php` |
| 09 | Centro de Alertas | Administrador | `views/admin/alertas.php` |
| 10 | Inventario (Lotes) | Bodeguero y Administrador | `views/bodeguero/inventario.php` |
| 11 | Registrar Entrada de Mercancía | Bodeguero y Administrador | `views/bodeguero/inventario.php` (ventana modal) |

## Funcionalidades

- Inicio de sesión con redirección según el rol (cajero, bodeguero, administrador)
- Punto de venta por código de barras con carrito, total, efectivo recibido y cambio
- Comprobante de venta con opción de imprimir
- Inventario por producto con estado de stock y últimos movimientos de entrada y salida
- Registro de entrada de mercancía con fecha de vencimiento del lote
- Centro de alertas de productos próximos a vencer y de stock mínimo
- Gestión de productos: búsqueda, creación, edición y eliminación
- Dashboard y reportes de ventas por rango de fechas

## Estructura del repositorio

```
SIGI2/
├── index.php          Inicio de sesión
├── logout.php         Cierre de sesión
├── assets/            Recursos estáticos (estilos, scripts, imágenes)
├── config/            Configuración y conexión a la base de datos
└── views/
    ├── admin/         Dashboard, productos, reportes, alertas
    ├── cajero/        Punto de venta
    └── bodeguero/     Inventario y entradas
SIGI_database.sql      Base de datos (importar en phpMyAdmin)
```

## Tecnologías

PHP · MySQL · HTML/CSS/JavaScript (diseño responsive)

## Cómo ejecutarlo en local

1. Instalar [XAMPP](https://www.apachefriends.org/) e iniciar **Apache** y **MySQL**.
2. Copiar la carpeta `SIGI2` en `C:\xampp\htdocs\`.
3. Abrir `http://localhost/phpmyadmin`, crear una base de datos llamada **`sigi_db`** (cotejamiento `utf8mb4_general_ci`) y **importar** dentro de ella el archivo `SIGI_database.sql`.
4. La conexión está en `config/db.php` y usa los valores por defecto de XAMPP: host `localhost`, usuario `root`, contraseña vacía y base de datos `sigi_db`. Si tu MySQL tiene otra configuración, ajústalos en ese archivo.
5. Abrir `http://localhost/SIGI2/index.php` en el navegador, o desde un celular conectado a la misma red con `http://IP_DE_TU_PC/SIGI2/index.php`.

## Mejoras identificadas en las pruebas de usabilidad (siguiente iteración)

1. Banner de pantalla completa, con ícono, alto contraste y vibración corta, cuando se bloquee una venta por falta de stock.
2. Botón permanente "Buscar producto" en la pantalla de escaneo, para no salir del flujo si falla la lectura.
3. Atajos rápidos de fecha (+7, +30, +90 días) y lectura de la fecha impresa con la cámara (OCR) en el registro de vencimiento.
4. Alertas diferenciadas por color (rojo: vencimiento, amarillo: stock mínimo) y agrupadas por ubicación en la estantería.
5. Cierre de caja con la diferencia resaltada en color y nota de justificación antes de confirmar.

## Comentarios por pantalla

Los comentarios se dejan en la pestaña **Issues** de este repositorio. Indicar en el título el número de la pantalla, por ejemplo: `[11] Registrar Entrada de Mercancía – comentario`.

## Videos

- Testeo móvil: https://youtu.be/8b0Gd5GOWgE
- Video del proyecto: https://youtu.be/gO5ykFAgB5g
