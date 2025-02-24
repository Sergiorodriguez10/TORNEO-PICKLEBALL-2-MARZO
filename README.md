# TORNEO-PICKLEBALL-2-MARZO
TORNEO PICKLEBALL 2 MARZO
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Nombres</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        #nameList { margin-top: 20px; }
    </style>
</head>
<body>
    <h2>Apunta tu nombre</h2>
    <input type="text" id="nameInput" placeholder="Escribe tu nombre">
    <button onclick="addName()">Añadir</button>
    <ul id="nameList"></ul>
    
    <script>
        document.addEventListener("DOMContentLoaded", loadNames);
        
        function addName() {
            const nameInput = document.getElementById("nameInput");
            const name = nameInput.value.trim();
            if (name) {
                let names = JSON.parse(localStorage.getItem("names")) || [];
                names.push(name);
                localStorage.setItem("names", JSON.stringify(names));
                nameInput.value = "";
                loadNames();
            }
        }
        
        function loadNames() {
            const nameList = document.getElementById("nameList");
            nameList.innerHTML = "";
            let names = JSON.parse(localStorage.getItem("names")) || [];
            names.forEach(name => {
                let li = document.createElement("li");
                li.textContent = name;
                nameList.appendChild(li);
            });
        }
    </script>
</body>
</html>
