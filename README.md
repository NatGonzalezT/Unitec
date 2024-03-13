# Unitec
Corporación universitaria Unitec
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal de Comunicación Universitaria</title>
    <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;700&display=swap" rel="stylesheet"> <!-- Fuente IBM -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/5.10.0/main.min.css" rel="stylesheet"> <!-- Estilos FullCalendar -->
    <style>
        body {
            font-family: 'IBM Plex Sans', sans-serif;
            background-color: #f0f6ff; /* Azul claro */
            color: #333; /* Color de texto oscuro */
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #2d2d2d; /* Gris oscuro */
            color: #fff; /* Color de texto blanco */
            padding: 20px;
            text-align: center;
        }
        nav ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
        }
        nav ul li {
            display: inline;
            margin-right: 20px;
        }
        nav ul li a {
            color: #fff; /* Color de texto blanco */
            text-decoration: none;
        }
        main {
            padding: 20px;
        }
        section {
            margin-bottom: 40px;
        }
        h1, h2 {
            color: #007acc; /* Azul */
        }
        footer {
            background-color: #ffb300; /* Amarillo */
            color: #333; /* Color de texto oscuro */
            text-align: center;
            padding: 20px;
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
        }
        #calendario {
            max-width: 800px; /* Ancho máximo del calendario */
            margin: 0 auto; /* Centrar el calendario horizontalmente */
        }
    </style>
</head>
<body>
    <header>
        <h1>Portal Universitario</h1>
        <nav>
            <ul>
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#eventos">Eventos</a></li>
                <li><a href="#foro">Foro</a></li>
                <li><a href="#mensajes">Mensajes</a></li>
                <li><a href="#busqueda">Búsqueda</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section id="eventos">
            <h2>Calendario de Eventos</h2>
            <div id="calendario"></div>
            npm install @fullcalendar/core @fullcalendar/interaction @fullcalendar/daygrid
            import { Calendar } from '@fullcalendar/core'
import interactionPlugin from '@fullcalendar/interaction'
import dayGridPlugin from '@fullcalendar/daygrid'
const calendarEl = document.getElementById('calendar')
const calendar = new Calendar(calendarEl, {
  plugins: [
    interactionPlugin,
    dayGridPlugin
  ],
  initialView: 'timeGridWeek',
  editable: true,
  events: [
    { title: 'Meeting', start: new Date() }
  ]
})
calendar.render()
        </section>
        <section id="foro">
            <h2>Foro de Discusión</h2>
            <div id="disqus_thread"></div>
            <script>
                var disqus_config = function () {
                    this.page.url = window.location.href; // [URL de la página](https://disqus.com/home/)
                    this.page.identifier = 'unique_page_id'; // Identificador único de la página
                };
                (function() { // No modificar el código debajo de esta línea
                    var d = document, s = d.createElement('script');
                    s.src = 'https://@UNITEC_IO.disqus.com/embed.js'; 
                    s.setAttribute('data-timestamp', +new Date());
                    (d.head || d.body).appendChild(s);
                })();
            </script>
        </section>
        <section id="mensajes">
            <h2>Mensajería Interna</h2>
            <form id="message-form">
                <input type="text" id="message-input" placeholder="Escribe tu mensaje aquí">
                <button type="submit">Enviar</button>
            </form>
            <div id="messages-container"></div>
            <script src="https://www.gstatic.com/firebasejs/9.4.0/firebase-app.js"></script>
            <script src="https://www.gstatic.com/firebasejs/9.4.0/firebase-database.js"></script>
            <script>
                var firebaseConfig = {
                    apiKey: "TU_API_KEY",
                    authDomain: "TU_DOMINIO.firebaseapp.com",
                    databaseURL: "https://TU_DOMINIO.firebaseio.com",
                    projectId: "TU_ID_DE_PROYECTO",
                    storageBucket: "TU_DOMINIO.appspot.com",
                    messagingSenderId: "TU_ID_DE_MENSAJERÍA",
                    appId: "TU_APP_ID"
                };
                firebase.initializeApp(firebaseConfig);
                var database = firebase.database();
                var messageForm = document.getElementById('message-form');
                var messageInput = document.getElementById('message-input');
                var messagesContainer = document.getElementById('messages-container');
                messageForm.addEventListener('submit', function(event) {
                    event.preventDefault();
                    var messageText = messageInput.value.trim();
                    if (messageText !== '') {
                        database.ref('messages').push({
                            text: messageText,
                            timestamp: firebase.database.ServerValue.TIMESTAMP
                        });
                        messageInput.value = '';
                    }
                });
                database.ref('messages').on('child_added', function(snapshot) {
                    var message = snapshot.val();
                    var messageElement = document.createElement('div');
                    messageElement.textContent = message.text;
                    messagesContainer.appendChild(messageElement);
                });
            </script>
        </section>
        <section id="busqueda">
            <h2>Búsqueda Avanzada</h2>
            <form id="search-form">
                <input type="text" id="search-input" placeholder="Ingrese su búsqueda...">
                <button type="submit">Buscar</button>
            </form>
            <div id="search-results"></div>
            <script>
                var searchForm = document.getElementById('search-form');
                var searchInput = document.getElementById('search-input');
                var searchResults = document.getElementById('search-results');
                searchForm.addEventListener('submit', function(event) {
                    event.preventDefault();
                    var searchTerm = searchInput.value.trim();
                    if (searchTerm !== '') {
                        // Aquí puedes realizar la búsqueda avanzada utilizando AJAX o cualquier otra técnica
                        // Por ahora, simplemente mostraremos un mensaje de ejemplo
                        searchResults.innerHTML = '<p>Resultados de búsqueda para: ' + searchTerm + '</p>';
                    }
                });
            </script>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Universidad UNITEC. Todos los derechos reservados.</p>
    </footer
