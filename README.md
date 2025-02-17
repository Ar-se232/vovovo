<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Форма</title>
</head>
<body>
    <h1>Заповніть форму</h1>
    <form action="submit.php" method="post">
        <label for="name">Ваше ім'я:</label>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="telegram">Ваш телеграм-канал:</label>
        <input type="text" id="telegram" name="telegram" required><br><br>
        
        <button type="submit">Надіслати</button>
    </form>
</body>
</html>
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = htmlspecialchars($_POST["name"]);
    $telegram = htmlspecialchars($_POST["telegram"]);
    
    $to = "your-email@example.com";  // Змініть на свою електронну адресу
    $subject = "Нова заявка з сайту";
    $message = "Ім'я: $name\nТелеграм-канал: $telegram";
    $headers = "From: no-reply@yourwebsite.com";

    if (mail($to, $subject, $message, $headers)) {
        echo "Дані надіслані успішно!";
    } else {
        echo "Помилка надсилання.";
    }
}
?>
