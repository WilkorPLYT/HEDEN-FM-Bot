# 📝 Changelog

Wszystkie zmiany w projekcie **HEDEN Cargo Bot** są dokumentowane w tym pliku.

Format oparty na [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) 
i projekcie zgodnie z [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Planowane
- 🔄 Integracja z webhook dla powiadomień
- 📊 Nowy system raportowania
- 🎨 Redesign paneli embed
- ⚡ Optymalizacja performansu

---

## [1.0.0] - 2026-03-06

### 🎉 Release

Pierwszy stabilny release HEDEN Cargo Bota!

### ✨ Dodane

#### 🎯 System Zarządzania Zleceniami
- ✅ Panel tworzenia nowych zleceń
- ✅ System akceptacji/odrzucania
- ✅ Tracking statusu zlecenia
- ✅ System komentarzy do zleceń
- ✅ Eksport zleceń do Excel

#### 👥 Zarządzanie Pracownikami
- ✅ Panel zarządzania pracownikami
- ✅ System ról i uprawnień
- ✅ Awanse/obniżki rang
- ✅ System ostrzeżeń
- ✅ Historia zmian pracownika

#### 🎤 Voice Tracking
- ✅ Automatyczne śledzenie voice channels
- ✅ Statystyki godzin prowadzenia
- ✅ Heatmapy aktywności
- ✅ Raporty miesięczne z paginacją
- ✅ Eksport CSV

#### 🎬 Streamy & Multimedia
- ✅ Panel do ogłaszania streamów
- ✅ Integracja Twitch/YouTube/TikTok
- ✅ System logowania streamów
- ✅ Galeria fotoreportaży

#### 🆘 Wsparcie & Tickety
- ✅ System ticketów #1234
- ✅ Kategorie ticketów
- ✅ Transkrypty rozmów
- ✅ System pri

orytetów

#### 📊 Narzędzia & System
- ✅ Backup automatyczny MongoDB
- ✅ System logów działalności
- ✅ Web Dashboard (Express)
- ✅ REST API endpoints
- ✅ Docker support

#### 🛠️ Developer Features
- ✅ Hot reload (nodemon)
- ✅ Szczegółowe logi debug
- ✅ ESLint config
- ✅ Prettier formatting
- ✅ Environment configuration

### 🐛 Naprawione

- Naprawiono błąd przy duplikowaniu zleceń
- Naprawiono issue z timeoutem MongoDB
- Naprawiono renderowanie emoji w panelach
- Naprawiono błędy przy bulk operacjach

### 📚 Dokumentacja

- Dodano kompletny README.md
- Dodano PROJECT_SETUP.md
- Addano BOT_COMMANDS.md
- Dodano CONTRIBUTING.md
- Dodano poradnik troubleshooting

### 🔄 Zmienione

- Refaktor struktury kodu
- Modernizacja do Discord.js 14
- Zmiana systemów logowania
- Optymalizacja zapytań do MongoDB

---

## [0.5.0-beta] - 2026-02-20

### ✨ Dodane

- Beta release systemu ticketów
- Voice tracking foundation
- Podstawowe komendy slash
- Dashboard Express skeleton

### 🐛 Naprawione

- Problemy z autoryzacją Discord
- Race conditions w zapisie do DB

### ⚠️ Known Issues
- Voice tracking czasami duplikuje sesje
- Dashboard wymaga odświeżenia po zmianach

---

## [0.1.0-alpha] - 2026-01-15

### ✨ Dodane

- Inicjalna struktura projektu
- Połączenie Discord.js
- Połączenie MongoDB
- Setup Express.js
- Podstawowa konfiguracja

---

## Legenda Symboli

- ✨ Nowe funkcje
- 🐛 Naprawy błędów
- 📚 Dokumentacja
- ⚡ Optymalizacja
- 🔄 Zmiany
- ⚠️ Deprecation notices
- 🚀 Performance improvements
- 🎉 Duże releases

---

## Jak Raportować Zmiany

1. Utwórz `git commit` z prefixem:
   ```
   feat: dodaj nową funkcję
   fix: napraw bug #123
   docs: aktualizuj README
   ```

2. PR musi zawierać opis zmian

3. Po merge'u, maintainer aktualizuje CHANGELOG.md

---

## Maintenance

**Ostatnia aktualizacja:** 2026-03-06
**Maintainers:** 𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻, Daniel [Daniek.]

Obejrzyj [releases](https://github.com/WilkorPLYT/HedenCargoWeb/releases) na GitHubie
