# 🚀 Despliegue de un sitio en Azure Static Web Apps mediante un Fork en GitHub (100% en la nube)
### Link de la web en la nube: https://white-field-0177d4a10.6.azurestaticapps.net/


**Autor:** Jossuar Bohorquez 👨‍💻  
**Repositorio:** https://github.com/JOSSUAR2004/jossuarpoke🐙**
**Asignatura:** Sistemas Distribuidos 📚  
**Semestre:** 9no semestre - Ingeniería de Sistemas 🎓  
### Fecha: 13/04/2025 📅 
---
Este tutorial te guía paso a paso para desplegar un sitio en **Azure Static Web Apps** usando un **fork de un repositorio en GitHub**, sin necesidad de clonar el código localmente.

---

## 🧾 Requisitos Previos

- Cuenta de **GitHub**.
- Cuenta de **Azure**.

---

## 1. 🔱 Haz un Fork del Repositorio

1. Ve al repositorio original en GitHub.
2. Haz clic en el botón **"Fork"** (arriba a la derecha).
3. Selecciona tu cuenta como destino del fork.
4. Opcionalmente, cambia el nombre del repositorio fork si lo deseas.

---

## 2. ☁️ Crea una Static Web App en Azure

1. Accede al [Portal de Azure](https://portal.azure.com/).
2. Busca **"Static Web Apps"** y haz clic en **Crear**.
3. Llena los campos requeridos:
   - **Subscription**: tu suscripción activa de Azure.
   - **Resource Group**: crea uno nuevo o selecciona uno existente.
   - **Name**: un nombre único para tu aplicación.
   - **Region**: selecciona la región más cercana a tus usuarios.
   - **Deployment source**: elige **GitHub**.
   - Autoriza a Azure a acceder a tu cuenta de GitHub si es la primera vez.
   - Selecciona el repositorio fork que creaste.
   - Selecciona la rama principal (por lo general `main` o `master`).

4. En la sección de **Build Details**:
   - **Build Presets**: selecciona el tipo de aplicación (React, Angular, Vue, etc.) o "Custom" si no se adapta a una plantilla.
   - **App location**: ruta raíz del código fuente (`/` si está en la raíz).
   - **Output location**: carpeta donde se genera el sitio compilado (por ejemplo `dist`, `build`, etc.).

5. Revisa y haz clic en **Crear**.

---

## 3. 🛡️ Configura seguridad con `staticwebapp.config.json`

Para agregar cabeceras de seguridad HTTP, crea un archivo en tu repositorio llamado:

```
staticwebapp.config.json
```

Coloca el siguiente contenido:

```json
{
  "globalHeaders": {
    "Content-Security-Policy": "default-src 'self'; img-src 'self' https://raw.githubusercontent.com https://pokeapi.co https://assets.pokemon.com; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; connect-src 'self' https://beta.pokeapi.co",
    "X-Frame-Options": "DENY",
    "Permissions-Policy": "geolocation=(), microphone=(), camera=()"
  },
  "navigationFallback": {
    "rewrite": "/index.html",
    "exclude": ["/images/", "/css/", "/js/*", "/favicon.ico"]
  }
}
```

📌 Este archivo debe estar en la raíz del **directorio de salida** (por ejemplo, dentro de la carpeta `dist/` si usas Angular, o `build/` si usas React).
##  ✅  Explicación Técnica: Headers de Seguridad

**Content-Security-Policy**  
Establece reglas estrictas sobre qué recursos pueden cargarse, previniendo ataques XSS e inyección de código malicioso.

**HTTP Strict Transport Security**  
Fuerza conexiones HTTPS y previene ataques de downgrade, con cache prolongado para mejor performance.

**X-Content-Type-Options**  
Anula el "MIME sniffing" del navegador, evitando ejecución de archivos como código ejecutable.

**Feature-Policy**  
Controla el acceso a APIs del navegador como geolocalización o cámara, reduciendo superficie de ataque.

---

## 4. 🤖 GitHub Actions se configura automáticamente

Azure agregará automáticamente un archivo de flujo de trabajo (`.github/workflows/azure-static-web-apps-<algo>.yml`) a tu repositorio fork.

Asegurate de cambiar aquí la ruta donde se encuentra tu aplicacion
Este archivo contiene los pasos para construir y desplegar tu aplicación cada vez que haces un cambio.

---

## 5. ✅ Primer despliegue automático

Una vez creada la Static Web App, Azure ejecutará el flujo de trabajo y desplegará tu aplicación automáticamente.

Puedes monitorear el proceso en:
- El portal de Azure → tu recurso de Static Web App.
- En GitHub → pestaña **Actions** del repositorio fork.

---

## 6. 🌐 ¡Tu sitio ya está publicado!

Una vez completado el flujo de trabajo, tendrás una URL como esta:

```
https://white-field-0177d4a10.6.azurestaticapps.net/
```

Puedes:
- Visitar la URL para ver tu sitio.
- Configurar un dominio personalizado desde el portal de Azure.

## 6. 🌐 DIAGRAMA DE INFRAESTRUCTURA
![](https://i.imgur.com/cZeIAgN.png)

## 🙌 Autor
**Jossuar Bohorquez**  
**Estudiante de Ingeniería de Sistemas**  
**GitHub: https://github.com/JOSSUAR2004**
