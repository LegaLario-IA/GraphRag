**Proyecto de Prueba - GraphRAG**

Este repositorio contiene un proyecto de prueba para implementar GraphRAG, una solución para generación de preguntas y recuperación de datos a partir de un gráfico de conocimiento construido mediante un LLM. En este caso, seguiremos los pasos necesarios para configurar y ejecutar una pipeline básica de indexación y consulta de datos usando GraphRAG.

**Requisitos**
Python versión 3.10 o superior.

GraphRAG instalado a través de pip (o desde la fuente):

**Instalación**

Instala los paquetes necesarios:
pip install graphrag


pip install -r requirements.txt
Crea el directorio para los datos de entrada:

mkdir -p ./ragtest/input
Agregar un texto de ejemplo (como un acta constitutiva o poder notarial):



Configuración
Inicializa tu proyecto con el siguiente comando:

python -m graphrag.index --init --root ./ragtest
Esto generará dos archivos en el directorio ./ragtest: .env y settings.yaml.

Abre el archivo .env y añade tu clave API de OpenAI o Azure OpenAI:

GRAPHRAG_API_KEY=<tu_clave_api>
Configura las opciones de settings.yaml según sea necesario (ej., ajustar el modelo de LLM si usas Azure).

Ejecutar la Pipeline de Indexación
Para ejecutar el pipeline y generar las entidades y relaciones a partir del texto, usa el siguiente comando:


python -m graphrag.index --root ./ragtest
Esto procesará el texto de entrada y generará archivos de salida en ./ragtest/output/<timestamp>/artifacts.

Consultas con el Motor de Búsqueda
Puedes realizar consultas a los datos indexados usando el motor de consultas de GraphRAG. Aquí hay dos ejemplos:

Búsqueda Global:

python -m graphrag.query --root ./ragtest --method global "¿Cual es el objeto social de esta acta constitutiva?"
Búsqueda Local:


python -m graphrag.query --root ./ragtest --method local "¿Cuales son las partes y cuáles son sus relaciones en el docuemnto?"

**Más información:**
https://microsoft.github.io/graphrag/
https://github.com/microsoft/graphrag
https://www.microsoft.com/en-us/research/blog/graphrag-unlocking-llm-discovery-on-narrative-private-data/
