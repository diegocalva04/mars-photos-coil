# Mars Photos — Coil y cuadrícula de imágenes

Continuación de Mars Photos para el codelab oficial [Cómo cargar y mostrar imágenes de Internet](https://developer.android.com/codelabs/basic-android-kotlin-compose-load-images?hl=es-419). La aplicación Kotlin con Jetpack Compose carga fotografías remotas con Coil, usa `AsyncImage` con estados de carga y error, y presenta la colección en una cuadrícula adaptable.

Este repositorio público e independiente conserva el historial Git del proyecto anterior de Mars Photos. La rama `main` contiene los avances progresivos de Coil y no modifica el repositorio anterior.

## Implementación

- Coil `2.4.0` y `AsyncImage` con `ImageRequest`, `LocalContext`, transición y descripción accesible.
- `ContentScale.Crop` para adaptar la imagen a la pantalla en orientación vertical y horizontal.
- Recursos existentes `loading_img` e `ic_broken_image` conectados como placeholder y error.
- `LazyVerticalGrid` con `GridCells.Adaptive(150.dp)`, claves basadas en `photo.id` y tarjetas con proporción `1.5f`.
- Pantalla de error con acción `Retry` conectada a `MarsViewModel.getMarsPhotos()`.
- Vista previa de Compose con los datos ficticios indicados por el codelab.

## Verificación

Se ejecutaron `testDebugUnitTest`, `assembleDebug` y `lintDebug`; las tres tareas terminaron correctamente. Las tres pruebas unitarias presentes pasaron: una prueba de ejemplo previa, la prueba del repositorio y la prueba actualizada de `MarsViewModel`. No se ejecutaron pruebas instrumentadas.

La aplicación se ejecutó en un teléfono Xiaomi 23100RN82L con Android 15/API 35. Se comprobaron la respuesta de la API, la cuadrícula, las orientaciones vertical y horizontal, el error de imágenes sin conexión y la recuperación mediante `Retry`. Las imágenes ya cargadas permanecieron disponibles por la caché; las solicitudes nuevas sin red mostraron el recurso de error.

## Evidencias

| Resultado | Captura |
| --- | --- |
| Estado inicial | [01-estado-inicial](docs/evidencias/01-estado-inicial.png) |
| URL de la primera fotografía | [02-url-primera-foto](docs/evidencias/02-url-primera-foto.png) |
| Primera imagen mediante Coil | [03-primera-fotografia-coil](docs/evidencias/03-primera-fotografia-coil.png) |
| `ContentScale.Crop`, vertical y horizontal | [04 vertical](docs/evidencias/04-recorte-vertical.png), [05 horizontal](docs/evidencias/05-recorte-horizontal.png) |
| Cuadrícula adaptable | [06-cuadricula-fotografias](docs/evidencias/06-cuadricula-fotografias.png) |
| Cuadrícula con tarjetas | [07-cuadricula-tarjetas](docs/evidencias/07-cuadricula-tarjetas.png) |
| Error de imágenes en modo avión | [08-cuadricula-modo-avion](docs/evidencias/08-cuadricula-modo-avion.png) |
| Pantalla de error y recuperación con Retry | [09 pantalla de error](docs/evidencias/09-pantalla-error-reintento.png), [10 recuperación](docs/evidencias/10-reintento-recupera-cuadricula.png) |`n| Pruebas unitarias de Gradle | [11-resultados-pruebas-unitarias](docs/evidencias/11-resultados-pruebas-unitarias.png) |`n| Repositorio y commits públicos | [13 vista pública](docs/evidencias/13-repositorio-github-publico.png), [12 historial](docs/evidencias/12-historial-github.png) |

El desarrollo y los commits están disponibles en [GitHub: diegocalva04/mars-photos-coil](https://github.com/diegocalva04/mars-photos-coil). Consulta el [historial por etapas](docs/HISTORIAL.md) y el [registro de validación](docs/VALIDACION.md).

## Compilar

Abrir esta carpeta en Android Studio y permitir la sincronización de Gradle. Para compilar desde PowerShell:

```powershell
.\gradlew.bat :app:assembleDebug
.\gradlew.bat :app:testDebugUnitTest
```

Se requiere Android SDK 37 y la configuración JDK incluida con Android Studio para el wrapper de este proyecto. El APK de depuración se genera en `app/build/outputs/apk/debug/app-debug.apk`.
