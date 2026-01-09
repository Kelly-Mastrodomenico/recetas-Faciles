# Instalación

[← Volver al índice](index.md)

---

## 💻 Requisitos del Sistema

### Software Necesario

| Herramienta | Versión Mínima | Propósito |
|-------------|----------------|-----------|
| **Navegador Web** | Cualquier versión actual | Chrome, Firefox, Safari, Edge |
| **Editor de Código** | - | Visual Studio Code (recomendado) |
| **Git** | 2.0+ | Control de versiones |
| **Node.js** (opcional) | 14.0+ | Para servidor de desarrollo |

### Requisitos de Backend (Fase Futura)

| Software | Versión Mínima |
|----------|----------------|
| **PHP** | 7.4+ |
| **MySQL** | 5.7+ o MariaDB 10.4+ |
| **Apache/Nginx** | - |

---

## 📥 Pasos de Instalación

### 1. Clonar el Repositorio

```bash
# Clonar desde GitHub
git clone https://github.com/tu-usuario/recetas-faciles.git

# Navegar al directorio del proyecto
cd recetas-faciles
```

### 2. Estructura de Archivos

Una vez clonado, la estructura del proyecto será:

```
recetas-faciles/
├── index.html
├── css/
│   ├── styles.css
│   └── responsive.css
├── js/
│   ├── main.js
│   ├── carousel.js
│   └── search.js
├── img/
│   ├── recetas/
│   └── categorias/
├── docs/
│   └── (documentación)
└── README.md
```

### 3. Configuración del Entorno de Desarrollo

#### Opción A: Servidor Local Simple

Abrir directamente `index.html` en el navegador.

**Nota:** Algunas funcionalidades JavaScript pueden requerir un servidor web.

#### Opción B: Live Server (Recomendado)

Si usas **Visual Studio Code:**

1. Instalar extensión "Live Server"
2. Hacer clic derecho en `index.html`
3. Seleccionar "Open with Live Server"

#### Opción C: Servidor Python

```bash
# Python 3
python -m http.server 8000

# Abrir en navegador:
# http://localhost:8000
```

#### Opción D: Servidor Node.js

```bash
# Instalar http-server globalmente
npm install -g http-server

# Ejecutar servidor
http-server -p 8000

# Abrir en navegador:
# http://localhost:8000
```

---

## 🗄️ Configuración de Base de Datos (Fase Futura)

### 1. Crear la Base de Datos

```sql
-- Importar el archivo SQL proporcionado
mysql -u root -p < recetas.sql
```

### 2. Estructura de Tablas

El archivo `recetas.sql` incluye las siguientes tablas:

**Tabla: recetas**
```sql
CREATE TABLE recetas (
  id INT(11) NOT NULL AUTO_INCREMENT,
  titulo VARCHAR(150) NOT NULL,
  descripcion TEXT,
  tiempo_preparacion INT(11) NOT NULL,
  tiempo_coccion INT(11) DEFAULT 0,
  porciones INT(11) NOT NULL,
  dificultad ENUM('facil','media','dificil') DEFAULT 'facil',
  imagen VARCHAR(255),
  id_categoria INT(11) NOT NULL,
  id_usuario INT(11) NOT NULL,
  fecha_publicacion DATETIME DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (id)
);
```

**Relaciones:**
- `recetas.id_categoria` → `categorias.id`
- `recetas.id_usuario` → `usuarios.id`

### 3. Datos de Ejemplo

El archivo SQL incluye 6 recetas de ejemplo:
- Brownie de Chocolate
- Pasta Carbonara
- Ensalada César
- Smoothie de Fresa
- Pancakes
- Pollo al Horno

---

## 🔧 Variables de Entorno (Fase Backend)

Crear un archivo `.env` en la raíz del proyecto:

```env
# Configuración de Base de Datos
DB_HOST=localhost
DB_PORT=3306
DB_NAME=recetas
DB_USER=root
DB_PASSWORD=tu_contraseña

# Configuración de la Aplicación
APP_ENV=development
APP_DEBUG=true
APP_URL=http://localhost:8000

# Configuración de Subida de Archivos
UPLOAD_MAX_SIZE=5242880
ALLOWED_EXTENSIONS=jpg,jpeg,png,webp
```

---

## ✅ Verificación de la Instalación

### Checklist de Comprobación

- [ ] El proyecto se clona correctamente
- [ ] El archivo `index.html` se abre en el navegador
- [ ] Los estilos CSS se cargan correctamente
- [ ] Las imágenes se visualizan
- [ ] El banner carrusel funciona
- [ ] La barra de búsqueda responde
- [ ] El menú de categorías se despliega
- [ ] El diseño es responsive

### Prueba Rápida

1. Abrir `index.html` en el navegador
2. Verificar que se muestre la página de inicio
3. Interactuar con el banner carrusel
4. Probar la búsqueda de recetas
5. Hacer clic en las categorías
6. Redimensionar la ventana para probar responsive

---

## 🐛 Solución de Problemas

### Las imágenes no se cargan

**Solución:** Verificar que las rutas de las imágenes sean relativas y correctas:
```html
<img src="img/recetas/brownie.jpg" alt="Brownie">
```

### Los estilos no se aplican

**Solución:** Verificar enlaces en el `<head>` de `index.html`:
```html
<link rel="stylesheet" href="css/styles.css">
```

### JavaScript no funciona

**Solución:** Usar un servidor web local (no abrir directamente el archivo HTML).

---

## 📚 Recursos Adicionales

- [Documentación de Git](https://git-scm.com/doc)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Live Server Extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

---

[← Anterior: Introducción](introduccion.md) | [Siguiente: Uso →](uso.md)
