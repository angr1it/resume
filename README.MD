# Modern Resume Theme — README

Проект использует тему [modern-resume-theme](https://github.com/sproogen/modern-resume-theme) для генерации одностраничного HTML-резюме на базе Jekyll с поддержкой PDF-экспорта и CI.

---

## Возможности

- Адаптивное HTML-резюме с иконками и разделами
- Публикация на GitHub Pages
- Генерация PDF-файла через Headless Chrome
- Конфигурация через `_config.yml`
- Автоматизация сборки через GitHub Actions

---

## Быстрый старт

### Установка локально

```bash
git clone https://github.com/yourname/resume
cd resume
bundle install
```

### Запуск

```bash
bundle exec jekyll build
python3 -m http.server 8000 --directory _site
```

Перейдите в браузере: http://localhost:8000

### Генерация PDF

```bash
google-chrome \
  --headless=new \
  --no-sandbox --disable-gpu \
  --disable-dev-shm-usage --no-zygote --no-first-run \
  --disable-features=Translate,DBus \
  --force-device-scale-factor=1 \
  --css-print-mode=print \
  --print-to-pdf=resume.pdf \
  --no-pdf-header-footer \
  --run-all-compositor-stages-before-draw \
  --timeout=10000 \
  http://localhost:8000/index.html
```

---

## GitHub Actions (CI)

Включена сборка PDF по каждому push в `main`. См. `.github/workflows/build_resume_pdf.yml`

---

## Структура `_config.yml`

```yaml
# Site
repository: sproogen/resume-theme
favicon: images/favicon.ico
version: 2

# Контактные данные
name: "Ваше имя"
title: "Ваша должность"
email: "email@example.com"
description: "Краткое описание"
website: "https://example.com"
darkmode: false

# Social
linkedin_username: yourname
github_username: yourgithub

# About section
about_profile_image: images/profile.jpg
about_content: |
  Краткое summary о себе

# Основной контент
content:
  - title: "Опыт работы"
    layout: list
    content:
      - layout: left
        title: "Компания"
        sub_title: "Должность"
        caption: "2020 — н.в."
        quote: >
          Вдохновляющая цитата о вашей роли
        description: |
          • Что вы сделали
          • Как улучшили процессы

  - title: "Навыки"
    layout: text
    content: |
      - Python, Docker
      - AWS, GitHub Actions

# Footer и билд
footer_show_references: true
remote_theme: sproogen/resume-theme
sass:
  sass_dir: _sass
  style: compressed
include:
  - assets/fonts
plugins:
  - jekyll-seo-tag
relative_links:
  enabled: true
```

---

## Поддержка

- `layout: list` — для проектов, опыта, образования
- `layout: text` — для навыков, описания, интересов
- `quote` — цитата под заголовком блока
- `additional_links` — с иконками Font Awesome
- `description` — поддерживает Markdown и изображения

---

## Полезные ссылки

- [Тема modern-resume-theme](https://github.com/sproogen/modern-resume-theme)
- [Документация Jekyll](https://jekyllrb.com/docs/)
- [Font Awesome Icons](https://fontawesome.com/icons)

---

Готово! Просто заполни `_config.yml`, запусти `jekyll serve` и экспортируй PDF.