---
name: hyperframes-setup
description: Instala o verifica HyperFrames (HTML a video, de HeyGen) en el contenedor de la sesión solo cuando se invoca. Úsala cuando el usuario escriba /hyperframes-setup, pida "instala hyperframes" o necesite crear videos con HyperFrames en un chat nuevo donde el comando no existe.
---

# HyperFrames setup (bajo demanda)

Solo corre cuando el usuario la llama. No instala nada al iniciar la sesión.

## Pasos

1. Verifica si ya está instalado:

   ```bash
   command -v hyperframes && hyperframes --version
   ```

2. Si no existe, instálalo (Node 22+ y ffmpeg deben estar disponibles):

   ```bash
   npm install -g hyperframes
   ```

3. Comprueba el entorno y reporta faltantes opcionales (whisper, Kokoro, MusicGen no son necesarios para renderizar):

   ```bash
   hyperframes doctor
   ```

4. Para tener las skills oficiales (`hyperframes`, `hyperframes-cli`, `hyperframes-registry`, `media-use`), crea un proyecto: `hyperframes init <nombre> --non-interactive`. Las skills se cargan al reiniciar o en el siguiente turno.

5. Informa al usuario: versión instalada, resultado de `doctor`, y que la telemetría de uso se desactiva con `hyperframes telemetry disable`.

## Notas

- El contenedor de la nube es temporal: la instalación no persiste entre sesiones. Por eso existe esta skill.
- Render de prueba: `hyperframes render -o out.mp4` dentro de un proyecto (usa captura por screenshot, más lenta, si no hay chrome-headless-shell).
- Referencia: https://hyperframes.heygen.com
