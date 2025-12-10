# 📖 Documentación de la API VStour - Brazo Web

Este repositorio contiene la especificación de la API Brazo Web en formato **OpenAPI (Swagger)**.

La especificación define todos los endpoints, modelos de datos, y los esquemas de seguridad (API Key y Token) necesarios para interactuar con la plataforma VStour.

---

## 🔑 Esquema de Seguridad de la API

La API Brazo Web utiliza un esquema de doble autenticación para todas las llamadas a endpoints que requieren acceso a los datos del contacto:

| Elemento | Tipo | Contenido | Ubicación | Vencimiento |
| :--- | :--- | :--- | :--- | :--- |
| **API Key** | Estático | `clicod` (Cliente) | **Header: `apikey`** | No aplica |
| **Token** | Bearer | Datos del Contacto Logueado | **Header: `Authorization: Bearer [TOKEN]`** | No tiene |

---

## 🚀 Visualización de la Documentación Interactiva

Existen dos métodos principales para ver la documentación interactiva de Swagger UI localmente.

### Opción 1: 🐳 Usando Docker Desktop (Recomendado)

Este método es el más limpio y portátil, usando la imagen oficial de Swagger UI sin dependencias locales adicionales (más allá de Docker).

#### Requisitos

* **Docker Desktop** instalado y en ejecución (requiere virtualización activada).

#### Instrucciones

1.  Asegúrate de estar en la raíz del proyecto (`/apibweb`).
2.  Ejecuta el siguiente comando. **¡IMPORTANTE!** Debes reemplazar `"C:/ruta/openapi.yaml"` por la **ruta absoluta** de tu archivo local `openapi.yaml`.

> **Ejemplo de ruta:** Si clonaste el proyecto en `C:\api\apibweb`, la ruta sería `"C:/api/apibweb/openapi.yaml"`.

docker run -d -p 8080:8080 -e SWAGGER_JSON=/tmp/openapi.yaml -v "C:/ruta/openapi.yaml":/tmp/openapi.yaml --name swagger-viewer swaggerapi/swagger-ui


3.  **Acceso:** Abre tu navegador y navega a:
    ➡️ **http://localhost:8080**

4.  **Para detener el visor:**
    ```
    docker stop swagger-viewer
    ```

---

### Opción 2: 🌐 Estático Local (Requiere Node.js)

Esta es la alternativa para usuarios que no tienen Docker o no pueden activar la virtualización.

#### Requisitos

* **Node.js** y **npm** instalados.

#### Pasos

| Acción | Comando (Ejecutar en PowerShell) | Nota |
| :--- | :--- | :--- |
| **1. Crear Carpeta UI** | `mkdir docs-ui` | Se crea un directorio para los archivos estáticos. |
| **2. Instalar Swagger UI** | `cd docs-ui` seguido de `npm install swagger-ui-dist` | Descarga los archivos HTML/CSS/JS. |
| **3. Copiar el YAML** | `copy ..\..\openapi.yaml node_modules\swagger-ui-dist\` | El `openapi.yaml` debe estar junto al `index.html` de la distribución. |
| **4. Instalar Servidor** | `npm install -g http-server` | Instala el servidor web estático (solo la primera vez). |

#### 5. Configurar `index.html`

Abre el archivo `docs-ui/node_modules/swagger-ui-dist/index.html` y modifica la línea de configuración del `url` para apuntar al archivo local:

```javascript
// --- Buscar y modificar dentro de la etiqueta <script> ---

// DESPUÉS (apuntando a tu archivo local):
url: "./openapi.yaml", 
6. Iniciar el Servidor
Desde la carpeta docs-ui/node_modules/swagger-ui-dist/, ejecuta:

http-server
Acceso: Abre tu navegador y navega a http://localhost:8080 (o el puerto que te indique la terminal).