<!DOCTYPE html>
<html>
<head>
    <title>Mi Diario Personal</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
    <script src="https://cdn.tiny.cloud/1/no-api-key/tinymce/5/tinymce.min.js" referrerpolicy="origin"></script>
    <style>
        /* ... (Estilos CSS personalizados) ... */
    </style>
</head>
<body>
    <div class="container">
        <h1>Mi Diario Personal</h1>

        <div id="editor">
            <div id="toolbar">
                <button onclick="document.execCommand('bold', false, null)">Negrita</button>
                <button onclick="document.execCommand('italic', false, null)">Cursiva</button>
                <input type="file" id="imagen" accept="image/*" onchange="insertarImagen(this)">
            </div>
            <div id="area-editor" contenteditable="true"></div>
        </div>
        <button onclick="guardarEntrada()">Guardar Entrada</button>

        <div id="calendario">
            <input type="date" id="fecha" onchange="mostrarFechaSeleccionada()">
        </div>

        <div id="lista-entradas">
            <h2>Mis Entradas</h2>
        </div>

        <div class="dropdown">
            <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                Configuración
            </button>
            <ul class="dropdown-menu">
                <li>
                    <div id="personalizacion" class="p-3">
                        <h2>Personalización</h2>
                        <label for="color-fondo">Color de fondo:</label>
                        <input type="color" id="color-fondo" value="#f8f8f8" onchange="cambiarEstilo()">

                        <label for="color-texto">Color de texto:</label>
                        <input type="color" id="color-texto" value="#333333" onchange="cambiarEstilo()">

                        <label for="fuente">Fuente:</label>
                        <select id="fuente" onchange="cambiarEstilo()">
                            <option value="Arial">Arial</option>
                            <option value="Verdana">Verdana</option>
                            <option value="Times New Roman">Times New Roman</option>
                        </select>
                    </div>
                </li>
            </ul>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        tinymce.init({
            selector: '#area-editor',
            plugins: 'image',
            toolbar: 'bold italic | image',
        });

        // ... (Funciones guardarEntrada, mostrarEntradas, editarEntrada y eliminarEntrada anteriores) ...

        function insertarImagen(input) {
            const file = input.files[0];
            const reader = new FileReader();

            reader.onload = function(e) {
                const img = document.createElement('img');
                img.src = e.target.result;
                document.getElementById('area-editor').appendChild(img);
            }

            reader.readAsDataURL(file);
        }

        function mostrarFechaSeleccionada() {
            const fechaSeleccionada = document.getElementById('fecha').value;
            alert("Fecha seleccionada: " + fechaSeleccionada);
        }

        function cambiarEstilo() {
            const colorFondo = document.getElementById("color-fondo").value;
            const colorTexto = document.getElementById("color-texto").value;
            const fuente = document.getElementById("fuente").value;

            document.body.style.backgroundColor = colorFondo;
            document.body.style.color = colorTexto;
            document.body.style.fontFamily = fuente;
        }

        // ... (Llamada a mostrarEntradas() al cargar la página) ...
    </script>
</body>
</html>
