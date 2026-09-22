Разверни на этом хосте публичную витрину агентов из репозитория:

https://github.com/cuthbertnogood/grok-bot-observatory

Сделай так:

1. Клонируй репо в домашнюю директорию пользователя, который крутит OpenClaw / Grok Bot. Не клади в iCloud.
2. Не открывай наружу OpenClaw Control UI и порт 18789.
3. Подними статический сервер только этой папки на 127.0.0.1:8088:
   python3 -m http.server 8088 --bind 127.0.0.1
4. Если на хосте уже есть Caddy / Tailscale Serve — повесь на витрину отдельный URL с аутентификацией. Это витрина, не админка.
5. Если доступен http://127.0.0.1:18789/health — добавь в index.html перед </body>:
   <script>window.OBSERVATORY = { healthUrl: "http://127.0.0.1:18789/health" };</script>
6. Если знаешь реальных агентов этого хоста (имена, модели, каналы из ~/.openclaw), обнови agents.json. Комнаты: warroom, kitchen, desk-a, desk-b, desk-c, lounge, racks, studio.
7. Поставь автозапуск сервера витрины (launchd или systemd user), чтобы страница жила после ребута.
8. В ответ напиши: путь клонирования, URL витрины, как открыть с телефона, и что gateway по-прежнему только localhost.

Не ставь Grafana, Docker и тяжёлые стеки без отдельной просьбы. Intel Mac не нагружать.
