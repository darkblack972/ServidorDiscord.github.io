<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Server Causa Ingresar</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url('https://media.discordapp.net/attachments/1222224620187418654/1320512335588364349/image.png?ex=6769de72&is=67688cf2&hm=9e163fde28e1460d1bf64baf71b889632bdf00720abfc73b18d200c8bec85ed3&=&format=webp&quality=lossless&width=550&height=116') no-repeat center center fixed;
            background-size: contain;
            color: white;
            text-align: center;
        }

        .container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            backdrop-filter: blur(5px);
            background-color: rgba(0, 0, 0, 0.8);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
        }

        .container h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .input-group {
            margin: 10px 0;
        }

        .input-group label {
            font-size: 1.2rem;
            display: block;
            margin-bottom: 5px;
        }

        .input-group input {
            font-size: 1rem;
            padding: 10px;
            width: 250px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            font-size: 1.2rem;
            padding: 10px 20px;
            background-color: #7289da;
            border: none;
            border-radius: 5px;
            color: white;
            cursor: not-allowed;
            opacity: 0.6;
            transition: opacity 0.3s, cursor 0.3s;
        }

        button.enabled {
            cursor: pointer;
            opacity: 1;
        }

        .footer {
            margin-top: 20px;
            display: flex;
            justify-content: center;
        }

        .footer img {
            width: 80px;
            height: 80px;
            margin: 0 10px;
            border-radius: 10%;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Bienvenido al Server Causa</h1>
        <p>Llena ambos campos para unirte al mejor servidor de Discord.</p>
        <div class="input-group">
            <label for="user">Tu nombre de usuario en Discord</label>
            <input type="text" id="user" placeholder="Ejemplo#1234">
        </div>
        <div class="input-group">
            <label for="inviter">Nombre del que te invitó</label>
            <input type="text" id="inviter" placeholder="Ejemplo#5678">
        </div>
        <button id="joinButton" disabled>Server Causa Ingresar</button>
        <div class="footer">
            <!-- Footer images removed as per request -->
        </div>
    </div>
    <script>
        const userField = document.getElementById('user');
        const inviterField = document.getElementById('inviter');
        const joinButton = document.getElementById('joinButton');

        function validateFields() {
            if (userField.value.trim() !== '' && inviterField.value.trim() !== '') {
                joinButton.disabled = false;
                joinButton.classList.add('enabled');
                joinButton.addEventListener('click', saveToFile);
            } else {
                joinButton.disabled = true;
                joinButton.classList.remove('enabled');
            }
        }

        function saveToFile() {
            const data = `${userField.value.trim()} fue invitado por ${inviterField.value.trim()}\n`;

            const blob = new Blob([data], { type: 'text/plain' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = 'usuarios_invitados.txt'; // Nombre del archivo
            link.click();

            alert("Los datos se han guardado correctamente en un archivo.");
            window.location.href = 'https://discord.gg/97YMhxFh';
        }

        userField.addEventListener('input', validateFields);
        inviterField.addEventListener('input', validateFields);
    </script>
</body>
</html>
