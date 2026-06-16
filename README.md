# 🚕 Кара-Куль Такси

Кара-Куль шаары үчүн иштелип чыккан толук веб-тапшырма (Taxi App).

## 📁 Долбоор Структурасы

```
taxi-app/
├── api/
│   ├── .htaccess          # API папкасынын коопсуздук конфигурациясы
│   ├── auth.php           # Авторизация + Регистрация (Google Sign-In)
│   ├── config.php         # Firebase + MySQL конфигурациясы
│   ├── driver.php         # Айдоочу функциялары
│   ├── location.php       # Геолокация (GPS координаталар)
│   ├── register.php       # Айдоочуларды каттоо
│   └── ride.php           # Заказ логикасы
├── sql/
│   └── database.sql       # MySQL база схемасы
├── .htaccess              # Apache сервер конфигурациясы
└── index.html             # Frontend (веб-интерфейс)
```

## 🛠 Орнотуу

### 1. MySQL базасын түзүү

```bash
mysql -u root -p < sql/database.sql
```

### 2. Конфигурация

`api/config.php` файлында төмөнкүлөрдү өзгөртүңүз:

```php
define('DB_HOST', 'localhost');
define('DB_NAME', 'taxi_karakol');
define('DB_USER', 'сиздин_колдонуучу');
define('DB_PASS', 'сиздин_сирсөз');

// Firebase
const firebaseConfig = {
    apiKey: "СИЗДИН_FIREBASE_API_KEY",
    authDomain: "сиздин-проект.firebaseapp.com",
    // ...
};
```

### 3. Firebase орнотуу

1. [Firebase Console](https://console.firebase.google.com/)'го кирүү
2. Жаңы проект түзүү
3. Authentication → Google Sign-In иштетүү
4. API Key алуу

### 4. Apache конфигурациясы

Apache серверде `mod_rewrite` жана `mod_headers` модулдары иштетилген болушу керек.

## 📱 Функционалдык мүмкүнчүлүктөрү

### Кардарлар үчүн:
- ✅ Google Sign-In аркылуу кирүү
- ✅ Картада онлайн айдоочуларды көрүү
- ✅ Заказ түзүү жана машина тандоо
- ✅ Баа эсептөө (Эконом, Комфорт, Бизнес)
- ✅ Жүрүштү көзөмөлдөө
- ✅ SMS тастыктоо

### Айдоочулар үчүн:
- ✅ Google Sign-In аркылуу кирүү
- ✅ Машина маалыматтарын каттоо
- ✅ Онлайн/Офлайн режим
- ✅ GPS геопозиция жаңыртуу
- ✅ Заказ кабыл алуу/четке кагуу
- ✅ Жүрүштү баштоо/бүтүү
- ✅ Статистика

## 🗺️ Кара-Куль шаары

- Борбордук координаталар: 42.4907, 78.3936
- Шаар чегарасы: 15 км радиус
- Белгилүү жерлер: Базар, Автовокзал, Оорукана, Парк, Мечит

## 📋 API Endpoints

### Авторизация
- `POST api/auth.php?action=google-login` - Google менен кирүү
- `POST api/auth.php?action=send-sms-code` - SMS код жөнөтүү
- `POST api/auth.php?action=verify-sms-code` - SMS код текшерүү
- `GET api/auth.php?action=profile` - Профиль алуу

### Айдоочу
- `POST api/register.php?action=complete-driver-profile` - Профиль толтуруу
- `POST api/register.php?action=set-status` - Статус өзгөртүү
- `GET api/driver.php?action=my-rides` - Жүрүштөр тарабы
- `POST api/driver.php?action=accept-ride` - Жүрүш кабыл алуу
- `POST api/driver.php?action=complete-ride` - Жүрүш бүтүү

### Геолокация
- `POST api/location.php?action=update-location` - Жайгашкан жер жаңыртуу
- `GET api/location.php?action=nearby-drivers` - Жакын айдоочулар

### Заказ
- `POST api/ride.php?action=create` - Заказ түзүү
- `POST api/ride.php?action=estimate-price` - Баа эсептөө
- `GET api/ride.php?action=status` - Статус алуу
- `POST api/ride.php?action=cancel` - Жокко чыгаруу

## 🔒 Коопсуздук

- JWT токендер
- Firebase Authentication
- SMS тастыктоо
- CORS саясаты
- SQL Injection коргоо (Prepared Statements)

## 📞 Байланыш

Кара-Куль Такси
© 2026 Бардык укуктар корголгон
