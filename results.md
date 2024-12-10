## Задание 1 - Автоматизация проверки формата файлов при коммите

1) В терминале перешла в корень репозитория laba-5:
2) Создала папку `hooks`
3) Создала файл `pre-commit` в папке `hooks`
4) Открыла файл `pre-commit` для редактирования в `nano`
5) Добавила следующий код в файл:
![Screnshot](https://github.com/ilonabond/Laba4/blob/main/Снимок%20экрана%202024-11-07%20в%2015.27.46.png)
7. Сохраните изменения в файле `pre-commit` (Ctrl+O, затем Enter, затем Ctrl+X для выхода).

#### Шаг 2: Сделайте скрипт исполняемым
```bash
chmod +x .git/hooks/pre-commit
```

#### Шаг 3: Проверьте работу хука
1. Добавьте тестовый `.txt` файл без подписи:
   ```bash
   echo "Пример без подписи" > test.txt
   git add test.txt
   git commit -m "Тестовый коммит без подписи"
   ```
   Вы увидите сообщение об ошибке и коммит не пройдет.

2. Добавьте подпись к файлу и попробуйте снова:
   ```bash
   echo "Автор: Иван Иванов" >> test.txt
   git add test.txt
   git commit -m "Тестовый коммит с подписью"
   ```
   Коммит пройдет успешно.

---

### Задание 2 - Использование Git Flow в проекте

#### Шаг 1: Убедитесь, что Git Flow установлен
1. На MacOS можно установить Git Flow с помощью Homebrew:
   ```bash
   brew install git-flow
   ```

2. Проверьте, что Git Flow установлен:
   ```bash
   git flow version
   ```

#### Шаг 2: Инициализируйте Git Flow в проекте
1. Перейдите в корень вашего репозитория:
   ```bash
   cd путь/к/вашему/репозиторию
   ```

2. Запустите инициализацию Git Flow:
   ```bash
   git flow init
   ```
   При инициализации Git Flow попросит указать имена веток (по умолчанию используйте `develop` и `main`).

#### Шаг 3: Создание функциональности
1. Создайте новую фичу:
   ```bash
   git flow feature start task-management
   ```

2. Внесите изменения в проект (например, создайте файл `task_manager.py`):
   ```bash
   echo "def create_task(title, description):" > task_manager.py
   echo "    print(f'Создана новая задача: {title}')" >> task_manager.py
   ```

3. Закоммитьте изменения:
   ```bash
   git add task_manager.py
   git commit -m "Добавлен функционал управления задачами"
   ```

4. Завершите фичу:
   ```bash
   git flow feature finish task-management
   ```

#### Шаг 4: Создание релиза
1. Переключитесь на ветку `develop` (если Git Flow не сделал это автоматически):
   ```bash
   git checkout develop
   ```

2. Начните релиз:
   ```bash
   git flow release start v1.0.0
   ```

3. Обновите версию проекта (например, в `version.txt`):
   ```bash
   echo "v1.0.0" > version.txt
   git add version.txt
   git commit -m "Обновлена версия для релиза v1.0.0"
   ```

4. Завершите релиз:
   ```bash
   git flow release finish v1.0.0
   ```

#### Шаг 5: Создание hotfix
1. Начните исправление ошибки:
   ```bash
   git flow hotfix start hotfix-1.0.1
   ```

2. Исправьте ошибку в файле (например, `file_with_error.py`):
   ```bash
   echo "# Исправлена ошибка" >> file_with_error.py
   git add file_with_error.py
   git commit -m "Исправлена критическая ошибка"
   ```

3. Завершите hotfix:
   ```bash
   git flow hotfix finish hotfix-1.0.1
   ```

#### Шаг 6: Отправьте изменения в удаленный репозиторий
1. Запушьте изменения:
   ```bash
   git push origin develop
   git push origin main
   ```
