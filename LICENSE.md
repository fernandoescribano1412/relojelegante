<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Reloj LED con Fecha</title>

<!-- Google Fonts Merriweather -->
<link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@700&display=swap" rel="stylesheet">

<style>
    html, body {
        margin: 0;
        padding: 0;
        background: black;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: 'Merriweather', serif;
        color: white;
        text-align: center;
    }

    #container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    #date {
        font-size: 5vw;
        margin-bottom: 2vh;
        text-shadow:
            0 0 5px #00ff00,
            0 0 10px #00ff00;
    }

    #clock {
        display: flex;
        justify-content: center;
        align-items: baseline;
        text-shadow:
            0 0 10px #00ff00,
            0 0 20px #00ff00,
            0 0 30px #00ff00,
            0 0 40px #00ff00;
    }

    #hhmm {
        font-size: 20vw;
        margin-right: 1vw;
    }

    #ss {
        font-size: 10vw;
        opacity: 0.8;
    }
</style>
</head>

<body>

<div id="container">
    <div id="date">Lunes, 13 Enero 2026</div>
    <div id="clock">
        <div id="hhmm">00:00</div>
        <div id="ss">00</div>
    </div>
</div>

<script>
// Función para actualizar fecha
function updateDate() {
    const now = new Date();
    const days = ['Domingo','Lunes','Martes','Miércoles','Jueves','Viernes','Sábado'];
    const months = ['Enero','Febrero','Marzo','Abril','Mayo','Junio','Julio','Agosto','Septiembre','Octubre','Noviembre','Diciembre'];
    const dayName = days[now.getDay()];
    const day = now.getDate();
    const month = months[now.getMonth()];
    const year = now.getFullYear();
    document.getElementById("date").textContent = `${dayName}, ${day} ${month} ${year}`;
}

// Función para actualizar hora
function updateClock() {
    const now = new Date();
    const h = String(now.getHours()).padStart(2,'0');
    const m = String(now.getMinutes()).padStart(2,'0');
    const s = String(now.getSeconds()).padStart(2,'0');

    document.getElementById("hhmm").textContent = `${h}:${m}`;
    document.getElementById("ss").textContent = s;
}

// Inicializar
updateDate();
updateClock();

// Actualizar cada segundo
setInterval(updateClock, 1000);
setInterval(updateDate, 60000); // actualiza fecha cada minuto
</script>

</body>
</html>
