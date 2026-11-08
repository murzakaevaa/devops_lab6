# Lab 6. Ansible Roles + CI (П06)

## Что было сделано
1. Создана Ansible-роль `nginx-vhosts`, которая устанавливает веб-сервер Nginx.
2. Роль настраивает виртуальные хосты (vhosts) на основе переменной `sites`.
3. Для каждого сайта (etis.com, fizfak.com, mehmat.ru) из шаблона `index.html.j2` создаётся индексная страница.
4. Для каждого сайта из шаблона `site.conf.j2` создаётся конфигурация веб-сервера.
5. Проверка работы выполнена через `curl` с подменой заголовка `Host`.
6. Настроены CI-пайплайны GitHub Actions: тестовый сценарий и проверка кода линтером (Ansible Lint).

## Файлы в репозитории
- `inventory.ini` — инвентарный файл со списком хостов.
- `playbook.yml` — главный плейбук, использующий роль.
- `run_playbook.sh` — скрипт для запуска плейбука.
- `roles/nginx-vhosts/tasks/main.yml` — задачи роли (установка Nginx, создание папок, копирование).
- `roles/nginx-vhosts/handlers/main.yml` — обработчик (перезапуск Nginx).
- `roles/nginx-vhosts/templates/site.conf.j2` — шаблон конфигурации виртуального хоста.
- `roles/nginx-vhosts/templates/index.html.j2` — шаблон стартовой страницы.
- `.github/workflows/devops_course_pipeline.yml` — CI-пайплайн (тестовый).
- `.github/workflows/lint.yml` — CI-пайплайн (Ansible Lint).

## Скриншоты (папка `скрины`)

| Файл | Что изображено на скриншоте |
| :--- | :--- |
| `01-structure.png` | Структура папок роли (`ls -R roles`) |
| `02-playbook-run.png` | Выполнение задач плейбука (Install nginx, Create folders) |
| `03-playbook-recap.png` | Итоговый PLAY RECAP (failed=0) |
| `04-curl-vhosts.png` | Проверка трёх виртуальных хостов через `curl` |
| `05-git-init.png` | Инициализация репозитория и привязка к GitHub |
| `06-git-commit.png` | Добавление файлов и создание коммита |
| `07-git-push.png` | Отправка изменений на GitHub |
| `08-actions-list.png` | Вкладка Actions со списком workflow |
| `09-repo-main.png` | Главная страница репозитория со списком файлов |
