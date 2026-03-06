<div align="center">

# � HEDEN Cargo - Discord Bot

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Discord.js](https://img.shields.io/badge/Discord.js-14+-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.js.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-13AA52?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)](https://discord.com/users/446740090757316608)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](#-licencja)

<br>

### 🚚 Zaawansowany bot Discord do zarządzania zleceniami spedycyjnymi i obsługi społeczności HEDEN Cargo

<br>

[✨ Funkcje](#-funkcje) •
[📸 Screenshots](#-screenshots) •
[🛠️ Technologie](#️-technologie) •
[📞 Kontakt](#-kontakt)

<br>

---

</div>

<br>

## ✨ Funkcje

<table>
<tr>
<td>

### � Zarządzanie Zleceniami
- ✅ System zlecen spedycyjnych
- ✅ Akceptacja/odrzucanie zleceń
- ✅ Tracking statusu zleceń
- ✅ Komentarze do zleceń

</td>
<td>

### 👥 Zarządzanie Pracownikami
- ✅ Panel zarządzania pracownikami
- ✅ System awansów i zwolnień
- ✅ System ostrzeżeń pracowników
- ✅ Raporty miesięczne z paginacją

</td>
</tr>
<tr>
<td>

### 🎤 Voice Tracking & Analityka
- ✅ Śledzenie czasu na kanałach voice
- ✅ Statystyki aktywności głosowej
- ✅ Heatmapy aktywności
- ✅ Analiza trendu użytkowania

</td>
<td>

### 🎬 Streamy & Multimedia
- ✅ Panel streamów (Twitch/YouTube/TikTok)
- ✅ System ogłoszeń społeczności
- ✅ Integracja streamerów
- ✅ Galeria zdjęć i fotoreportaż

</td>
</tr>
</table>

<br>

## 📸 Screenshots

<div align="center">

### � Panel Zarządzania Zleceniami

<img src="screenshots/zlecenia.png" alt="Ticket system" width="700">

<br><br>

### 👥 Bot na Discord w akcji

<img src="screenshots/discord.png" alt="Discord bot" width="400">

<br><br>

### 📈 Raporty i Statystyki

<img src="screenshots/raporty.png" alt="Reports" width="500">

</div>

<br>

## 🎨 Przykładowe Logi

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚙️  HEDEN Cargo Bot - Uruchamianie...
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[OK] ✓ Zalogowano jako HEDEN Cargo#1234
[INFO] Discord.js v14.8.0
[INFO] Serwer: HEDEN Cargo Sp. z o.o.
[INFO] MongoDB: Połączone
[TICKET] 🎫 System ticketów załadowany
[VOICE] 🎤 Voice tracking aktywny
[COMMAND] 🎯 Zarejestrowano 42 komendy slash
[OK] ✓ Bot gotowy do pracy!

[TICKET] 🎫 Nowy ticket #001 - Rekrutacja
[VOICE] 🔊 Użytkownik 𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻 dołączył (1h 23m)
[SPEDYCJA] 🚚 Nowe zlecenie #045 - Dostawa Kraków
[REPORT] 📊 Raport wygenerowany dla marca 2026
```

<br>

## 🛠️ Technologie

<div align="center">

[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Discord.js](https://img.shields.io/badge/Discord.js-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.js.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-13AA52?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express.js](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

</div>

### Stack Techniczny:

- **Backend:** Node.js 18+ z Discord.js 14
- **API:** Express.js z CORS i middleware
- **Baza Danych:** MongoDB 4.4+ (Atlas lub self-hosted)
- **Voice Tracking:** Integracja audio Discord
- **HTTP Requests:** Axios (async requests)
- **Containerization:** Docker & Docker Compose

<br>

## 🚀 Szybki Start

### Wymagania
- Node.js 18+
- npm lub yarn
- MongoDB (Atlas lub lokalnie)
- Token bota Discord
- Discord.js 14+

### Instalacja

```bash
# Klonowanie repozytorium
git clone https://github.com/WilkorPLYT/HedenCargoWeb.git
cd HedenCargoWeb

# Instalacja zależności
npm install

# Konfiguracja
cp .env.example .env
# Edytuj .env i dodaj swoje tokeny

# Uruchamianie
npm start
```

<br>

## ⚙️ Konfiguracja

### Plik `.env`

```env
# Discord
DISCORD_TOKEN=twoj_token_bota
APPLICATION_ID=id_aplikacji
GUILD_ID=id_twojego_serwera
OWNER_ID=twoje_id_discorda

# MongoDB
MONGODB_URI=mongodb+srv://user:password@cluster.mongodb.net/hedencargo

# Konfiguracja
PREFIX=$
PORT=6969
```

### Plik `config.js`

- **Kanały** - Nazwy kanałów Discord
- **Role** - Role do zarządzania uprawnieniami
- **Emoji** - Custom emoji serwera
- **Streameraom** - Dane streamerów
- **Uprawnienia** - Dostęp do funkcji

<br>

## 📁 Struktura Projektu

```
HedenCargoWeb/
├── 📄 index.js                 # Główny plik bota
├── 📄 server.js                # Serwer Express
├── 📄 config.js                # Centralna konfiguracja
├── 📄 package.json             # Zależności
├── 📄 .env.example             # Wzorzec zmiennych
├── 📄 README.md                # Ta dokumentacja
├── 📄 BOT_COMMANDS.md          # Dokumentacja komend
├── 📄 Dockerfile               # Docker config
├── 📁 express_files/
│   ├── controller.js           # Kontrolery
│   ├── router.js               # Routery
│   └── mongo_schemas.js        # Schematy
├── 📁 src/
│   ├── commands/               # Komendy bota
│   ├── events/                 # Event handlery
│   ├── models/                 # Modele danych
│   ├── services/               # Usługi
│   └── utils/                  # Funkcje pomocnicze
└── 📁 scripts/
    └── clear_db.js             # Skrypty utility
```

<br>

## 💼 Dostępne na zamówienie

<div align="center">

### 🎯 Chcesz takiego bota dla swojej firmy?

<br>

| Pakiet | Opis |
|--------|------|
| 🎫 **Basic** | Bot do ticketów + voice tracking |
| 🚗 **Professional** | Pełny system zarządzania + reporting |
| 🏢 **Enterprise** | Wsparcie + hosting + utrzymanie |

<br>

### 📞 Skontaktuj się po wycenę!

</div>

<br>

## 📞 Kontakt

<div align="center">

### Zainteresowany? Napisz do nas!

<br>

[![Discord](https://img.shields.io/badge/Discord-𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/users/446740090757316608)
[![GitHub](https://img.shields.io/badge/GitHub-WilkorPLYT-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/WilkorPLYT)

<br>

| Platforma | Kontakt |
|-----------|---------|
| 💬 **Discord** | [𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻](https://discord.com/users/446740090757316608) (ID: `446740090757316608`) |
| 🐙 **GitHub** | [@WilkorPLYT](https://github.com/WilkorPLYT) |
| 👨‍💻 **Co-Developer** | [@daniekdan](https://github.com/daniekdan) - Daniel [Daniek.] |

</div>

<br>

## 📄 Licencja

<div align="center">

**MIT License - Wolne użytkowanie w projektach prywatnych i komercyjnych**

Autor: WilkorPLYT & Daniel [Daniek.]
Copyright © 2024-2026 HEDEN Cargo Sp. z o.o.

</div>

<br>

---

<br>

## 👨‍💻 Autorzy

<div align="center">

[![Stworzony przez](https://img.shields.io/badge/Stworzony%20przez-WilkorPLYT%20%26%20Daniel-blueviolet?style=for-the-badge)](https://github.com/WilkorPLYT)

<br>

Stworzony z ❤️ przez **𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻** & **Daniel [Daniek.]** dla **HEDEN Cargo Sp. z o.o.**

<br>

[![GitHub](https://img.shields.io/badge/GitHub-WilkorPLYT-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/WilkorPLYT)
[![GitHub](https://img.shields.io/badge/GitHub-daniekdan-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/daniekdan)
[![Discord](https://img.shields.io/badge/Discord-𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/users/446740090757316608)

<br>

---

<br>

**⭐ Jeśli podoba Ci się ten projekt, zostaw gwiazdkę! ⭐**

</div>