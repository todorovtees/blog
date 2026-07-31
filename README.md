# Todorov Tees Blog — пълно ръководство (професионална версия)

Нов, изцяло преработен дизайн: "hang-tag" карти за статиите (като истински
етикет на дреха — с дупка, конец, прошита пунктирана рамка), QC-stamp
акцент, хартиен canvas фон, три нива типография (Anton за заглавия, Inter
за текст, JetBrains Mono за "етикетни" данни като номер на дроп и дата).

Технологията е същата като преди — чист HTML/CSS/JS на GitHub Pages,
статиите се пазят в `posts.json` в самия repo. Само дизайнът е сериозно
издигнат.

---

## ⚠️ Преди да качиш каквото и да е — прочети това

Миналия път имаше два проблема, които създадоха всичките мъчения:

1. **Папка/файл с грешен регистър на буквите** (`CSS` вместо `css`) — GitHub Pages различава главни от малки букви, за разлика от Windows/Mac.
2. **Drag & drop на папки в браузъра** понякога не пренася вярно вложената структура (под-папки се губят или преименуват).

**За да няма никакво повторение на това, най-силно препоръчвам качване през `git` командния ред** (стъпка 2 по-долу) вместо drag & drop през браузъра. Отнема 5 минути и е 100% сигурно. Ако наистина предпочиташ browser upload, инструкциите за него са в **Приложение А** най-отдолу — но следвай ги буква по буква.

---

## 1. Изтрий старото repo (препоръчително, за чист старт)

Тъй като предният опит остави файлове с грешен регистър на буквите, най-чисто е да започнем отначало:

1. Отвори `https://github.com/todorovtees/blog`
2. **Settings** (в самото repo, долу в списъка вляво или в горното меню на repo-то)
3. Scroll до най-долу → **Danger Zone → Delete this repository**
4. Потвърди с името на repo-то

Ако предпочиташ да не трием нищо, просто изтрий ръчно всички файлове в него (включително папката `assets`) преди да продължиш към стъпка 2, за да няма стари/дублирани файлове с грешен регистър.

## 2. Качване през `git` (сигурният начин)

Нужен ти е `git` инсталиран на компютъра (безплатно, ако нямаш: [git-scm.com](https://git-scm.com/downloads)).

1. Направи ново repo в GitHub: [github.com/new](https://github.com/new)
   - Име: `blog`
   - Public
   - **НЕ** добавяй README/gitignore/license автоматично (остави ги неотметнати)
   - Create repository

2. Разархивирай zip-а, който ти дадох, някъде на компютъра (напр. Desktop).

3. Отвори терминал (Mac: Terminal, Windows: Command Prompt или PowerShell, или Git Bash) и изпълни, ред по ред:

```bash
cd Desktop/todorov-blog-pro
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/todorovtees/blog.git
git push -u origin main
```

(Пътят `Desktop/todorov-blog-pro` смени с реалния път до разархивираната папка на твоя компютър.)

4. Ще те помоли за GitHub потребител/парола — вместо парола, GitHub изисква **Personal Access Token** (виж стъпка 5 по-долу — същият токен, който ти трябва и за admin панела, може да ползваш за push-ване).

Готово — целият проект, с правилната структура на файловете и папките (гарантирано без проблеми с главни/малки букви), е в GitHub.

## 3. Включи GitHub Pages

1. В repo-то: **Settings → Pages**
2. **Build and deployment → Source** → **Deploy from a branch**
3. Branch: `main`, папка `/ (root)` → **Save**
4. Изчакай 1-2 минути → сайтът е на `https://todorovtees.github.io/blog/`

**Провери веднага (много важно):**
Отвори `https://todorovtees.github.io/blog/assets/css/style.css` — трябва да видиш CSS код, започващ с `@import url(...)`. Ако видиш нещо различно (напр. `normalize.css` или GitHub грешка), спри и провери отново структурата на файловете, преди да продължиш.

## 4. Свържи домейна `blog.todorovtees.com`

Файлът `CNAME` вече съдържа `blog.todorovtees.com`.

**В GitHub (Settings → Pages → Custom domain):**
- Полето трябва вече да показва `blog.todorovtees.com`
- Изчакай зелената отметка "DNS check successful" (появява се, след като DNS записът по-долу се разпространи)
- Включи **Enforce HTTPS**, щом стане достъпно

**В GoDaddy (DNS настройки на todorovtees.com):**
1. **My Products → DNS** за `todorovtees.com`
2. Добави запис:
   - Тип: **CNAME**
   - Име (Host): `blog`
   - Стойност: `todorovtees.github.io`
   - TTL: по подразбиране
3. Запази. Разпространението отнема от няколко минути до няколко часа.

## 5. Направи Personal Access Token (за admin панела и/или git push)

1. GitHub → снимка на профила (горе вдясно) → **Settings**
2. Долу вляво: **Developer settings**
3. **Personal access tokens → Fine-grained tokens → Generate new token**
4. Име: `todorov-blog-admin`
5. **Repository access → Only select repositories** → избери `blog`
6. **Permissions → Repository permissions → Contents → Read and write**
7. **Generate token** → копирай веднага (показва се само веднъж!)

## 6. Как да добавяш статии

1. Отвори `https://blog.todorovtees.com/admin.html` (или `https://todorovtees.github.io/blog/admin.html`, докато чакаш DNS-а)
2. Първия път въведи:
   - **GitHub потребител**: `todorovtees`
   - **Repo**: `blog`
   - **Branch**: `main`
   - **Token**: токенът от стъпка 5
3. "Свържи се" — токенът се пази само в браузъра ти (сесийно)
4. Оттам: добавяш, редактираш, триеш статии; всяко записване прави нов commit в GitHub

---

## Финален чеклист

- [ ] `https://todorovtees.github.io/blog/` показва стилизирания сайт (не гол HTML)
- [ ] `https://todorovtees.github.io/blog/assets/css/style.css` показва CSS код, не грешка
- [ ] `https://blog.todorovtees.com/` работи (след DNS разпространение)
- [ ] `admin.html` се свързва успешно и виждаш таблицата със статии
- [ ] Пробвай да добавиш тестова статия и провери, че се появява на живо в блога

---

## Приложение А — качване през браузъра (алтернатива на git)

Ако наистина не искаш да инсталираш git:

1. Разархивирай zip-а на компютъра
2. В GitHub repo-то → **Add file → Upload files**
3. Отвори разархивираната папка `todorov-blog-pro` **отвътре** (не провлачвай самата папка `todorov-blog-pro` — влез в нея и провлачи **съдържанието ѝ**: `index.html`, `post.html`, `admin.html`, `posts.json`, `CNAME`, `.nojekyll`, `README.md` и папката `assets` — всичко едновременно, маркирано)
4. Уверете се, че под "assets" в прегледа на GitHub преди commit виждаш вложените `css/` и `img/` — ако не ги виждаш, отвори `assets` папката отделно и качи `css/` и `img/` в нея поотделно
5. Commit changes
6. **Задължително провери:** отвори `github.com/todorovtees/blog/tree/main/assets/css` — трябва да видиш файл, кръстен точно `style.css` (малки букви). Ако папката се казва `CSS` (главни), преименувай я: отвори файла → молив (Edit) → в полето с пътя горе смени `CSS/style.css` на `css/style.css` → Commit.

---

## Бележки

- Съдържанието на статиите поддържа основен HTML (`<p>`, `<b>`, `<img>`, `<h2>` и т.н.).
- Снимките се качват автоматично в `assets/uploads/` в repo-то при запис на статия през admin панела.
- Полето "Категория" е по избор — ако го оставиш празно, просто не се показва в статията.
- Ако искаш по-визуален редактор за писане (WYSIWYG вместо чист HTML), кажи ми и ще добавя лек такъв (напр. вграден TipTap/Quill редактор).
