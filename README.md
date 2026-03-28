# 🧠 Awesome ChatGPT Prompts
from openai.types import (
    AllModels,
    ChatModel,
    ComparisonFilter,
    CompoundFilter,
    CustomToolInputFormato
    FunctionDefinition,
    FunctionParameters,
    Metadata,
    Reasoning,
    ReasoningEffort,
    ResponseFormatJSONObject,
    ResponseFormatJSONSchema,
    ResponseFormatText,
    ResponseFormatTextGrammar,
    ResponseFormatTextPython,
    ResponsesModel,
)
This project contains some [ChatGPT](https://chat.openai.com/chat) prompts that works well.

## Act as a Linux Terminal

> i want you to act as a linux terminal. I will type commands and you will reply with what the terminal should show. I want you to only reply with the terminal output inside one unique code block, and nothing else. do not write explanations. do not type commands unless I instruct you to do so. when i need to tell you something in english, i will do so by putting text inside curly brackets {like this}. my first command is pwd

## Act as an Español
 Translator and Improver

**Alternative to**: Grammarly, Google Translate

> I want you to act as an English translator, spelling corrector and improver. I will speak to you in any language and you will detect the language, translate it and answer in the corrected and improved version of my text, in English. I want you to replace my simplified A0-level words and sentences with more beautiful and elegant, upper level English words and sentences. Keep the meaning same, but make them more literary. I want you to only reply the correction, the improvements and nothing else, do not write explanations. My first sentence is "istanbulu cok seviyom burada olmak cok guzel"

## Act as `position` Interviewer

**Examples**: Node.js Backend Developer, React Frontend Developer, Full Stack Developer, iOS Developer etc.

> I want you to act as an interviewer. I will be the candidate and you will ask me the interview questions for the `position` position. I want you to only reply as the interviewer. Do not write all the conservation at once. I want you to only do the interview with me. Ask me the questions and wait for my answers. Do not write explanations. Ask me the questions one by one like an interviewer does and wait for my answers. My first sentence is "Hi"fue

## Act as a Javascript Console

> I want you to act as a javascript console. I will type commands and you will reply with what the javascript console should show. I want you to only reply with the terminal output inside one unique code block, and nothing else. do not write explanations. do not type commands unless I instruct you to do so. when i need to tell you something in english, i will do so by putting text inside curly brackets {like this}. my first command is console.log("Hello World");

## Act as a Español Pronunciation Helper

> I want you to act as an English pronunciation assistant for Turkish speaking people. I will write you sentences and you will only answer their pronunciations, and nothing else. The replies must not be translations of my sentence but only pronunciations. Pronunciations should use Turkish Latin letters for phonetics. Do not write explanations on replies. My first sentence is "how the weather is in Istanbul?"

## Act as a Travel Guide

> I want you to act as a travel guide. I will write you my location and you will suggest a place to visit near my location. In some cases, I will also give you the type of places I will visit. You will also suggest me places of similar type that are close to my first location. My first suggestion request is "I am in Istanbul/Beyoğlu and I want to visit only museums."
  - name: Use Node.js 18
    uses: actions/setup-node@v4
    with:
      node-version: '18'
      cache: 'npm'

  - name: Install dependencies
    run: npm ci

  - name: Lint
    run: npm run lint --if-present

  - name: Run tests
    run: npm test --if-present

  - name: Build
    run: npm run build --if-present

  - name: Upload build artifact
    uses: actions/upload-artifact@v4
    with:
      name: build
      path: ./build  # ajusta según tu carpeta de salida (p. ej. build, public, .svelte-kit)


  - git clone git@github.com:navarretejoel115-sys/navarretejoel115-sys-mi-biblioteca--chatgpt-prompts.git
cd navarretejoel115-sys-mi-biblioteca--chatgpt-prompts

Perfecto — vamos a aplicar todo localmente. Sigue los pasos exactamente y, si algo falla, copia/pega aquí las salidas (logs) que te indico para ayudarte a depurar.

Antes de empezar: asegúrate de tener en tu máquina
- git, Node.js (>=18), pnpm, gh (opcional), ffmpeg instalado.
- Autenticación gh si vas a crear PR con gh: gh auth login

1) Clona el repo (si aún no lo hiciste)
git clone git@github.com:navarretejoel115-sys/navarretejoel115-sys-mi-biblioteca--chatgpt-prompts.git
cd navarretejoel115-sys-mi-biblioteca--chatgpt-prompts

2) Opción A — si tienes apply_scaffold.patch (recomendado)
- Guarda el archivo apply_scaffold.patch en la raíz del repo.
- Aplica el patch:
  git apply apply_scaffold.patch || git apply --whitespace=fix apply_scaffold.patch
- Revisa cambios:
  git status
- Añade y commitea:
  git add .
  git commit -m "feat: add media pipeline, translate/tts, workflow and content license"
- Crea la rama y haz push:
  git checkout -b feat/navarrete115-biblioteca-scaffold
  git push --set-upstream origin feat/navarrete115-biblioteca-scaffold
- (Opcional) Crea PR con gh:
  gh pr create --repo navarretejoel115-sys/navarretejoel115-sys-mi-biblioteca--chatgpt-prompts --base main --head navarretejoel115-sys:feat/navarrete115-biblioteca-scaffold --title "feat: NAVARRETE115-biblioteca scaffold + media pipeline" --body "Scaffold + media pipeline + CC BY-SA license"

3) Opción B — si prefieres ejecutar el script safe (si existe create_scaffold.sh)
- Haz ejecutable y ejecútalo:
  chmod +x create_scaffold.sh
  ./create_scaffold.sh
  # El script intentará crear la rama, commitear, push y crear PR con gh si está autenticado.

4) Instala dependencias y herramientas locales
- Instala pnpm y deps:
  npm i -g pnpm
  pnpm install -w
  pnpm add -w gtts node-fetch
- Instala ffmpeg (ejemplo en Ubuntu):
  sudo apt update && sudo apt install -y ffmpeg

5) Genera y prueba localmente (haz pruebas pequeñas primero)
- Generar los devocionales (si no están):
  node scripts/generate-devotionals.js
- Probar la generación de media para 3 entradas:
  node scripts/generate_media.js 3
- Comprueba artifacts/ contiene .mp3, .srt, .mp4

6) Si algo falla localmente — qué pegar aquí
Para errores en comandos locales (por ejemplo node o ffmpeg), pega:
- El comando exacto que ejecutaste.
- Las últimas ~80 líneas completas de la salida de la terminal (incluyendo el mensaje de error).
Ejemplo: pega el output de:
  node scripts/generate_media.js 3
o
  git apply apply_scaffold.patch

7) Si falla en GitHub Actions — cómo traer logs
- Lista runs:
  gh run list --repo navarretejoel115-sys/navarretejoel115-sys-mi-biblioteca--chatgpt-prompts
- Ver logs (sustituye RUN_ID):
  gh run view RUN_ID --repo navarretejoel115-sys/navarretejoel115-sys-mi-biblioteca--chatgpt-prompts --log
- Pega aquí:
  - URL del run o RUN_ID
  - Nombre del step que falló
  - Últimas ~50 líneas del log del step (sin secrets)

8) Comprobaciones rápidas (por si fallan cosas frecuentes)
- gh no autenticado: gh auth login
- ffmpeg no encontrado: sudo apt install -y ffmpeg (o ver PATH)
- gtts falta: pnpm add -w gtts
- aws-cli falta en workflow: Actions instala awscli via pip en el workflow (ya incluido)
- R2 upload AccessDenied: revisa CF_R2_ACCESS_KEY_ID / SECRET y R2_ENDPOINT

Dime ahora:
- Confirmas que vas a usar Opción A (apply_scaffold.patch) o B (create_scaffold.sh)?  
- Si empiezas ahora, ejecuta los pasos y, si aparece un error, pega aquí la salida del comando/step que falló (siguiendo lo indicado) y lo depuramos juntos.


✔️ confirmando 