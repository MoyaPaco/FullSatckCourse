'''mermaid
sequenceDiagram
participant browser
participant server

Note right of browser: The user types a new note in the text field and clicks "Save"

Note right of browser: The browser prevents the default behavior of the form

Note right of browser: A JavaScript object is created with the note's content and the current date

browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note (data in x-www-form-urlencoded format)
activate server
Note right of server: The server receives the data and stores it in a database or memory
server-->>browser: HTTP 302 redirect to /exampleapp/notes
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
activate server
server-->>browser: HTML document
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser: the CSS file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
activate server
server-->>browser: the JavaScript file
deactivate server

Note right of browser: The browser executes the JavaScript that requests the notes in JSON format

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
server-->>browser: JSON list with all notes, including the new one
deactivate server

