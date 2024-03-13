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
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Universidad XYZ. Todos los derechos reservados.</p>
    </footer>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/5.10.0/main.min.js"></script> <!-- FullCalendar -->
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            var calendarEl = document.getElementById('calendario');
            var calendar = new FullCalendar.Calendar(calendarEl, {
                initialView: 'dayGridMonth', // Vista mensual por defecto
                events: [
                    {
                        title: 'Evento 1',
                        start: '2024-03-15',
                        end: '2024-03-16'
                    },
                    {
                        title: 'Evento 2',
                        start: '2024-03-20'
                    }
                ]
            });
            calendar.render();
        });
    </script>
</body>
</html>
