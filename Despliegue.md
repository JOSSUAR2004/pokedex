# 🚀 Proyecto Angular desplegado en Vercel

Este repositorio contiene una aplicación desarrollada con **Angular**, desplegada utilizando la plataforma **Vercel** como parte del curso **Arquitectura Distribuida**, del **9no semestre de Ingeniería de Sistemas**.

---

## 🧾 Detalles del proyecto

- 📚 **Asignatura**: Arquitectura Distribuida  
- 🎓 **Semestre**: 9no – Ingeniería de Sistemas  
- 👨‍💻 **Autor**: Jossuar Bohorquez  
- 🔗 **Repositorio**: https://github.com/JOSSUAR2004/proyecto-arquitectura-distribuida

---

## ⚙️ Estructura del proyecto

proyecto-arquitectura-distribuida/
├── dist/
│   └── pokedex-angular/
│       ├── index.html
│       ├── main.js
│       ├── styles.css
│       └── ...
├── angular.json
├── package.json
└── README.md

---

## ✅ Paso a paso del despliegue en Vercel

### 1️⃣ Construcción del proyecto Angular

Desde la raíz del proyecto, se ejecutó:

     npm run build

Esto generó el contenido estático listo para producción en la ruta:

    /dist/pokedex-angular/

---

### 2️⃣ Subir el proyecto a GitHub

Si no estaba versionado aún, se hizo lo siguiente:

    git init
    git add .
    git commit -m "Despliegue listo"
    git branch -M main
    git remote add origin https://github.com/JOSSUAR2004/proyecto-arquitectura-distribuida.git
    git push -u origin main

---

### 3️⃣ Conectar con Vercel

1. Ingresar a https://vercel.com
2. Iniciar sesión con GitHub
3. Hacer clic en “Add New Project”
4. Seleccionar el repositorio `proyecto-arquitectura-distribuida`

---

### 4️⃣ Configuración del proyecto en Vercel

En el paso de configuración:

- **Framework Preset**: `Other`
- **Root Directory**: dist/proyecto-arquitectura-distribuida
- **Build Command**: (vacío)
- **Output Directory**: .

---



### 6️⃣ Despliegue final

- Se hizo clic en “Deploy”
- Vercel desplegó la carpeta `dist/proyecto-arquitectura-distribuida`
- Se obtuvo una URL pública como:

    https://proyecto-arquitectura-distribuida.vercel.app

---

## 🛡️ Observaciones

- Este es un despliegue sin backend (solo frontend)
- La app puede conectarse a servicios externos vía HTTP
- Ideal para sitios estáticos, SPA y prototipos rápidos

---

## 🙌 Autor

**Jossuar Bohorquez**  
Estudiante de Ingeniería de Sistemas  
GitHub: https://github.com/JOSSUAR2004
