<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <!--Colores de fondo y estilos, resolución-->
    <style>
        body {
            background-color: #eed7ec;
            font-family: 'Arial', sans-serif;
            text-align: center;
            padding: 50px;
        }
        h1 {
            color: #33002f;
            font-size: 3em;
        }
        p {
            font-size: 1.5em;
            color: #421414;
        }
        .flower-image {
            width: 600px;
            margin-top: 40px;
        }
        .btn {
            display: inline-block;
            padding: 10px 20px;
            background-color: #790051;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            margin-top: 20px;
            font-size: 1.2em;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .btn:hover {
            background-color: #004d40;
        }
        #message {
            font-size: 2em;
            color: #3b012d;
            margin-top: 50px;
            opacity: 1;
            transition: opacity 0.5s ease;
        }
        #message.fade-out {
            opacity: 0;
        }
        #message.fade-in {
            opacity: 1;
        }
        #next-btn {
            display: none;
        }
        #content {
            display: none;
        }
        #video-section {
            margin-top: 40px;
        }
        video {
            width: 80%;
            max-width: 200px;
            margin-top: 10px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <h1></h1>

    <div id="message">Hola, Lou.</div>
    <button id="next-btn" class="btn" onclick="showNextMessage()">Siguiente</button>
<!--Primer título y mensaje con la flor jsj-->
    <div id="content">
        <h1>Mejor tarde que nunca c:</h1>
        <p>Fue divertido hacer esto a decir verdad, y siento que valió la pena aprender algo de programación para hacer esta clase de cosas, en fin.</p>
        <img src="dehecho.jpg" width="50px"/>
        <img src="Gorena.jpeg" alt="Flores Virtuales" class="flower-image">
        <br>
        <a href="https://www.youtube.com/watch?v=PykXcyfPUk4" class="btn">Click aquí.</a>

        <!-- Sección de video, acordarme de subir el archivo de video "Lou.mp4"-->
        <div id="video-section">
            <p>Timelapse del dibujo.</p>
            <video controls>
                <source src="Lou.mp4" type="video/mp4">
                Tu navegador no soporta la reproducción de videos.
            </video>
        </div>
    </div>
<!--Estos mensajes van a aparecerle-->
    <script>
        const messages = [
            "Hola, Lou.",
            "¿Qué tal? dfsfsdf",
            "Ya sé que la cosa esta fue el otro día y blablabla",
            "Pero qué más da jsj.",
            "Me dijiste que no te gustan las flores físicas, pero nunca dijiste nada de las virtuales",
            "Así que:",
        ];
        let messageIndex = 0;

        function showNextMessage() {
            const messageElement = document.getElementById('message');
            const nextButton = document.getElementById('next-btn');

            // Inicio del fade out, no olvidar xddd
            messageElement.classList.add('fade-out');

            messageElement.addEventListener('transitionend', function handler() {
                //Remover el listener para evitar múltiples llamadas uwu
                messageElement.removeEventListener('transitionend', handler);

                messageIndex++;

                if (messageIndex < messages.length) {

                    messageElement.textContent = messages[messageIndex];

                    messageElement.classList.remove('fade-out');
                    messageElement.classList.add('fade-in');

                    messageElement.addEventListener('transitionend', function handlerFadeIn() {
                        messageElement.classList.remove('fade-in');
                        messageElement.removeEventListener('transitionend', handlerFadeIn);
                    });
                } else {
                    messageElement.style.display = 'none';
                    nextButton.style.display = 'none';
                    document.getElementById('content').style.display = 'block';
                }
            });
        }

        window.onload = function() {
            document.getElementById('next-btn').style.display = 'inline-block';
        };
    </script>

</body>
</html>
