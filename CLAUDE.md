# Lesson — Multi-Agent Pipeline

Проект для генерации frontend-дайджестов и сценариев видео с помощью цепочки специализированных агентов.

## Структура агентов

Агенты находятся в `.claude/agents/` (записи) и `.agents/` (полные инструкции).

| Агент | Роль |
|-------|------|
| `video-script-orchestrator` | Запускает полный пайплайн от новостей до готовых сценариев |
| `frontend-digest-agent` | Собирает frontend-новости, генерирует HTML-дайджест |
| `content-analyst` | Выбирает топ-3 новости для видео |
| `scriptwriter` | Пишет сценарий короткого видео по новости |
| `critique-agent` | Оценивает сценарий, возвращает на доработку или одобряет |
| `format-router` | Адаптирует сценарий под Reels и/или Shorts |

## Пайплайн

```
frontend-digest-agent → content-analyst → [scriptwriter → critique-agent (макс 2 итерации)] × 3 → format-router
```

## Вызов оркестратора

Для запуска полного цикла используй агента `video-script-orchestrator`:

```
Запусти video-script-orchestrator:
- date: 2026-05-06
- format: both
- output_dir: D:/lesson/video-scripts
```

## Выходные файлы

- HTML-дайджест: `D:/lesson/frontend-digest-YYYY-MM-DD.html`
- Сценарии: `D:/lesson/video-scripts/YYYY-MM-DD/scripts.md`
