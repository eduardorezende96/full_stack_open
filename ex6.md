sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes new note via forms and clicks "Save" button
    
    browser->>server: POST /exampleapp/new_note (note=Nova Nota)
    activate server
    Note right of server: O servidor salva a nova nota
    server-->>browser: Resposta com notas atualizadas em JSON
    deactivate server

    Note right of browser: O navegador (SPA) atualiza a lista de notas dinamicamente
    browser->>server: GET /exampleapp/data.json
    activate server
    server-->>browser: Lista atualizada de notas em JSON
    deactivate server

    Note right of browser: Browser renders new notes list
