sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user has already loaded the SPA from https://studies.cs.helsinki.fi/exampleapp/spa

    Note right of browser: The user types a note and clicks the "Save" button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: The server receives the note in JSON format and stores it
    server-->>browser: 201 Created (without reloading the page)
    deactivate server
