# Sistema de Gestión - Mantenimiento BMW/Mini Toluca y Metepec

## 📋 Descripción

Sistema web completo para la gestión integral de un taller de mantenimiento automotriz especializado en BMW y MINI. Permite el control de vehículos, inventario de refacciones, generación de cotizaciones y exportación de reportes.

## ✨ Características Principales

### 🚗 Gestión de Vehículos
- Registro de entrada y salida de automóviles
- Información completa del cliente y vehículo
- Control de estados (en taller, terminado, entregado)
- Seguimiento de fechas de entrada y salida

### 🔧 Catálogo de Refacciones
- Inventario completo con códigos únicos
- Categorización por tipo de refacción
- Control de precios y stock
- Información de proveedores

### 💰 Cotizaciones Profesionales
- Generación automática de cotizaciones
- Cálculo automático de IVA (16%)
- Selección múltiple de refacciones
- Exportación a PDF y Excel

### 📊 Dashboard Interactivo
- Estadísticas en tiempo real
- Resumen de vehículos en taller
- Eficiencia del taller
- Vehículos recientes

## 🛠️ Tecnologías Utilizadas

### Backend
- **Python 3.8+**
- **Flask 2.3.3** - Framework web
- **SQLAlchemy 3.0.5** - ORM para base de datos
- **Flask-Login 0.6.3** - Autenticación de usuarios
- **SQLite** - Base de datos

### Frontend
- **Bootstrap 5.3.0** - Framework CSS
- **Font Awesome 6.4.0** - Iconos
- **jQuery 3.6.0** - JavaScript
- **Google Fonts (Inter)** - Tipografía

### Generación de Reportes
- **ReportLab 4.0.4** - Generación de PDF
- **OpenPyXL 3.1.2** - Generación de Excel

## 📦 Instalación

### Prerrequisitos
- Python 3.8 o superior
- pip (gestor de paquetes de Python)

### Pasos de Instalación

1. **Clonar el repositorio**
   ```bash
   git clone <url-del-repositorio>
   cd MantenimientoAuto
   ```

2. **Crear entorno virtual (recomendado)**
   ```bash
   python -m venv venv
   
   # En Windows
   venv\Scripts\activate
   
   # En macOS/Linux
   source venv/bin/activate
   ```

3. **Instalar dependencias**
   ```bash
   pip install -r requirements.txt
   ```

4. **Ejecutar la aplicación**
   ```bash
   python app.py
   ```

5. **Acceder al sistema**
   - Abrir navegador en: `http://localhost:5000`
   - Usuario por defecto: `admin`
   - Contraseña por defecto: `admin123`

## 🗄️ Estructura de la Base de Datos

### Tablas Principales

#### Usuario
- `id` - Identificador único
- `username` - Nombre de usuario
- `email` - Correo electrónico
- `password_hash` - Contraseña encriptada
- `nombre_completo` - Nombre completo
- `rol` - Rol del usuario (admin, usuario)
- `fecha_registro` - Fecha de registro

#### Vehiculo
- `id` - Identificador único
- `marca` - Marca del vehículo
- `modelo` - Modelo del vehículo
- `año` - Año del vehículo
- `color` - Color del vehículo
- `placas` - Número de placas
- `vin` - Número VIN (opcional)
- `cliente_nombre` - Nombre del cliente
- `cliente_telefono` - Teléfono del cliente
- `cliente_email` - Email del cliente
- `fecha_entrada` - Fecha de entrada al taller
- `fecha_salida` - Fecha de salida del taller
- `estado` - Estado actual (en_taller, terminado, entregado)
- `observaciones` - Observaciones adicionales
- `usuario_id` - Usuario que registró el vehículo

#### Refaccion
- `id` - Identificador único
- `codigo` - Código único de la refacción
- `nombre` - Nombre de la refacción
- `descripcion` - Descripción detallada
- `precio` - Precio unitario
- `stock` - Cantidad en inventario
- `categoria` - Categoría de la refacción
- `proveedor` - Proveedor de la refacción

#### Cotizacion
- `id` - Identificador único
- `vehiculo_id` - Vehículo asociado
- `fecha_creacion` - Fecha de creación
- `subtotal` - Subtotal sin IVA
- `iva` - Monto del IVA
- `total` - Total con IVA
- `estado` - Estado de la cotización
- `observaciones` - Observaciones
- `usuario_id` - Usuario que creó la cotización

#### CotizacionRefaccion
- `id` - Identificador único
- `cotizacion_id` - Cotización asociada
- `refaccion_id` - Refacción asociada
- `cantidad` - Cantidad solicitada
- `precio_unitario` - Precio unitario al momento
- `subtotal` - Subtotal del item

## 🚀 Funcionalidades Detalladas

### 1. Sistema de Autenticación
- Login seguro con encriptación de contraseñas
- Control de sesiones
- Roles de usuario (administrador, usuario)
- Protección de rutas

### 2. Gestión de Vehículos
- **Registro de entrada**: Captura completa de información del vehículo y cliente
- **Seguimiento**: Control de estados y fechas
- **Edición**: Modificación de información
- **Filtros**: Búsqueda por marca, cliente, placas, estado

### 3. Catálogo de Refacciones
- **Categorización**: Organización por tipo (Motor, Frenos, Suspensión, etc.)
- **Control de inventario**: Stock en tiempo real
- **Precios**: Gestión de precios actualizados
- **Proveedores**: Información de proveedores

### 4. Cotizaciones
- **Selección dinámica**: Agregar/quitar refacciones
- **Cálculo automático**: Subtotal, IVA y total
- **Exportación**: PDF y Excel profesionales
- **Seguimiento**: Estados de cotización

### 5. Dashboard
- **Estadísticas**: Vehículos en taller, terminados, total
- **Eficiencia**: Tasa de finalización
- **Vehículos recientes**: Últimos registros
- **Acciones rápidas**: Enlaces directos a funciones principales

## 📁 Estructura del Proyecto

```
MantenimientoAuto/
├── app.py                 # Aplicación principal Flask
├── requirements.txt       # Dependencias de Python
├── README.md             # Documentación
├── templates/            # Plantillas HTML
│   ├── base.html         # Plantilla base
│   ├── index.html        # Página de inicio
│   ├── login.html        # Página de login
│   ├── dashboard.html    # Dashboard principal
│   ├── vehiculos.html    # Lista de vehículos
│   ├── nuevo_vehiculo.html # Formulario nuevo vehículo
│   ├── refacciones.html  # Lista de refacciones
│   ├── nueva_refaccion.html # Formulario nueva refacción
│   ├── cotizaciones.html # Lista de cotizaciones
│   └── nueva_cotizacion.html # Formulario nueva cotización
├── static/               # Archivos estáticos
│   ├── css/             # Hojas de estilo
│   ├── js/              # JavaScript
│   └── images/          # Imágenes
└── taller.db            # Base de datos SQLite (se crea automáticamente)
```

## 🔧 Configuración

### Variables de Entorno
```python
# En app.py
app.config['SECRET_KEY'] = 'tu_clave_secreta_aqui_cambiala_en_produccion'
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///taller.db'
```

### Personalización
- **Colores**: Modificar variables CSS en `templates/base.html`
- **Logo**: Reemplazar iconos Font Awesome
- **Información del taller**: Actualizar en `templates/index.html`

## 📊 Reportes y Exportación

### PDF
- Diseño profesional con ReportLab
- Información completa del vehículo y cliente
- Tabla detallada de refacciones
- Cálculo de totales
- Encabezado personalizado del taller

### Excel
- Formato profesional con OpenPyXL
- Múltiples hojas de cálculo
- Fórmulas automáticas
- Estilos y formato

## 🔒 Seguridad

- **Autenticación**: Sistema de login seguro
- **Encriptación**: Contraseñas hasheadas con Werkzeug
- **Sesiones**: Control de sesiones con Flask-Login
- **Validación**: Validación de formularios
- **Protección CSRF**: Protección contra ataques CSRF

## 🚀 Despliegue en Producción

### Recomendaciones
1. **Cambiar SECRET_KEY**: Usar una clave secreta fuerte
2. **Base de datos**: Considerar PostgreSQL para producción
3. **Servidor web**: Usar Gunicorn o uWSGI
4. **Proxy reverso**: Nginx o Apache
5. **HTTPS**: Configurar certificado SSL
6. **Backup**: Implementar respaldos automáticos

### Ejemplo con Gunicorn
```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:8000 app:app
```

## 🐛 Solución de Problemas

### Error de Base de Datos
```bash
# Eliminar base de datos corrupta
rm taller.db
# Reiniciar aplicación (se creará automáticamente)
```

### Error de Dependencias
```bash
# Actualizar pip
pip install --upgrade pip
# Reinstalar dependencias
pip install -r requirements.txt --force-reinstall
```

### Error de Puerto
```bash
# Cambiar puerto en app.py
app.run(debug=True, host='0.0.0.0', port=5001)
```

## 📞 Soporte

Para soporte técnico o consultas:
- **Email**: contacto@bmwminitaller.com
- **Teléfono**: (722) XXX-XXXX

## 📄 Licencia

Este proyecto está desarrollado específicamente para el taller "Mantenimiento BMW/Mini Toluca y Metepec".

## 🔄 Actualizaciones

### Versión 1.0.0
- Sistema base completo
- Gestión de vehículos
- Catálogo de refacciones
- Cotizaciones con exportación
- Dashboard interactivo

### Próximas Funcionalidades
- [ ] Gestión de proveedores
- [ ] Reportes avanzados
- [ ] Notificaciones por email
- [ ] App móvil
- [ ] Integración con sistemas de pago

---

**Desarrollado con ❤️ para el taller Mantenimiento BMW/Mini Toluca y Metepec** 