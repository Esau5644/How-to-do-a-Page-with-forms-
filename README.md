# ¡Hola! Soy Esau 👋

Bienvenido a mi perfil de GitHub. Soy un estudiante del CETis 17 con un poco de conocimiento sobre lenguajes de programación. En este README, te mostraré cómo crear una página web con un formulario utilizando PHP.

## Proyecto: Formulario de Contacto en PHP

En este proyecto, he creado una página web con un formulario de contacto. Este formulario permite a los usuarios ingresar su nombre, email y un mensaje, y luego envía esa información para su procesamiento.

### Código PHP

El código PHP procesa el formulario, valida los datos y muestra un mensaje de éxito o error según corresponda.

```php
<?php
$message = '';

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $nombre = htmlspecialchars($_POST['nombre']);
    $email = htmlspecialchars($_POST['email']);
    $mensaje = htmlspecialchars($_POST['mensaje']);

    // Validación simple
    if (!empty($nombre) && !empty($email) && !empty($mensaje)) {
        // Aquí podrías enviar un correo o guardar la información en una base de datos
        $message = 'Mensaje enviado correctamente';
    } else {
        $message = 'Por favor, complete todos los campos';
    }
}
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulario de Contacto</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #333;
            color: #fff;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #555;
        }
        .message {
            margin-top: 20px;
            padding: 10px;
            border-radius: 4px;
            text-align: center;
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
    <div class="container">
        <h1>Formulario de Contacto</h1>
        <?php if ($message): ?>
            <div class="message <?php echo $message == 'Mensaje enviado correctamente' ? 'success' : 'error'; ?>">
                <?php echo $message; ?>
            </div>
        <?php endif; ?>
        <form method="POST" action="">
            <div class="form-group">
                <label for="nombre">Nombre</label>
                <input type="text" id="nombre" name="nombre" required>
            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" name="email" required>
            </div>
            <div class="form-group">
                <label for="mensaje">Mensaje</label>
                <textarea id="mensaje" name="mensaje" rows="5" required></textarea>
            </div>
            <button type="submit">Enviar</button>
        </form>
    </div>
</body>
</html>
