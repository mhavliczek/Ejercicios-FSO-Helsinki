sequenceDiagram
    participant navegador
    participant servidor

    Note right of navegador: El usuario navega a https://studies.cs.helsinki.fi/exampleapp/spa

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate servidor
    servidor-->>navegador: Documento HTML
    deactivate servidor

    Note right of navegador: El navegador comienza a cargar el HTML de la SPA

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate servidor
    servidor-->>navegador: Archivo CSS
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate servidor
    servidor-->>navegador: Archivo JavaScript de la SPA
    deactivate servidor

    Note right of navegador: El navegador ejecuta el archivo spa.js que maneja la lógica de la SPA

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: [{ "content": "HTML es fácil", "date": "2023-1-1" }, ... ]
    deactivate servidor

    Note right of navegador: El navegador renderiza las notas usando los datos recibidos
