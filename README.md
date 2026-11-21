# 📱 Encuentros App - iOS & Web (Capacitor)

Proyecto preparado para compilar como **aplicación nativa de iOS (para la App Store)** y ejecutable en web/móvil con acceso directo a la **cámara física para escaneo de códigos QR**.

---

## 📂 Estructura del Proyecto

```text
encuentros-app/
├── public/
│   └── index.html          # Aplicación completa con lector QR por cámara real
├── ios/
│   └── App/
│       └── App/
│           └── Info.plist  # Configuración iOS con permisos de cámara y privacidad
├── capacitor.config.json   # Configuración de Capacitor (ID de paquete: com.encuentros.app)
├── package.json            # Dependencias del proyecto
└── README.md               # Esta guía
```

---

## 🚀 1. Cómo probar la aplicación AHORA MISMO

Puedes probar la app con la cámara activa de dos formas:

### Opción A: Abrir directamente en tu navegador (Safari / Chrome)
Haz doble clic en el archivo `public/index.html` o ejecuta en tu terminal:
```bash
open public/index.html
```
1. Ve a la pestaña **«📷 Escanear»**.
2. Tu navegador te pedirá permiso para usar la cámara: pulsa **«Permitir»**.
3. Apunta a cualquier código QR de un evento y verás cómo lo detecta en tiempo real con sonido y vibración háptica.

---

## 🍏 2. Pasos para compilar en Xcode y subir a la App Store

Para generar el archivo ejecutable de iOS que se sube a Apple Developer / App Store Connect:

### Requisito previo en tu Mac:
1. Instalar **Node.js**: Descárgalo gratis desde [nodejs.org](https://nodejs.org) (versión LTS).
2. Instalar **Xcode**: Descárgalo gratis desde la **Mac App Store**.

### Comandos de compilación:
Desde la terminal en esta carpeta (`/Users/nicopazos/.gemini/antigravity/scratch/encuentros-app`):

```bash
# 1. Instalar las dependencias de Capacitor
npm install

# 2. Generar el proyecto de Xcode
npx cap add ios

# 3. Sincronizar los archivos web con la app nativa
npx cap sync ios

# 4. Abrir el proyecto en Xcode
npx cap open ios
```

Una vez en Xcode:
1. Conecta tu iPhone por cable o selecciona un simulador de iPhone.
2. Pulsa el botón **Play (▶)** para instalar la app en tu teléfono.
3. Para publicar, ve al menú superior: **Product > Archive** y sigue el asistente para subirlo a tu cuenta de **Apple Developer**.

---

## ✅ 3. Requisitos de Apple ya incluidos en este código

Para evitar que los revisores de Apple rechacen la aplicación, ya hemos integrado:

1. **Permiso de Cámara (`NSCameraUsageDescription`):** Configurado en `Info.plist` con la justificación requerida por Apple.
2. **Botón de Eliminación de Cuenta y Datos:** Cumple la directriz obligatoria *App Store Review Guideline 5.1.1(v)* (disponible en la pestaña *Perfil > Privacidad*).
3. **Aviso de Política de Privacidad:** Modal integrado con el desglose de uso de cámara y datos.
4. **Cumplimiento de exportación (`ITSAppUsesNonExemptEncryption: false`):** Evita trámites burocráticos de encriptación al subir la app.
