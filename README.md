# GROK BOT HOST — обсерватория агентов

Публичная витрина работы агентов на хосте Grok Bot / OpenClaw.

Это **не** Control UI и **не** админка gateway. Сюда можно пускать браузер. Сам OpenClaw (`127.0.0.1:18789`) наружу не открывать.

Репозиторий: https://github.com/cuthbertnogood/grok-bot-observatory

## Файлы

- `index.html` — страница
- `agents.json` — состав смены, комнаты, задачи
- `office.jpg` — опциональная карта офиса (если нет, рисуется сетка)
- `BOT_PROMPT.md` — текст, который можно отдать Grok Bot / OpenClaw

## Развёртывание на хосте

```bash
cd ~
git clone https://github.com/cuthbertnogood/grok-bot-observatory.git
cd grok-bot-observatory
python3 -m http.server 8088 --bind 127.0.0.1
```

Открыть: `http://127.0.0.1:8088`

Наружу отдавай только этот порт через Tailscale Serve или Caddy с basic auth. Не проксируй `18789`.

Опционально живой health (только localhost):

```html
<script>
  window.OBSERVATORY = { healthUrl: "http://127.0.0.1:18789/health" };
</script>
```

вставить перед закрывающим `</body>` в `index.html`.

## Состав смены

Править `agents.json`. Комнаты: `warroom`, `kitchen`, `desk-a`, `desk-b`, `desk-c`, `lounge`, `racks`, `studio`.
