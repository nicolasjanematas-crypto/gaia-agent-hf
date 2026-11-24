# gaia-agent-hf

Agente para el reto GAIA de la **Unidad 4 del curso [Hugging Face Agents Course](https://huggingface.co/learn/agents-course/en/unit4/hands-on)**, construido con [smolagents](https://github.com/huggingface/smolagents) (`CodeAgent` + `LiteLLMModel`).

Responde las 20 preguntas del nivel 1 del benchmark [GAIA](https://huggingface.co/datasets/gaia-benchmark/GAIA) que el curso sirve a través de su API de scoring, usando herramientas de búsqueda web, lectura de páginas y lectura de archivos adjuntos (xlsx, pdf, imágenes, audio).

## Archivos

- `HF_Agents_Unidad4_Reto_GAIA.ipynb` — cuaderno completo de Google Colab con el pipeline: descarga de preguntas, ground truth del dataset público de GAIA para validación local, descarga de adjuntos, herramientas, agente, evaluación y envío al leaderboard.

## Herramientas del agente

| Herramienta | Qué hace |
|---|---|
| `buscar_web` | Búsqueda web (Tavily o DuckDuckGo) |
| `visitar_url` | Lee el texto de una página web |
| `descargar_archivo` | Descarga adjuntos de las preguntas |
| `leer_archivo` | Lee txt/csv/json/xlsx/pdf, describe imágenes (Gemini visión) y transcribe audio (Groq Whisper) |

## Cómo ejecutarlo

1. Abrir el notebook en Google Colab.
2. Configurar las claves en el Paso 1: `GEMINI_API_KEY`, `OPENAI_API_KEY`, opcionales `GROQ_API_KEY`, `TAVILY_API_KEY`.
3. Aceptar las condiciones del dataset GAIA y crear un token de lectura de Hugging Face (Paso 3).
4. Ejecutar los pasos en orden; el Paso 7 compara modelos y el Paso 8 corre las 20 preguntas.
5. El Paso 9 calcula la nota en local (comparación exacta `strip().lower()` contra el dataset público, igual que el servidor) y el Paso 10 envía al leaderboard del curso.

## Resultado

Score local del agente con GPT-4o: **9/20 (45%)** tras correcciones de formato — por encima del 30% requerido para el certificado del curso.

## Nota

Las 20 preguntas pertenecen a la partición de validación pública de GAIA, por lo que el cuaderno permite validar en local antes de enviar. Proyecto con fines educativos para el curso de Hugging Face.
