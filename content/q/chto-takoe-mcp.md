---
title: "Что такое MCP и зачем он нужен?"
description: "MCP (Model Context Protocol) — стандарт для подключения инструментов к AI-агентам. Браузер, базы данных, API — всё это агент получает через MCP."
date: 2026-03-27
lastmod: 2026-03-27
tags: ["mcp", "claude-code", "инструменты", "агенты"]
categories: ["инструменты"]
question: "Везде пишут про MCP. Что это такое и как это использовать в вайбкодинге?"
short_answer: "MCP — это способ дать AI-агенту доступ к внешним инструментам: браузеру, базе данных, файловой системе, API. Подключаешь MCP-сервер — и агент умеет делать то, что раньше не мог."
thread_url: ""
opinions_count: 5
has_code: true
difficulty: "средний"
draft: false
---

## Мнения из сообщества

### @vibecoder1

> MCP изменил мой воркфлоу: подключил Playwright MCP — агент сам открывает браузер, кликает, делает скриншоты. Теперь UI-задачи решаются без моего участия.

Практический пример: браузерная автоматизация через MCP.

### @developer1

> Самое полезное для меня — MCP для баз данных. Агент напрямую делает SELECT, видит реальные данные, дебажит запросы. Раньше приходилось копировать схему вручную.

MCP как прямой доступ к данным для контекста.

### @vibecoder2

> Важно понять: MCP — это протокол, не конкретный инструмент. Anthropic его создал, но MCP-серверы пишет кто угодно. Уже сотни готовых серверов: GitHub, Slack, Notion, Linear.

Экосистема: открытый протокол с растущим сообществом.

### @senior_dev1

> Написал свой MCP-сервер за пол-дня. Агент теперь умеет работать с нашим внутренним API. Протокол простой — JSON-RPC поверх stdio или HTTP.

Расширяемость: любой разработчик может создать свой MCP-сервер.

## Код

```json
// ~/.claude/settings.json — подключение MCP-серверов
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp"]
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/project"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your-token"
      }
    }
  }
}
```

```bash
# Проверить доступные MCP инструменты в сессии
claude --mcp-debug

# Запустить с конкретным MCP-сервером
claude --mcp-server playwright
```

## Популярные MCP-серверы

| Сервер | Что даёт агенту |
|--------|----------------|
| `@playwright/mcp` | Браузер: навигация, клики, скриншоты |
| `@modelcontextprotocol/server-github` | GitHub: issues, PR, code |
| `@modelcontextprotocol/server-filesystem` | Файловая система |
| `@modelcontextprotocol/server-postgres` | PostgreSQL запросы |
| `@modelcontextprotocol/server-slack` | Slack сообщения |

## Итог

MCP нужен когда агенту не хватает стандартных инструментов. Базовый набор — браузер, база данных, внешние API. Найди готовый сервер в реестре MCP или напиши свой — протокол открытый и простой.
