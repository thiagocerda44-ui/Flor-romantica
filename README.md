# Flor-romantica
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Intento Final 💖</title>
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            text-align: center;
            background: linear-gradient(to bottom, #ffe6f0, #fff);
            overflow: hidden;
            transition: 1s;
        }

        h1 {
            color: #d63384;
            margin-top: 20px;
        }

        .flor {
            font-size: 90px;
            animation: latido 1.5s infinite;
            transition: 0.5s;
        }

        @keyframes latido {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        button {
            padding: 12px 25px;
            font-size: 18px;
            margin: 10px;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            position: relative;
        }

        .si {
            background-color: #ff4d88;
            color: white;
        }

        .no {
            background-color: #999;
            color: white;
            position: absolute;
        }

        #respuesta {
            margin-top: 20px;
            font-size: 22px;
            color: #444;
            transition: 0.5s;
        }

        .corazon {
            position: absolute;
            color: #ff4d88;
            font-size: 20px;
            animation: flotar 5s linear infinite;
        }

        @keyframes flotar {
            0% { transform: translateY(100vh); opacity: 1; }
            100% { transform: translateY(-10vh); opacity: 0; }
        }

        /* Pantalla final */
        .final {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, #ff99cc, #ff4d88);
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            color: white;
            font-size: 30px;
            text-align: center;
            opacity: 0;
            pointer-events: none;
            transition: 1s;
        }

        .final.activo {
            opacity: 1;
            pointer-events: all;
        }

        .mensajeFinal {
            font-size: 40px;
            animation: latido 1.5s infinite;
        }
    </style>
</head>
<body>

    <div class="flor" id="flor">🌸</div>
    <h1>¿Lo intentamos por última vez? 💖</h1>

    <button class="si" onclick="responder('si')">Sí 💕</button>
    <button id="btnNo" class="no">No 😢</button>

    <div id="respuesta"></div>

    <!-- Pantalla final -->
    <div class="final" id="pantallaFinal">
        <div class="mensajeFinal">💖 Gracias por darme otra oportunidad 💖</div>
        <p>Prometo hacerlo especial esta vez… 🌸</p>
    </div>

    <script>
        const btnNo = document.getElementById("btnNo");
        const flor = document.getElementById("flor");
        const final = document.getElementById("pantallaFinal");

        btnNo.style.top = "60%";
        btnNo.style.left = "55%";

        document.addEventListener("mousemove", function(e) {
            const rect = btnNo.getBoundingClientRect();
            const distancia = Math.hypot(
                e.clientX - (rect.left + rect.width / 2),
                e.clientY - (rect.top + rect.height / 2)
            );

            if (distancia < 100) {
                const nuevaX = Math.random() * (window.innerWidth - rect.width);
                const nuevaY = Math.random() * (window.innerHeight - rect.height);

                btnNo.style.left = nuevaX + "px";
                btnNo.style.top = nuevaY + "px";
            }
        });

        function responder(opcion) {
            let respuesta = document.getElementById("respuesta");

            if(opcion === "si") {
                respuesta.innerHTML = "💖 Sabía que dirías que sí... 💖";

                // Cambia la flor
                flor.innerHTML = "🌹";
                flor.style.transform = "scale(1.5)";

                lanzarCorazones();

                // Mostrar pantalla final
                setTimeout(() => {
                    final.classList.add("activo");
                }, 1500);
            }
        }

        function lanzarCorazones() {
            for(let i = 0; i < 40; i++) {
                let corazon = document.createElement("div");
                corazon.className = "corazon";
                corazon.innerHTML = "💖";
                corazon.style.left = Math.random() * 100 + "vw";
                corazon.style.animationDuration = (2 + Math.random() * 2) + "s";
                document.body.appendChild(corazon);

                setTimeout(() => {
                    corazon.remove();
                }, 5000);
            }
        }
    </script>

</body>
</html>
