# 🌱 PowerGreen

PowerGreen es una página web que nace con un propósito claro: que cada persona pueda conocer el impacto que deja en el planeta y, sobre todo, proveer las herramientas para reducirlo.

## Tutorial: Clonar el repo y generar el APK con Capacitor (Android)

### Resumen rápido de rutas

- **Comandos git, npm y npx cap**: Se ejecutan desde la carpeta raíz del proyecto web (donde está `package.json` y `capacitor.config.*`)
- **Comandos Gradle** (`./gradlew ...`): Se ejecutan dentro de `android/`

### Requisitos previos (una sola vez)

- **Node.js LTS** (18 o 20) y npm (o pnpm/yarn)
- **Git**
- **Java 17** (Temurin/Adoptium recomendado) → configura `JAVA_HOME`
- **Android Studio** (SDKs, Platform Tools, AVD)

### Clonar el repositorio en tu PC

```bash
# 1. Elige una carpeta de trabajo
cd ~/dev

# 2. Clona el repo (reemplaza por tu URL real)
git clone https://github.com/tu-org/PowerGreen.git

# 3. Entra al proyecto
cd PowerGreen
```

### Instalar dependencias del proyecto web

```bash
# con npm
npm ci

# (o npm install, o pnpm i, o yarn según uses)
```

### Compilar la app web (build)

Este paso genera los archivos estáticos (por ejemplo en `dist/` o `build/`) que Capacitor copiará dentro del proyecto nativo.

```bash
# Revisa package.json para conocer el script correcto
npm run build
```

Asegúrate de que el resultado (ej.: `dist/`) coincida con lo configurado como `webDir` en `capacitor.config.ts/json`.

### Preparar Android con Capacitor

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

### Abrir Android Studio

Desde la raíz del proyecto (donde está `package.json` y `capacitor.config.*`), ejecuta:

```bash
npx cap open android
```

Esto abre la carpeta `android/` en Android Studio.

### Construir el APK (Debug) en Android Studio

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


💚 **¡Gracias por contribuir a un planeta más verde!**
