<div align="center">

# ⚡ StackBlitz × WebContainer

**Запускай Node.js прямо в браузере — без установки, без сервера, без ожидания.**

[![Live](https://img.shields.io/badge/demo-GitHub%20Pages-2ea44f?style=for-the-badge&logo=github)](https://ivanm696.github.io/stackblitz.com/)
[![StackBlitz](https://img.shields.io/badge/StackBlitz-1389FD?style=for-the-badge&logo=stackblitz&logoColor=white)](https://stackblitz.com)
[![WebContainer](https://img.shields.io/badge/WebContainer-API-8A2BE2?style=for-the-badge)](https://webcontainers.io)
[![Node.js](https://img.shields.io/badge/Node.js-in%20browser-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org)

[Демо](https://ivanm696.github.io/stackblitz.com/) · [Туториал](https://webcontainer-tutorial.pages.dev/1-webcontainer-api/1-express-app/1-what-we-are-building/) · [Как писать баг-репорты](./repro.md)

</div>

---

## 📖 О проекте

Репозиторий-заметка по **[StackBlitz](https://stackblitz.com)** — веб-редактору кода, в котором можно создавать, запускать и делиться веб-приложениями прямо из браузера.

В основе лежит **WebContainer** — среда выполнения Node.js, работающая целиком внутри вкладки браузера. Благодаря ей `npm install`, dev-сервер и терминал работают локально, без облачных виртуалок.

## ✨ Возможности

| | Что даёт |
|---|---|
| 🚀 **Мгновенный старт** | Проект открывается за секунды, зависимости ставятся в браузере |
| 🔒 **Изолированность** | Код выполняется в песочнице браузера на твоей машине |
| 🛠 **Полноценный dev-flow** | Терминал, npm, Vite, Express, DevTools |
| 🔗 **Делись ссылкой** | Любой проект — это URL, который открывается у других «как есть» |
| 🐞 **Отладка** | Можно ставить `debugger` и править файлы зависимостей |

## 🗂 Структура репозитория

```text
stackblitz.com/
├── .github/        # служебные файлы GitHub
├── CNAME           # настройки домена для GitHub Pages
├── package.json    # минимальный манифест проекта
├── repro.md        # как оформлять репро для проблем WebContainer
└── README.md       # вы здесь
```

## 🚦 Быстрый старт

```bash
git clone https://github.com/ivanm696/stackblitz.com.git
cd stackblitz.com
```

Хочешь попробовать WebContainer на практике — пройди туториал:
**[Что мы строим → Express-приложение в браузере](https://webcontainer-tutorial.pages.dev/1-webcontainer-api/1-express-app/1-what-we-are-building/)**

Минимальный пример запуска через API:

```js
import { WebContainer } from '@webcontainer/api';

const webcontainer = await WebContainer.boot();
await webcontainer.mount({
  'index.js': { file: { contents: "console.log('Привет из браузера!')" } },
});

const process = await webcontainer.spawn('node', ['index.js']);
process.output.pipeTo(new WritableStream({ write: (d) => console.log(d) }));
```

## 🐞 Нашёл баг в WebContainer?

Хороший репро — половина решения. Короткая памятка (подробности в [`repro.md`](./repro.md)):

1. **Проверь локально** — работает ли проект в обычном Node.
2. **Автозапуск команды** — добавь `.stackblitzrc`, чтобы ошибка воспроизводилась сразу.
3. **Изолируй вызов** — сведи пример до одного проблемного API-вызова.
4. **Прочитай ошибку** — часто там уже есть подсказка.

## 🔗 Полезные ссылки

- 🌐 [StackBlitz](https://stackblitz.com)
- 📚 [Документация платформы](https://developer.stackblitz.com/docs/platform/project-config)
- 🧪 [Minimal Reproducible Example](https://stackoverflow.com/help/minimal-reproducible-example)

---

<div align="center">

Сделано с ☕ by [**ivanm696**](https://github.com/ivanm696)

</div>
