# Satelite

<p align="center">
  <strong>Спутник в небе — связь без границ.</strong><br/>
  Лёгкий и красивый десктопный клиент sing-box / Xray / mihomo
</p>

<p align="center">
  <a href="https://github.com/zn0wii/satelite-proxy/stargazers"><img src="https://img.shields.io/github/stars/zn0wii/satelite-proxy?style=social" alt="Звёзды" /></a>
  &nbsp;
  <img src="https://img.shields.io/badge/macOS-Apple%20Silicon%20%7C%20Intel-111111?logo=apple&logoColor=white" alt="macOS" />
  <img src="https://img.shields.io/badge/Windows-x64-0078D4?logo=windows&logoColor=white" alt="Windows" />
  &nbsp;
  <img src="https://img.shields.io/badge/Linux-x64-FCC624?logo=linux&logoColor=black" alt="Linux" />
  <img src="https://img.shields.io/badge/Tauri-2-24C8DB?logo=tauri&logoColor=white" alt="Tauri" />
  <img src="https://img.shields.io/badge/Rust-%23000000?logo=rust&logoColor=white" alt="Rust" />
  <img src="https://img.shields.io/badge/License-Apache%202.0-green.svg" alt="Лицензия" />
</p>

Импорт подписок, переключение между тремя ядрами, маршрутизация по правилам, цепочки прокси, умный DNS, системный прокси / TUN, постоянное присутствие в трее — всё, что нужно на каждый день.  
Он **достаточно лёгкий, достаточно стабильный и достаточно красивый**.

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/banner-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="./assets/banner-light.png">
    <img src="./assets/banner-light.png" alt="Баннер">
  </picture>
</p>

## Почему Satelite

Прокси-клиентов уже достаточно. Satelite не хочет быть ещё одной оболочкой с «более длинным списком функций», а собирает три ядра — **sing-box / Xray / mihomo** — в один спутник, который действительно можно держать на рабочем столе:

| Что для вас действительно важно | Как это делает Satelite |
| --- | --- |
| **Размер и память** | Tauri 2 + Rust, а не целое семейство Chromium. Свёрнутый в трей, он должен забываться, а не съедать половину памяти. При сворачивании в трей можно включить «режим низкой памяти», выгружая интерфейс. |
| **Не хочется быть привязанным к одному ядру** | sing-box (по умолчанию), Xray, mihomo (Clash Meta) переключаются одной кнопкой на странице настроек; подписки, правила и DNS следуют за этим. Также можно включить «многоядерный режим»: основной слушатель sing-box остаётся без изменений, а указанные узлы по протоколу делегируются вспомогательным процессам Xray / mihomo. |
| **Узлы падают** | Три способа выбора маршрута: вручную, urltest ядра, интеллектуальное переключение на стороне приложения. Умный режим пассивно отслеживает журналы соединений + выполняет проверки по требованию, автоматически обходя сбои, а не постоянно сканирует всю таблицу. |
| **Не хочется тонуть в конфигурации** | «Простой режим» оставляет только соединения / узлы / трафик; «профессиональный режим» открывает правила, DNS, Hosts, журналы. Одно и то же ядро — два ритма. |
| **Интерфейс — тоже функция** | Эффект матового стекла, светлая / тёмная тема, множество акцентных цветов (включая пользовательский выбор), три варианта анимации главной страницы (частицы / классика / смайлик). В ту секунду, когда открывается окно, должно быть понятно: это не админ-панель 2018 года. |
| **Работает сразу из коробки** | Три ядра автоматически скачиваются и обновляются, при неожиданном завершении автоматически перезапускаются; подписки Clash, sing-box JSON, share-ссылки, `clash://` / `sing-box://` / `singbox://` импортируются из браузера одним щелчком. |

> Спутник вращается вокруг вас, а не вы вокруг YAML.

---

## Что он умеет

- **Подписки и конфигурация**: подписки Clash, sing-box JSON, share-ссылки узлов; импорт по ссылке / из файла / через глубокие ссылки браузера; подписки можно обновлять по расписанию. Также можно использовать полную конфигурацию sing-box напрямую как рабочую.
- **Свободное переключение трёх ядер**: sing-box (по умолчанию) · Xray · mihomo (Clash Meta), на странице настроек можно скачать / обновить / переключить одним щелчком. Кроме того, «многоядерный режим» позволяет основному слушателю sing-box оставаться на месте и делегировать узлы по протоколам вспомогательным процессам Xray / mihomo — несколько ядер работают одновременно.
- **Протоколы**: SS, VMess, VLESS, Trojan, Hysteria2, TUIC, AnyTLS, WireGuard, SOCKS5 и др.; неподдерживаемые протоколы автоматически фильтруются по текущему ядру, не создавая конфигураций, к которым нельзя подключиться.
- **Цепочки прокси**: пул узлов + многоскачковая цепная маршрутизация (вход → транзит → выход), редактирование перетаскиванием на холсте в стиле схемы метро, диагностика реального выхода на каждом участке по одному щелчку.
- **Умный выбор маршрута**: вручную · интеллектуальное обход препятствий приложением · urltest ядра; выбор по ситуации, без привязки к одной стратегии.
- **Маршрутизация по правилам**: несколько наборов правил (локальные / удалённые `.srs`), приоритет перетаскиванием; политика может задавать группу узлов, фильтр по ключевым словам или указывать на цепочку прокси; встроенные правила для китайских сайтов / китайских IP / зарубежных ресурсов; резервный выход: прокси / напрямую / блокировка. Переключение режимов «правила» / «глобальный» / «напрямую» одним щелчком.
- **DNS и Hosts**: DoH / DoT / FakeIP, наборы DNS-правил, системные Hosts, резолвер по умолчанию; встроенная DNS-диагностика, пошаговое построение пути разрешения для каждого домена, локальные / китайские пути выделяются красным для предупреждения о риске утечки.
- **Сетевая диагностика**: на главной странице одним щелчком измеряются задержка текущего узла + IP выхода, четыре IP-источника проверяются наперегонки, после переключения узла проверка выполняется автоматически.
- **Управление узлами**: группировка по подписке / протоколу / стране, поиск и сортировка; TCP Ping для проверки доступности, реальная задержка для всей цепочки, тест отдельного узла по клику — сразу по нажатию, результаты по каждому узлу передаются потоково.
- **Системный прокси / TUN**: системный прокси перехватывается одним щелчком; TUN (system / gvisor / mixed); обход локальной сети, опциональный TUN IPv6, можно перехватывать QUIC.
- **Порты**: mixed / Clash API (ключ доступа опционален), несколько слушателей, разрешение локальной сети.
- **Соединения и трафик**: активные соединения, закрытые, неудачные запросы, направление трафика, автоматическое определение имени процесса.
- **Постоянное присутствие в трее**: при закрытии окно сворачивается в трей, автозапуск, тихий запуск, опциональная иконка в трее; ядро работает в фоне, окно может исчезать.
- **Самоуправление ядрами**: три ядра автоматически загружаются и обновляются, при неожиданном завершении автоматически перезапускаются; не нужно самому искать бинарники и сверять версии.
- **Двуязычные тексты (китайский / английский)**, светлая / тёмная тема, множество акцентных цветов.

<p align="center">
  <img src="assets/1.png" alt="Обзор Windows" width="760" />
  &nbsp;
  <img src="assets/3.png" alt="Маршрутизация по правилам" width="760" />
</p>
<p align="center">
  <img src="assets/2.png" alt="Настройки приложения" width="760" />
</p>

## 🖥 Поддержка платформ

| Платформа            | Статус   |
| --------------- | ------ |
| macOS Apple Silicon | ✅ Поддерживается |
| macOS Intel     | ✅ Поддерживается |
| Windows         | ✅ Поддерживается |
| Linux           | ✅ Поддерживается |
| Android         | 🧪 Ранняя стадия · [Interstellar](https://github.com/zn0wii/interstellar-proxy) (отдельный проект, см. ниже) |

> Satelite Proxy всё ещё активно разрабатывается; перед обновлением сохраняйте резервные копии важных файлов конфигурации.

### macOS сообщает «Повреждено, невозможно открыть»

Неподписанные приложения блокируются карантинной отметкой Gatekeeper в macOS. Выполните в терминале следующую команду, после чего приложение можно открыть:

```bash
sudo xattr -d com.apple.quarantine /Applications/Satelite.app
```

## 📱 Android-версия: Interstellar

Спутник летит на мобильные устройства — **[Interstellar](https://github.com/zn0wii/interstellar-proxy)** — это Android-версия Satelite.

Важно отметить: хотя он позиционируется как «мобильная версия», это не порт десктопной версии, а **самостоятельный проект с новой реализацией**. Interstellar использует часть дизайнерских идей Satelite, но интерфейс и архитектура полностью переработаны с нуля под мобильные устройства.

Interstellar пока находится на ранней стадии; функции и опыт быстро развиваются. Приглашаем [посмотреть](https://github.com/zn0wii/interstellar-proxy), попробовать и оставить отзыв.

## 🛠 Технологический стек

- **Ядра**: [sing-box](https://github.com/SagerNet/sing-box) (по умолчанию) · [Xray](https://github.com/XTLS/Xray-core) · [mihomo](https://github.com/MetaCubeX/mihomo) (Clash Meta)
- **Десктопный фреймворк**: [Tauri 2](https://tauri.app/)
- **Фронтенд**: React + TypeScript + Vite
- **Бэкенд**: Rust

## 📦 Разработка

```bash
# Установка зависимостей
pnpm install

# Запуск режима разработки (при отсутствии ядер или встроенных наборов правил приложение скачает их само)
pnpm tauri dev
```

Скрипт сборки по умолчанию включает в установочный пакет три ядра (sing-box / Xray / mihomo с соответствующими geodata) и три встроенных удалённых набора правил (`.srs`); при отсутствии они скачиваются автоматически; `--singbox-only` / `-SingboxOnly` позволяют уменьшить пакет до одного sing-box. Также можно сначала вручную положить их в `src-tauri/resources/`:

```bash
# macOS Apple Silicon / Intel
./scripts/fetch-bundled-core-darwin-arm64.sh    # или fetch-bundled-core-darwin-amd64.sh
./scripts/fetch-bundled-xray-darwin-arm64.sh    # ядро Xray + geodata (есть версия amd64)
./scripts/fetch-bundled-mihomo-darwin-arm64.sh  # ядро mihomo + geodata (есть версия amd64)
./scripts/fetch-bundled-rule-sets.sh
```

```bash
# Linux amd64
./scripts/fetch-bundled-core-linux-amd64.sh
./scripts/fetch-bundled-xray-linux-amd64.sh
./scripts/fetch-bundled-mihomo-linux-amd64.sh
./scripts/fetch-bundled-rule-sets.sh
```

```powershell
# Windows x64
pwsh scripts/fetch-bundled-core-windows-amd64.ps1
pwsh scripts/fetch-bundled-xray-windows-amd64.ps1
pwsh scripts/fetch-bundled-mihomo-windows-amd64.ps1
# Наборы правил загружаются вместе с build-windows.ps1
```

### macOS DMG

Выполнять на **macOS** (не обязательно на той же архитектуре: Apple Silicon может кросс-компилировать под Intel):

```bash
# Сборка под архитектуру текущей машины
./scripts/build-dmg.sh

# Apple Silicon
./scripts/build-dmg.sh --arch arm64

# Intel (x86_64)
./scripts/build-dmg.sh --arch intel
# Эквивалентно:
./scripts/build-dmg-intel.sh
```

По умолчанию скрипт загружает и включает в установочный пакет три ядра (sing-box / Xray / mihomo) (`--singbox-only` позволяет уменьшить до одного sing-box). Результат находится в:

`src-tauri/target/<aarch64|x86_64>-apple-darwin/release/bundle/dmg/`

### Установочный пакет Windows

```powershell
pwsh scripts/build-windows.ps1                    # Установочный пакет NSIS (по умолчанию, три ядра)
pwsh scripts/build-windows.ps1 -Bundle msi        # MSI
pwsh scripts/build-windows.ps1 -Bundle portable   # Портативная версия: zip для распаковки и использования, данные рядом с exe
pwsh scripts/build-windows.ps1 -SingboxOnly       # Облегчённая: только sing-box
```

Результат находится в `src-tauri/target/release/bundle/nsis/` или `.../msi/` (портативная версия в `.../portable/`). Ядра, не включённые в установочный пакет, можно в любой момент скачать онлайн на странице настроек.

### Linux AppImage

Выполнять на **Linux x64**. Сначала установите системные зависимости (Ubuntu / Debian, для других дистрибутивов см. [Tauri prerequisites](https://tauri.app/start/prerequisites/)):

```bash
sudo apt-get install -y libwebkit2gtk-4.1-dev libappindicator3-dev librsvg2-dev patchelf
```

Затем соберите (скрипты загрузки трёх ядер см. выше; при их отсутствии нужно выполнить заранее):

```bash
pnpm tauri build --config src-tauri/tauri.linux.conf.json
```

Результат находится в `src-tauri/target/release/bundle/appimage/` (`*.AppImage`).

---

Если всё удобно, поставьте [Star](https://github.com/zn0wii/satelite-proxy) — спутник будет лететь немного стабильнее.

## Дружественные ссылки

- **Сообщество единомышленников** [linux.do](https://linux.do/)

## История звёзд

<a href="https://www.star-history.com/?repos=zn0wii%2Fsatelite-proxy&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=zn0wii/satelite-proxy&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=zn0wii/satelite-proxy&type=date&legend=top-left" />
   <img alt="График истории звёзд" src="https://api.star-history.com/chart?repos=zn0wii/satelite-proxy&type=date&legend=top-left" />
 </picture>
</a>
