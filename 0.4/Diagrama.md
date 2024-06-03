sequenceDiagram
    participant navegador
    participant servidor

    Note right of navegador: El usuario escribe una nota en el campo de texto y hace clic en el botón Guardar

    navegador->>servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate servidor
    servidor-->>navegador: Redirigir a /notes
    deactivate servidor

    Note right of navegador: El navegador redirige a /notes y recarga la página

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate servidor
    servidor-->>navegador: Documento HTML
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate servidor
    servidor-->>navegador: Archivo CSS
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate servidor
    servidor-->>navegador: Archivo JavaScript
    deactivate servidor

    Note right of navegador: El navegador comienza a ejecutar el código JavaScript que obtiene el JSON del servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: [{ "content": "HTML es fácil", "date": "2024-1-1" }, ... ]
    deactivate servidor

   %% Nota: El navegador ejecuta las notas
