<!DOCTYPE html>
<html lang="en">
    <link rel="stylesheet" href="style.css">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicación de Productos</title>
   
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        form {
            margin-bottom: 20px;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            margin-bottom: 10px;
        }
        .notification {
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
        }
        .success {
            background-color: #d4edda;
            color: #155724;
        }
        .error {
            background-color: #f8d7da;
            color: #721c24;
        }
    </style>
</head>
<body>

    <!-- Inicio de sesión -->
    <form id="loginForm">
        <h2>Iniciar Sesión</h2>
        <label for="username">Nombre de Usuario:</label>
        <input type="text" id="username" name="username" required><br>
        <label for="password">Contraseña:</label>
        <input type="password" id="password" name="password" required><br>
        <button type="button" onclick="login()">Iniciar Sesión</button>
    </form>

    <!-- Lista de productos -->
    <h2>Lista de Productos</h2>
    <ul id="productList">

    </ul>

    <!-- Pantalla de Editar/Agregar Producto -->
    <form id="editProductForm" style="display: none;">
        <h2>Editar/Agregar Producto</h2>
        <label for="productName">Nombre del Producto:</label>
        <input type="text" id="productName" name="productName" required><br>
        <button type="button" onclick="saveProduct()">Guardar Producto</button>
    </form>

    <!-- Notificaciones -->
    <div id="notification" class="notification" style="display: none;"></div>

    <script>
        // inicio de sesión simulada
        function login() {
            // éxito
            showNotification('Inicio de sesión exitoso', 'success');
            // obtener la lista de productos
            getProductList();
        }

        // Función para mostrar la lista de productos
        function getProductList() {
            // obtener la lista de productos desde el servidor
            const products = ['Producto1', 'Producto2', 'Producto3','Producto4' ];
            const productList = document.getElementById('productList');
            productList.innerHTML = '';
            products.forEach(product => {
                const listItem = document.createElement('li');
                listItem.textContent = product;
                productList.appendChild(listItem);
            });
        }

        // Función para mostrar la pantalla de editar/agregar producto
        function showEditProductForm() {
            document.getElementById('editProductForm').style.display = 'block';
        }

        // Función para guardar el producto editado/agregado
        function saveProduct() {
            const productName = document.getElementById('productName').value;
            // éxito
            showNotification(`Producto '${productName}' guardado con éxito`, 'success');
            // obtener la lista de productos actualizada
            getProductList();
            // Ocultar el formulario de edición/agregado
            document.getElementById('editProductForm').style.display = 'none';
        }

        // Función para mostrar notificaciones
        function showNotification(message, type) {
            const notificationElement = document.getElementById('notification');
            notificationElement.textContent = message;
            notificationElement.className = `notification ${type}`;
            notificationElement.style.display = 'block';
            // Ocultar la notificación después de 5 segundo
            setTimeout(() => {
                notificationElement.style.display = 'none';
            }, 5000);
        }
    </script>

</body>
</html>
