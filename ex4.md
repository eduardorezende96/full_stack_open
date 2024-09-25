sequenceDiagram
    participant browser
    participant server

    Note right of browser: O usuário escreve uma nova nota e clica em "Save" no formulário
    
    browser->>server: POST /exampleapp/new_note (note=Nova Nota)
    activate server
    Note right of server: O servidor processa e armazena a nova nota
    server-->>browser: Redireciona para /exampleapp/notes
    deactivate server
    
    browser->>server: GET /exampleapp/notes
    activate server
    server-->>browser: HTML document (atualizado)
    deactivate server

    browser->>server: GET /exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "Nova nota", "date": "2024-09-25" }, ... ]
    deactivate server

    Note right of browser: O navegador renderiza as notas atualizadas
