# 🤖 Skillset AI Chat Bot Development Week

## 📝 Описание проекта
Добро пожаловать в Skillset AI Chat Bot Development Week! Это 9-дневный челлендж, направленный на изучение основ разработки программного обеспечения через создание AI чат-ботов с использованием Gemini AI для учащихся 5-7 классов (JUNIORS) и 8-11 классов (SENIORS) школы цифровых технологии Skillset Schools. В челлендже могут принять участие только учащиеся Skillset! К челленджу можно подключиться в любое время, главное отправить свое решение до дедлайна: 30 января, 18:00.

## 🎯 Цель проекта
Разработать функциональный Telegram бот с интеграцией Gemini AI и дополнительного API по выбору.

## 🏆 Призы
### Категория JUNIORS (5-7 классы):
- 🥇 1 место - Футболка "Skillset"
- 🥈 2 место - Кружка "Skillset"
- 🥉 3 место - Блокнот для кодинга "Skillset"

### Категория SENIORS (8-11 классы):
- 🥇 1 место - Футболка "Skillset"
- 🥈 2 место - Кружка "Skillset"
- 🥉 3 место - Блокнот для кодинга "Skillset"

## 📅 Важные даты
- **Дедлайн**: 30 января, 18:00 | Ссылка для сдачи проекта: [SAICBD Google Form](https://forms.gle/AQRfg3f6g46RmoSdA)
- **Объявление результатов**: 31 января|

### Советы для новичков
- Не бойтесь ошибок! Они - часть процесса обучения.
- Используйте Google, Perplexity, ChatGPT, Claude и другие инструменты для поиска решений проблем и разработки своего решения.
- Задавайте вопросы менторам - они здесь, чтобы помочь: 
   - мр. Толеген: http://t.me/ipayed
   - мр. Ерсултан: http://t.me/h4m13t

## 🛠️ Этапы разработки

### Шаг 1-2: Настройка окружения
1. Установка Visual Studio Code и Python: https://code.visualstudio.com/ & https://www.python.org/
2. Регистрация на GitHub и создание репозитория

A) Можно просто загрузить свой готовый проект, через загрузку файлов вручную на Github репозитории.

B) Можно установить программу Git, чтобы через командную строку Bash сохранять версии своего проекта на Github.
```bash
# Инициализация Git репозитория
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/username/repository.git
git push -u origin main
```


### Шаг 3-4: Создание базового Telegram бота

> Можете использовать наш Starter-Telegram-Bot-App: [app.py](https://github.com/Dataflow-kz/Skillset-AI-Chat-Bot-Development-Week/blob/main/app.py)

```python
import telebot

bot = telebot.TeleBot('YOUR_BOT_TOKEN')

@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.reply_to(message, "Привет! Я твой первый бот!")

@bot.message_handler(func=lambda message: True)
def echo_all(message):
    bot.reply_to(message, message.text)

bot.polling()
```

### Шаг 5-6: Интеграция Gemini AI
```python
import google.generativeai as genai

genai.configure(api_key='YOUR_GEMINI_API_KEY')
model = genai.GenerativeModel('gemini-1.5-flash')

@bot.message_handler(func=lambda message: True)
def handle_message(message):
    response = model.generate_content(message.text)
    bot.reply_to(message, response.text)
```

### Шаг 7-8: Интеграция дополнительного API
Выберите один из предложенных API:
1. OpenWeatherMap API
2. News API
3. CoinGecko API
4. NASA API
5. The Cat API
6. REST Countries API
7. Любой другой бесплатный API

Пример интеграции Weather API:
```python
import requests

@bot.message_handler(commands=['weather'])
def get_weather(message):
    city = message.text.split()[1]
    response = requests.get(
        f'http://api.openweathermap.org/data/2.5/weather?q={city}&appid=YOUR_API_KEY'
    )
    data = response.json()
    weather = data['weather'][0]['description']
    temp = data['main']['temp'] - 273.15
    bot.reply_to(message, f"Погода в {city}: {weather}, температура: {temp:.1f}°C")
```

### Шаг 9: Финальное тестирование и документация

## 📚 Требования к проекту
1. Бот должен быть полностью функциональным
2. Код должен быть загружен на GitHub
3. Репозиторий должен содержать подробный README.md
4. Необходимо использовать как минимум один дополнительный API
5. Необязательно публиковать телеграм бот через облачную платформу, достаточно, чтобы бот запускался локально.

## 📤 Как сдать проект
1. Загрузите код на GitHub с хорошо оформленным README.MD файлом.
2. Заполните форму сдачи проекта: [LINK]
3. Убедитесь, что ваш README.md содержит:
   - Описание бота
   - Инструкции по установке
   - Примеры использования
   - Список использованных технологий

## 💡 Пример проекта
NASA Daily Bot - бот для получения актуальных данных из космоса:
https://github.com/silvermete0r/nasa_daily_bot

## 🤝 Поддержка
По всем вопросам обращайтесь к менторам проекта или создавайте issues в GitHub репозитории.

[Предыдущий контент остаётся без изменений до секции Лицензия]

## 📜 Лицензия
[MIT License](LICENSE)

## 📖 Словарь терминов для начинающих

### Основные инструменты
- **Python** - популярный язык программирования, который очень прост для изучения. Представьте его как конструктор LEGO: вы собираете простые блоки кода, чтобы создать что-то крутое.

- **Visual Studio Code (VSCode)** - это как продвинутый блокнот для программистов. В нём удобно писать код, и он подсвечивает ошибки, как учитель с красной ручкой, только моментально.

- **Git** - система, которая запоминает все изменения в вашем коде, как машина времени. Если что-то пошло не так, всегда можно вернуться к работающей версии.

- **GitHub** - это как социальная сеть для кода. Здесь программисты хранят свои проекты, делятся ими с другими и работают вместе. Представьте его как облачное хранилище для кода с дополнительными возможностями.

### API и библиотеки
- **API (Application Programming Interface)** - программный интерфейс, то есть описание способов взаимодействия одной компьютерной программы с другими.

- **Telegram Bot API** - набор инструментов от Telegram, которые позволяют вашему боту общаться с пользователями. Как пульт управления для бота.

- **Gemini AI API** - инструмент от Google, который позволяет боту "думать" и отвечать почти как человек.

### Технические термины
- **Бот** - программа, которая автоматически отвечает на сообщения пользователей по заданным правилам.

- **Репозиторий** - папка с вашим проектом на GitHub. Как цифровой портфель для вашего кода.

- **Commit** - сохранение изменений в коде, как контрольная точка в игре.

- **Token** - секретный ключ доступа, как пароль для вашего бота. Получаем с помощью: http://t.me/BotFather

### Команды Git
- `git init` - начать отслеживать изменения в проекте
- `git add` - добавить файлы для сохранения
- `git commit` - сохранить изменения
- `git push` - отправить изменения на GitHub

### Полезные ресурсы для обучения
- [Python для начинающих](https://www.python.org/about/gettingstarted/)
- [Документация Telegram Bot API](https://core.telegram.org/bots/api)
- [Полное руководство по Python для учащихся Skillset](https://github.com/silvermete0r/Skillset_learning_python_projects)
