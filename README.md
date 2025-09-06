# 🌱 PowerGreen

PowerGreen es una página web que nace con un propósito claro: que cada persona pueda conocer el impacto que deja en el planeta y, sobre todo, proveer las herramientas para reducirlo.

## 📱 Tutorial: Clonar el repo y generar el APK con Capacitor (Android)

### 🗺️ Resumen rápido de rutas

- **Comandos git, npm/pnpm/yarn y npx cap**: Se ejecutan desde la carpeta raíz del proyecto web (donde está `package.json` y `capacitor.config.*`)
- **Comandos Gradle** (`./gradlew ...`): Se ejecutan dentro de `android/`

### 0️⃣ Requisitos previos (una sola vez)

- **Node.js LTS** (18 o 20) y npm (o pnpm/yarn)
- **Git**
- **Java 17** (Temurin/Adoptium recomendado) → configura `JAVA_HOME`
- **Android Studio** (SDKs, Platform Tools, AVD)
- **Capacitor CLI** (v5+): se usa vía npx (no hace falta instalar global)
- **Cuenta y proyecto en Firebase** con Auth y Base de datos (Firestore o Realtime Database), y su config

### 1️⃣ Clonar el repositorio en tu PC

```bash
# 1. Elige una carpeta de trabajo
cd ~/dev

# 2. Clona el repo (reemplaza por tu URL real)
git clone https://github.com/tu-org/PowerGreen.git

# 3. Entra al proyecto
cd PowerGreen
```

### 2️⃣ Instalar dependencias del proyecto web

```bash
# con npm
npm ci

# (o npm install, o pnpm i, o yarn según uses)
```

### 3️⃣ Configurar variables/entorno (Firebase)

- Crea tu archivo de entorno si aplica (por ejemplo `.env`, `.env.production` o el que use tu build)
- Coloca allí las claves de Firebase config (`apiKey`, `authDomain`, `projectId`, etc.)
- Si el proyecto inyecta la config desde `capacitor.config.ts` o desde el código, asegúrate de que no queden vacías en producción
- Verifica que Auth y la DB (Firestore/Realtime) estén habilitadas en Firebase

> ⚠️ **Consejo**: Para apps empaquetadas con WebView (Capacitor), configura orígenes/permitidos y dominios de OAuth en Firebase si usas proveedores externos (Google, etc.)

### 4️⃣ Compilar la app web (build)

Este paso genera los archivos estáticos (por ejemplo en `dist/` o `build/`) que Capacitor copiará dentro del proyecto nativo.

```bash
# Revisa package.json para conocer el script correcto
npm run build
```

Asegúrate de que el resultado (ej.: `dist/`) coincida con lo configurado como `webDir` en `capacitor.config.ts/json`.

### 5️⃣ Preparar Android con Capacitor

Si es la primera vez que agregas Android:

```bash
npx cap add android
```

Cada vez que hagas `npm run build`, sincroniza con el proyecto nativo:

```bash
npx cap sync android

# (o al menos)
npx cap copy android
```

### 6️⃣ Abrir Android Studio

Desde la raíz del proyecto (donde está `package.json` y `capacitor.config.*`), ejecuta:

```bash
npx cap open android
```

Esto abre la carpeta `android/` en Android Studio.

### 7️⃣ Construir el APK (Debug) en Android Studio

**En Android Studio:**
- Menú **Build** → **Build Bundle(s) / APK(s)** → **Build APK(s)**
- Al terminar, el APK queda en: `android/app/build/outputs/apk/debug/app-debug.apk`

**💡 Tip**: También puedes usar Gradle por consola, dentro de `android/`:

```bash
cd android
./gradlew assembleDebug

# Salida: app/build/outputs/apk/debug/app-debug.apk
```

## 🤝 Contribuir

Si quieres contribuir al proyecto, por favor:

1. Haz un fork del repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Haz commit de tus cambios (`git commit -m 'Añade nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia [especificar licencia] - mira el archivo [LICENSE](LICENSE) para detalles.

---

💚 **¡Gracias por contribuir a un planeta más verde!**
