sequenceDiagram
    participant navegador
    participant servidor

    Note right of navegador: El usuario escribe una nueva nota en el campo de texto y hace clic en el botón Guardar

    navegador->>servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate servidor
    servidor-->>navegador: Confirmación de recepción (status 201 Created)
    deactivate servidor

    Note right of navegador: El navegador actualiza la lista de notas sin recargar la página

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: [{ "content": "HTML es fácil", "date": "2024-1-1" }, { "content": "Nueva nota", "date": "2024-06-02" }, ... ]
    deactivate servidor

    Note right of navegador: El navegador renderiza las notas incluyendo la nueva nota creada
