<!DOCTYPE html> 
<html lang="pt"> 
<head> 
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <title>29/10</title> 
    <style> 
        body { 
            font-family: "Times New Roman", serif; 
            margin: 0; 
            background-color: #1e1e2f; 
            color: #f0f0f0; 
            overflow: hidden; 
        } 
        .container { 
            text-align: center; 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            flex-direction: column; 
        } 
        input[type="password"] { 
            padding: 10px; 
            margin-top: 10px; 
            font-size: 16px; 
            border: 1px solid #555; 
            border-radius: 5px; 
            background-color: #3e3e4e; 
            color: #fff; 
        } 
        button { 
            padding: 10px 20px; 
            margin-top: 10px; 
            font-size: 16px; 
            background-color: #007bff; 
            color: #fff; 
            border: none; 
            border-radius: 5px; 
            cursor: pointer; 
        } 
        button:hover { 
            background-color: #0056b3; 
        } 
        .error { 
            color: red; 
            margin-top: 10px; 
        } 
        #balloon-container { 
            position: absolute; 
            top: 0; 
            left: 0; 
            width: 100%; 
            height: 100%; 
            overflow: hidden; 
            z-index: -1; 
        } 
        .balloon { 
            position: absolute; 
            width: 50px; 
            height: 70px; 
            background-color: red; 
            border-radius: 50%; 
            animation: float 5s linear infinite; 
        } 
        .balloon::before { 
            content: ''; 
            position: absolute; 
            width: 2px; 
            height: 20px; 
            background: #fff; 
            bottom: -20px; 
            left: 50%; 
            transform: translateX(-50%); 
        } 
        @keyframes float { 
            0% { 
                transform: translateY(100vh); 
                opacity: 0; 
            } 
            50% { 
                opacity: 1; 
            } 
            100% { 
                transform: translateY(-10vh); 
                opacity: 0; 
            } 
        } 
        .content { 
            text-align: justify; 
            background-color: #2e2e3e; 
            padding: 20px; 
            border-radius: 10px; 
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3); 
            max-width: 800px; 
            margin: 40px auto; 
            overflow-y: auto; 
            max-height: 80vh; 
        } 
        .content h1 { 
            text-align: center; 
            margin-bottom: 20px; 
        } 
        .dedication { 
            margin-top: 20px; 
            font-size: 14px; 
            text-align: center; 
        } 
    </style> 
    <script> 
        function checkPassword() { 
            const password = document.getElementById('password').value; 
            const correctPassword = "the1"; 
            if (password === correctPassword) { 
                document.body.innerHTML = `
                    <div id="balloon-container"></div> 
                    <div class="content"> 
                        <h1>FELIZ ANIVERSÁRIO MEU LINDO</h1>
                        <p>Eu era como um suicida jogando roleta russa em um parque de diversões abandonado...</p>
                        <p><b>feliz aniversário senhor lucas araujo fernandes...</b></p>
                    </div>`;
                startBalloons(); 
                addMusic();
            } else { 
                document.getElementById('error-message').innerText = "Senha incorreta. Tente novamente!"; 
            } 
        }

        function startBalloons() { 
            const container = document.getElementById('balloon-container'); 
            for (let i = 0; i < 30; i++) { 
                const balloon = document.createElement('div'); 
                balloon.classList.add('balloon'); 
                balloon.style.backgroundColor = getRandomColor(); 
                balloon.style.left = Math.random() * 100 + 'vw'; 
                balloon.style.animationDuration = Math.random() * 2 + 3 + 's'; 
                container.appendChild(balloon); 
            } 
        }

        function getRandomColor() { 
            const colors = ['#ff0000', '#ffa500', '#ffff00', '#00ff00', '#00ffff', '#0000ff', '#ff00ff']; 
            return colors[Math.floor(Math.random() * colors.length)]; 
        }

        function addMusic() { 
            const iframe = document.createElement('iframe');
            iframe.width = "560";
            iframe.height = "315";
            iframe.src = "https://www.youtube.com/embed/cZb-ubdscvA?autoplay=1";
            iframe.frameBorder = "0";
            iframe.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture";
            iframe.allowFullscreen = true;
            document.body.appendChild(iframe);
        }
    </script> 
</head> 
<body> 
    <div class="container"> 
        <h1>ALERTA</h1> 
        <p>Insira a senha para acessar o conteúdo:</p> 
        <p>Dica: a senha está na imagem que foi enviada</p> 
        <p>BOBAO, EU SEI A SENHA E VOCE NAO</p> 
        <input type="password" id="password" placeholder="TENTE A SENHA"> 
        <button onclick="checkPassword()">Entrar</button> 
        <p id="error-message" class="error"></p>
    </div> 
</body> 
</html>
