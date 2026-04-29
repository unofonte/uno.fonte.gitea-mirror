источник [**sudden-che/gitea-mirror**](https://github.com/sudden-che/gitea-mirror)

[README-EN](README.md)

---

# Gitea Push Mirror Automation

Скрипт на Python для автоматизации зеркалирования (Push Mirror) репозиториев между двумя инстансами Gitea.

## 🔧 Возможности

- Получает **все доступные репозитории** пользователя: личные, организационные, приватные.
- Создаёт недостающие репозитории на целевом Gitea.
- Настраивает Push Mirror с `sync_on_commit`.
- Пропускает репозитории, если зеркала уже настроены.
- Поддерживает `--dry-run` и `--insecure` режимы.
- Работает через REST API, используя `Authorization: token ...` заголовки.

---

## 🚀 Запуск

1. Установи зависимости:

```bash
pip install -r requirements.txt
```

2. Создай .env файл (можно переименовать из примера ниже):

# .env
```bash
SRC_GITEA_URL=https://your-gitea1.com
SRC_GITEA_TOKEN=токен_от_source_gitea

DEST_GITEA_URL=https://your-gitea2.com
DEST_GITEA_TOKEN=токен_от_target_gitea
DEST_GITEA_USER=your-user
```

3. Запусти скрипт:


```bash
python mirror_script.py --insecure           # игнорирует SSL ошибки
python mirror_script.py --dry-run            # эмулирует действия, без изменений
python mirror_script.py --dry-run --insecure
``````



## Скрипт

Проверяет существование каждого репозитория на target.
Если репозитория нет — создаёт его.
Если push mirror уже настроен — не добавляет его повторно.
При ошибках авторизации выводит диагностические сообщения.
