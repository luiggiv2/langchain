# Creación de un RAG utilizando la integración de LangChain con OpenAI

A continuación se detalla un pequeño manual para la construcción y actualización de una aplicación RAG (Retrieval Augmented Generation), basados en la guía de tutoriales de LangChain. Se detalla a continuación la siguiente arquitectura propuesta.

<img width="779" alt="Captura de pantalla 2024-12-09 a la(s) 12 30 49" src="https://github.com/user-attachments/assets/7232d847-6eb1-4a33-904a-cbf8218b70d4">

## Pre requisitos
  - Python 3.11
  - Editor de código, en este tutorial se utilizó VS Code.
  - Una clave API de OpenAI
  - Una cuenta de Pinecone

## Configuración del entorno

  - Crea un directorio y navega hasta el en la ventana del terminal.
  - Como paso siguiente se debe crear un entorno virtual, este entorno virtual servirá como un espacio aislado para un proyecto específico, permitiendo gestionar las dependencias de forma independiente.

    ```
    python3.11 -m venv nombre_entorno #"Nombre de entorno que deseas crear/nombrar"
    ```

La creación de entornos virtuales es una práctica recomendada en el desarrollo de aplicaciones Python, ya que ayuda a mantener una mejor organización y a evitar problemas de compatibilidad entre diferentes proyectos.

Una vez creado el entorno virtual, puedes activarlo utilizando un comando específico (que varía según el sistema operativo). Por ejemplo, en sistemas basados en Unix, se suele usar:

```
source nombre_entorno/bin/activate
```

Al activar el entorno virtual, se modifican algunas variables de entorno para que Python busque los paquetes instalados dentro del entorno virtual en lugar de los instalados globalmente.

Posterior a ello se debe realizar la instalación de paquetes necesarios para el entorno de trabajo.

```
pip install langchain openai
```

Al ejecutar este comando, se estará dotando el entorno de Python con las herramientas necesarias para construir aplicaciones de inteligencia artificial que interactúen con el lenguaje de manera efectiva, aprovechando la potencia de los modelos de lenguaje de OpenAI.

## Contrucción de aplicación RAG

Para la creación de la aplicación, realiza el seguimiento del tutorial [Build a Retrieval Augmented Generation (RAG) App: Part 1](https://python.langchain.com/docs/tutorials/rag/) <br>
En esta sección se hará uso de la clave API de OpenAI para que se pueda interactuar con el modelo GPT. <br>

El tutorial mostrará cómo crear una simple aplicación de preguntas y respuestas sobre una fuente de datos de texto. Se verá cómo LangSmith puede ayudar a rastrear y comprender la aplicación.

Una aplicación **RAG** típica tiene dos componentes principales:

  - `Indexación` un canal para ingerir datos de una fuente e indexarlos.
  - `Recuperación y generación` la cadena RAG real, que toma la consulta del usuario en tiempo de ejecución y recupera los datos relevantes del índice, para luego pasarlos al modelo.

## Actualización de la app RAG  para realizar el uso  de Pinecone

Para la integración de Pinecone, se debe instalar el cliente de Pinecone

```
pip install pinecone-client
```

Este paquete proporciona una interfaz para interactuar con la base de datos vectorial Pinecone desde Python. Pinecone es una base de datos diseñada para almacenar y buscar vectores numéricos de alta dimensión, lo que la hace ideal para aplicaciones de búsqueda semántica, recomendación y otras tareas de inteligencia artificial que requieren la comprensión de relaciones entre datos.

Para este paso se debe crear e iniciar sesión en la cuenta Pinecone y generar una Clave API.

Para integrar Pinecone con LangChain, realiza el seguimiento del tutorial [Pinecone](https://python.langchain.com/docs/integrations/vectorstores/pinecone/)<br>

  - En esta sección se inicializará una conexión con pinecone utilizando la API_KEY.
  - Se configurará el almacenamiento de incrustaciones generados por OpenAI.
  - Se actualizará la lógica de recuperación a consultar Pinecone y generar respuestas más relevantes.
