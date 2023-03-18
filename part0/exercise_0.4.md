sequenceDiagram
	participant browser
	participant server

	browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
	activate server
	server-->>browser: HTTP Status code 302 
	deactivate server

	Note right of browser: Browser performs URL redirect

	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
	activate server
	server-->>browser: document (notes)
	deactivate server

	Note right of browser: Browser reloads the page

	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
	activate server
	server-->>browser: CSS file
	deactivate server

	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
	activate server
	server-->>browser: JavaScript file
	deactivate server

	Note right of browser: Browser executes code in main.js to retrieve the notes data (JSON).

	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
	activate server
	server-->>browser: [{"content": "", "date": ""},...]
	deactivate server

	Note to the right of browser: Browser executes event handler to render the notes to display 

