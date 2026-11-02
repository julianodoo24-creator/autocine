# AutoCine

Reproductor de video para iPhone (iOS 17 o posterior):

- **Listas M3U / M3U8**: pega un enlace, se leen grupos, logos y nombres. Búsqueda, filtro por grupo y favoritos.
- **Jellyfin y Emby**: inicia sesión en tu servidor, navega bibliotecas, series, temporadas y episodios (ordenados). El servidor convierte MKV, HEVC o DTS si hace falta.
- **Tus videos**: impórtalos desde Archivos o Fotos y míralos sin conexión.
- **Sigue donde lo dejaste** en películas y episodios.
- **AirPlay** y vista horizontal con el reproductor nativo de iOS.
- Sin cuenta: todo se guarda en el iPhone.

> ⚠️ **CarPlay**: Apple no permite apps de video en CarPlay. Una app instalada sin App Store no puede pedir ese permiso, así que AutoCine **no aparecerá en la pantalla del auto**. Funciona en el iPhone y por AirPlay (por ejemplo, a una tele o a un adaptador AirPlay).

---

## Instalarla desde Windows (sin Mac)

Una sola vez:

1. **Sube el proyecto a GitHub**
   - Crea una cuenta en github.com y un repositorio nuevo (por ejemplo `autocine`).
   - Pulsa *uploading an existing file* y arrastra **todo el contenido** de esta carpeta, incluida la carpeta oculta `.github`.
     Si no la ves, actívala en el Explorador: *Vista → Mostrar → Elementos ocultos*.
2. **Descarga la app compilada**
   - En el repositorio, ve a la pestaña **Actions**. Verás "Compilar IPA" en marcha (tarda unos 5 minutos).
   - Cuando tenga el ✅, ábrelo y descarga **AutoCine-ipa**. Descomprime el zip: dentro está `AutoCine.ipa`.
3. **Prepara el PC**
   - Instala **iTunes** (desde apple.com, no la versión de Microsoft Store) e **iCloud** para Windows.
   - Instala **Sideloadly** (sideloadly.io).
4. **Instala en el iPhone**
   - Conecta el iPhone por cable y toca *Confiar en este ordenador*.
   - Abre Sideloadly, arrastra `AutoCine.ipa`, escribe tu Apple ID y pulsa **Start**.
5. **Activa la app en el iPhone**
   - *Ajustes → Privacidad y seguridad → Modo de desarrollador* → activar y reiniciar.
   - *Ajustes → General → VPN y gestión de dispositivos* → toca tu Apple ID → **Confiar**.

**Importante:** con un Apple ID gratuito la app caduca a los **7 días**. Para renovarla, vuelve a pasar el mismo `.ipa` por Sideloadly (no pierdes tus listas). Con la cuenta de desarrollador de Apple (99 $/año) dura 1 año.

## Si tienes un Mac

```bash
brew install xcodegen
cd AutoCine
xcodegen generate
open AutoCine.xcodeproj
```

En Xcode: *Signing & Capabilities → Team* → elige tu Apple ID, conecta el iPhone y pulsa ▶.

## Estructura

| Archivo | Qué hace |
|---|---|
| `Sources/AutoCineApp.swift` | Arranque y pestañas |
| `Sources/Models.swift` | Datos y lector de listas M3U |
| `Sources/Store.swift` | Guardado de listas, servidores y favoritos |
| `Sources/PlaylistViews.swift` | Pantallas de listas, canales y favoritos |
| `Sources/MediaServer.swift` | Conexión con Jellyfin / Emby |
| `Sources/LocalVideos.swift` | Videos importados |
| `Sources/Player.swift` | Reproductor y "seguir donde lo dejaste" |
| `project.yml` | Configuración del proyecto (XcodeGen) |
| `.github/workflows/build.yml` | Compilación automática en GitHub |
