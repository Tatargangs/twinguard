
# TwinGuard: Система Авторизации с Видео Для Защиты Доступа

Добро пожаловать в репозиторий TwinGuard! Этот проект представляет собой приложение авторизации на языке Python с использованием библиотеки Tkinter для создания графического интерфейса. TwinGuard предназначен для работы в полноэкранном режиме и использования различных функций безопасности, таких как блокировка системных клавиш, воспроизведение видео при бездействии, защита учетных записей, а также предотвращение отключения экрана и режима сна.

## Основные Функции TwinGuard

- **Авторизация пользователей**: Поддержка базового входа с сохранением учетных записей в локальной базе данных SQLite. Для шифрования данных используется библиотека Cryptography (Fernet).
- **Полноэкранный режим с ограничениями**: TwinGuard работает в полноэкранном режиме, скрывается из панели задач и списка окон Alt+Tab.
- **Система безопасности**:
  - Блокировка определенных системных клавиш, таких как `Ctrl`, `Windows`, `Esc`, `Tab`, чтобы предотвратить выход из приложения.
  - Автоматическое выключение приложения при входе с учетной записью "twinguardadmin".
- **Защита от бездействия**: При длительном бездействии пользователя, на экране воспроизводится заранее загруженное видео.
- **Уведомления и использование клавиатуры**: Информация о раскладке клавиатуры (смена при помощи Shift + Alt) для удобства пользователя.
- **Возможность скачивания видео с YouTube** для показа на экране бездействия.
- **Защита от перехода системы в спящий режим и выключения экрана**.
  
## Установка

Для работы с TwinGuard потребуется Python и несколько дополнительных библиотек. Следуйте этим шагам для установки и запуска проекта:

1. Убедитесь, что на вашем компьютере установлен Python версии 3.7 или выше.

2. Клонируйте этот репозиторий:

    ```sh
    git clone https://github.com/your-username/twinguard.git
    ```

3. Перейдите в папку проекта:

    ```sh
    cd twinguard
    ```

4. Установите зависимости:

    ```sh
    pip install -r requirements.txt
    ```

    **requirements.txt** должен включать следующие библиотеки:

    - `pytube`
    - `bcrypt`
    - `cryptography`
    - `opencv-python`
    - `tkinter`
    - `pynput`
    - `Pillow`
    - `keyboard`

5. Убедитесь, что у вас установлен шрифт `arial.ttf` в рабочем каталоге. Он используется для вывода текста на экране видео.

## Использование

После завершения установки зависимостей вы можете запустить приложение следующей командой:

```sh
python main.py
```

### Основные особенности интерфейса:

- При запуске программа запускается в **полноэкранном режиме**, скрывает панель задач и удаляет видимость из окна Alt+Tab.
- Пользователь должен ввести **имя пользователя и пароль** для доступа к системе. Для выхода из программы используйте учетные данные:

  - **Имя пользователя**: `twinguardadmin`
  - **Пароль**: `admin123`

  При использовании этих учетных данных программа завершится и вернет вас к рабочему столу.

- **Таймер бездействия**: если пользователь неактивен в течение 10 секунд, начнется воспроизведение видео на весь экран, чтобы привлечь внимание. Для продолжения работы достаточно произвести любое действие (движение мышью, нажатие клавиши и т.д.).

### Безопасность

- При запуске программа **блокирует некоторые системные клавиши**, такие как `Ctrl`, `Windows`, `Tab` и `Esc`, чтобы пользователь не мог закрыть окно или покинуть приложение.
- Все учетные записи **зашифрованы** с использованием библиотеки **Cryptography (Fernet)**.
- Пароли хранятся в базе данных в виде хэшей, созданных с помощью библиотеки **bcrypt**.
- Программа создает папку `C:\\twinguard` для хранения базы данных и шифровального ключа.

### Папка twinguard

TwinGuard использует директорию `C:\\twinguard` для хранения:

- **База данных пользователей** (`users.db`)
- **Ключ шифрования** (`secret.key`)
- **Видео для бездействия** (`video.mp4`)

Эти файлы будут созданы автоматически при первом запуске приложения.

## Настройка и Адаптация

TwinGuard можно настроить под нужды любого пользователя:

- Путь к видео можно изменить, обновив атрибут `video_path`.
- Таймер бездействия можно увеличить или уменьшить путем изменения параметра `10` в функции `self.inactivity_timer = Timer(10, self.check_inactivity)`.

## Поддерживаемые ОС

TwinGuard предназначен для работы на **Windows**, поскольку включает команды для управления панелью задач и клавишами, которые специфичны для этой ОС.

## Замечания

- Программа требует наличия **шрифта arial.ttf** для отображения текста на видео. Убедитесь, что шрифт доступен в рабочем каталоге программы.
- TwinGuard блокирует системные клавиши, что может повлиять на удобство работы, если что-то пойдет не так. Рекомендуется использовать программу на тестовой машине или в безопасном окружении.

## Планы на будущее

- **Добавление функционала двухфакторной аутентификации**.
- **Создание более дружественного интерфейса** для пользователей.
- **Оптимизация воспроизведения видео** для лучшей производительности.

## Контакты

Если у вас есть вопросы или предложения, вы можете создать **Issue** в репозитории или связаться с автором по электронной почте: `your-email@example.com`.

## Лицензия

Проект TwinGuard распространяется под лицензией MIT. Подробности можно найти в файле LICENSE.

