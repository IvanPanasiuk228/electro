# Налаштування EmailJS для відправки заявок

## Крок 1: Створення акаунту EmailJS

1. Перейдіть на [emailjs.com](https://www.emailjs.com/)
2. Зареєструйтеся або увійдіть в акаунт
3. Перейдіть в Dashboard

## Крок 2: Налаштування Email Service

1. В Dashboard натисніть "Add New Service"
2. Виберіть "Gmail" або "Outlook"
3. Підключіть свій email `nowogodnayaskazka@gmail.com`
4. Скопіюйте **Service ID** (наприклад: `service_abc123`)

## Крок 3: Створення Email Template

1. Перейдіть в розділ "Email Templates"
2. Натисніть "Create New Template"
3. Налаштуйте шаблон:

**Subject:** Nowa wiadomość z formularza kontaktowego

**Content:**
```
Nowa wiadomość z formularza kontaktowego:

Imię i Nazwisko: {{from_name}}
Email: {{from_email}}
Telefon: {{from_phone}}
Usługa: {{service_type}}

Wiadomość:
{{message}}

---
Wiadomość wysłana z formularza na stronie Energy.Expert
```

4. Збережіть шаблон і скопіюйте **Template ID** (наприклад: `template_xyz789`)

## Крок 4: Отримання Public Key

1. Перейдіть в розділ "Account" → "API Keys"
2. Скопіюйте **Public Key** (наприклад: `user_def456`)

## Крок 5: Оновлення коду

Замініть в файлі `script.js` наступні значення:

```javascript
// Рядок 4: Замініть YOUR_PUBLIC_KEY
emailjs.init("user_def456");

// Рядок 95: Замініть YOUR_SERVICE_ID та YOUR_TEMPLATE_ID
emailjs.send('service_abc123', 'template_xyz789', templateParams)
```

## Приклад оновленого коду:

```javascript
// Initialize EmailJS
(function() {
    emailjs.init("user_def456"); // Ваш Public Key
})();

// В функції відправки:
emailjs.send('service_abc123', 'template_xyz789', templateParams)
    .then(function(response) {
        // Успішна відправка
    }, function(error) {
        // Помилка
    });
```

## Тестування

1. Відкрийте сайт в браузері
2. Заповніть форму контактів
3. Натисніть "Wyślij Wiadomość"
4. Перевірте email `nowogodnayaskazka@gmail.com`

## Важливо!

- EmailJS безкоштовний план дозволяє 200 email на місяць
- Для більшої кількості потрібен платний план
- Всі заявки будуть приходити на `nowogodnayaskazka@gmail.com`

## Підтримка

Якщо виникнуть проблеми:
1. Перевірте консоль браузера (F12)
2. Переконайтеся, що всі ID правильні
3. Перевірте налаштування Gmail/Outlook 