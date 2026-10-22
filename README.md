# Mi Espacio — organizador escolar personal

Aplicación web en español para organizar tareas, exámenes, calendario, hábitos, sesiones de estudio, notas y horario. Diseño adaptable a móvil, tablet y ordenador. No requiere cuenta, API de pago ni instalación de dependencias.

## Qué incluye

- **Mi día:** bienvenida personalizable, tareas de hoy, próximos eventos, hábitos, logros con estrellas y próxima clase.
- **Configuración inicial:** la primera vez solicita el nombre preferido y permite elegir entre rosa palo, rosa palo con purpurina, azul claro, verde claro, beige o morado.
- **Estantería de asignaturas:** libros visuales por materia, con opción de adjuntar archivos y guardar resúmenes escritos. Los documentos se guardan localmente en el navegador.
- **Tarjetas de repaso:** crea tarjetas de pregunta y respuesta para practicar conceptos, fechas y personajes.
- **Modo concentración:** reduce las distracciones visuales y permite activar un sonido ambiente generado en el dispositivo.
- **Calendario mensual:** cuadrícula real de lunes a domingo. Los eventos se alimentan de la misma lista de tareas y exámenes; no se duplican.
- **Tareas y exámenes:** tipos, asignatura, fecha, hora, prioridad, estado, búsqueda y filtros.
- **Hábitos:** registros independientes por fecha, historial y racha aproximada.
- **Modo estudio:** temporizador con pausa/reanudación, duración personalizada, recuperación tras recargar, sesiones guardadas y ajustes Pomodoro.
- **Registro de notas:** diferentes escalas, equivalencia normalizada sobre 10 y medias por asignatura.
- **Progreso:** estadísticas y gráficos derivados de los datos registrados.
- **Mi horario:** horario inicial solicitado, editable, con clases, recreo y actividad extraescolar diferenciados.
- **Ajustes:** nombre, frase, tema, preferencias y configuración Pomodoro.
- **Copias de seguridad:** exportación e importación JSON validadas, con confirmación antes de reemplazar datos.

## Cómo abrirla en el ordenador

1. Descomprime `mi-espacio.zip`.
2. Abre la carpeta `mi-espacio`.
3. Haz doble clic en `index.html` para abrirla en un navegador moderno.

Para una experiencia más fiable, especialmente con permisos de notificación o despliegue, usa un servidor local.

### Servidor local opcional

Si tienes Python 3 instalado:

1. Abre una terminal dentro de la carpeta `mi-espacio`.
2. Ejecuta `python -m http.server 8000`.
3. Abre `http://localhost:8000` en el navegador.

No hay paquetes que instalar. También puedes usar la extensión Live Server de VS Code si ya la utilizas.

## Publicar en internet

La aplicación es estática y puede publicarse en GitHub Pages o Vercel:

### GitHub Pages
1. Crea un repositorio nuevo en GitHub.
2. Sube los archivos de esta carpeta (incluido `index.html` en la raíz publicada).
3. En el repositorio, abre **Settings → Pages**.
4. Selecciona la rama y la carpeta raíz como fuente de publicación.
5. Espera a que GitHub muestre la URL HTTPS asignada. No hay una URL pública hasta que completes este paso.

### Vercel
1. Importa el repositorio desde Vercel o sube el proyecto mediante el flujo disponible en su panel.
2. No configures un comando de compilación ni una carpeta de salida especial: es una web estática.
3. Publica y utiliza la URL HTTPS que te proporcione Vercel.

## Abrir la web con una etiqueta NFC

1. Publica primero la web y copia la URL pública HTTPS.
2. En un móvil compatible, abre una aplicación de escritura NFC de confianza.
3. Selecciona crear un registro de tipo **URL/enlace** y pega la dirección HTTPS publicada.
4. Acerca la etiqueta NFC al móvil para escribir el enlace y verifica la escritura.
5. Después, al acercar un móvil compatible a la etiqueta, se podrá abrir la página.

La etiqueta solo contiene el enlace web. **No guarda tus tareas, notas, hábitos ni el resto de los datos**, y no sincroniza información entre dispositivos.

## Dónde se guardan los datos

Los datos (incluidos los adjuntos de la estantería) se guardan en `localStorage` del navegador y dispositivo donde usas la aplicación. Los adjuntos grandes pueden alcanzar el límite de almacenamiento del navegador; si sucede, reduce su tamaño o guarda una copia externa. No se envían a un servidor ni se sincronizan automáticamente. Si borras los datos del navegador, puedes perder la información; exporta copias JSON con regularidad. Para usar los mismos datos en otro dispositivo, exporta en el primero y luego importa el archivo en el segundo.

## Copias de seguridad

- En **Ajustes y copias de seguridad → Exportar JSON** se descarga una copia completa, incluidos los datos de la estantería y sus archivos adjuntos.
- Para restaurar, elige **Importar una copia** y selecciona el archivo JSON.
- La aplicación valida la estructura básica y solicita confirmación porque la importación reemplaza los datos actuales.
- Guarda una copia reciente antes de importar o borrar datos.

## Restaurar el horario inicial

En **Mi horario → Restaurar original**, o en **Ajustes y copias de seguridad → Restaurar horario**, se recuperan las clases y horas iniciales. Las tareas, notas, hábitos y sesiones no se borran.

## Limitaciones conocidas

- El almacenamiento es local por navegador/dispositivo; no hay cuenta ni sincronización en la nube.
- Los recordatorios dentro de la página se muestran al consultar la aplicación. Las notificaciones del navegador son opcionales y requieren permiso; una web estática no garantiza avisos cuando el navegador está cerrado.
- No se programa una etiqueta NFC desde la aplicación: solo se puede guardar en ella la URL publicada.
- El tiempo del temporizador se calcula con marcas de tiempo y puede recuperarse tras una recarga. El navegador o el sistema operativo pueden limitar temporizadores y notificaciones en segundo plano.
- Los gráficos son sencillos y se generan a partir de los registros locales; no hay calificaciones, tareas ni eventos escolares ficticios precargados. Los hábitos sugeridos son ejemplos editables.
- El tema usa una fuente web externa si hay conexión; el resto de la aplicación funciona sin dependencias externas.

## Privacidad

No se piden contraseñas ni credenciales. Como los datos se guardan en el navegador local, evita utilizar la aplicación en un perfil compartido si quieres mantener tu información privada.


## Preparación PWA para iPhone

Esta versión incluye `manifest.webmanifest`, `service-worker.js`, registro del service worker e iconos para la pantalla de inicio.

1. Publica el contenido de esta carpeta en tu proyecto de Vercel, manteniendo `index.html` en la raíz publicada.
2. Abre la URL HTTPS en Safari en el iPhone.
3. Pulsa **Compartir → Añadir a pantalla de inicio**. Si aparece la opción **Abrir como app**, actívala.
4. Prueba las funciones con y sin conexión antes de depender del modo sin conexión.

Nota: la PWA guarda los datos en el almacenamiento local del navegador. Esta preparación no convierte la web en una app de la App Store ni sincroniza automáticamente los datos entre dispositivos. Revisa también que el proyecto publicado sea la versión correcta antes de reemplazar la web actual.
