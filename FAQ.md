# ❓ Frequently Asked Questions (FAQ)

Odpowiedzi na najczęstsze pytania dotyczące **HEDEN Cargo Bot**.

---

## 🚀 Ogólne

### Jak zainstalować bota?

1. Przejdź do [PROJECT_SETUP.md](PROJECT_SETUP.md) - pełny poradnik instalacji
2. Alternatywnie użyj Docker: `docker-compose up -d`

**Szybki start:**
```bash
git clone https://github.com/WilkorPLYT/HedenCargoWeb.git
cd HedenCargoWeb
npm install
cp .env.example .env
# Edytuj .env z tokenami
npm start
```

---

### Jaka jest licencja?

**MIT License** - możesz używać w projektach prywatnych i komercyjnych.
[Przeczytaj LICENSE](LICENSE)

---

### Czy mogę wnieść wkład?

**TAK!** Każdy wkład jest mile widziany. Przeczytaj [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 🔧 Instalacja & Konfiguracja

### Jak se konfiguruje Discord Token?

1. Przejdź na [Discord Developer Portal](https://discord.com/developers/applications)
2. Utwórz nową aplikację
3. Przejdź na zakładkę "Bot" i skopiuj token
4. Wklej do `.env` jako `DISCORD_TOKEN`

[Tutaj pełny poradnik](PROJECT_SETUP.md#-konfiguracja-discord)

---

### Jak podłączyć MongoDB?

**Opcja 1: Lokalnie**
```bash
# Zainstaluj MongoDB Community Edition
# Uruchom: mongod
# W .env: MONGODB_URI=mongodb://localhost:27017/hedencargo
```

**Opcja 2: MongoDB Atlas (Cloud)**
```
1. Przejdź na https://www.mongodb.com/cloud/atlas
2. Utwórz darmowy cluster
3. Skopiuj connection string
4. Wklej do .env jako MONGODB_URI
```

[Pełny poradnik](PROJECT_SETUP.md#-konfiguracja-mongodb)

---

### Dlaczego bot nie startuje?

Wykonaj kroki troubleshooting:

```bash
# 1. Sprawdź Node.js
node --version  # Powinna być 18+

# 2. Zainstaluj zależności
npm install

# 3. Sprawdź .env
cat .env  # Powinna mieć wszystkie wymagane zmienne

# 4. Sprawdź logi
npm start  # Szukaj błędów w konsoli
```

[Więcej](PROJECT_SETUP.md#-troubleshooting)

---

### Jak uruchomić w trybie development?

```bash
npm run dev
```

To uruchamia bot z **hot reload** (restartuje automatycznie przy zmianach kodu).

---

## 🎯 Funkcje & Komendy

### Jakie są dostępne komendy?

Przeczytaj [BOT_COMMANDS.md](../HedenCargoWeb/BOT_COMMANDS.md) dla pełnej listy.

Główne komendy:
- `/ticket` - Utwórz ticket
- `/voice-stats` - Pokaż statystyki voice
- `$pomoc` - Panel pomocy
- `$spedycja` - Panel spedycji

---

### Jak dodać custom emoji?

W `config.js`:

```javascript
const emojis = {
  success: '<:checkmark:123456789>',  // Custom emoji
  error: '❌',                         // Unicode emoji
  voice: '🎤'
};
```

Aby pobrać ID customowego emoji:
```
1. W Discord - Włącz Developer Mode
2. PPM na emoji w kanale
3. "Copy Custom Emoji"
4. Skopiuj ID z `<:name:ID>`
```

---

### Jak zmienić prefix komend (`$`)?

W `.env`:
```env
PREFIX=!
```

Lub w `config.js`:
```javascript
const config = {
  prefix: '!'
};
```

---

## 👥 Zarządzanie & Uprawa

### Jak promować pracownika?

```
/promote <@mention> <nowa_rola>
```

Wymaga roli `Admin` lub wyższej.

---

### Jak resetować tickety?

```bash
npm run clear-tickets
```

Lub w skrypcie:
```javascript
// scripts/clear_db.js
db.tickets.deleteMany({})
```

---

## 📊 Voice Tracking

### Dlaczego statystyki voice się nie aktualizują?

1. ✅ Sprawdź czy bot ma uprawnienie "Connect" w voice channels
2. ✅ Sprawdź czy `voicesessions.json` ma prawa zapisu
3. ✅ Sprawdzlogi w kanale `Logs`

Resetuj cache:
```bash
# Usuń cache voice sessions
rm -rf data/voicesessions.json
```

---

### Jak wyeksportować statystyki do Excel?

```
/export-voice-stats
```

Bot wyśle plik `.xlsx` do kanału.

---

## 🐛 Błędy & Troubleshooting

### Bot offline / "Nie podłączony"

```bash
# 1. Sprawdź token
grep DISCORD_TOKEN .env

# 2. Sprawdź połączenie internetowe
ping 8.8.8.8

# 3. Restartuj bota
npm start
```

---

### "ECONNREFUSED" - MongoDB connection error

```bash
# 1. Sprawdź czy MongoDB działa
mongosh

# 2. Jeśli Atlas - sprawdź IP whitelist
# W MongoDB Atlas:
# Network Access → Add IP Address → Dodaj thy IP lub 0.0.0.0/0

# 3. Sprawdź MONGODB_URI w .env
cat .env | grep MONGODB_URI
```

---

### Port 6969 już używany

```bash
# Znajdź proces
lsof -i :6969

# Zabij proces
kill -9 <PID>

# Lub zmień port w .env
PORT=7000
```

---

### Brakuje emoji w panelach

```javascript
// W config.js sprawdź czy emoji istnieją:
// 1. Czy są w cudzysłowach
// 2. Czy ID jest poprawne
// 3. Czy bot ma dostęp do emoji

// ✅ Dobrze:
emoji: '<:success:123456789>'

// ❌ Źle:
emoji: 'success'  // Brak cudzysłowów
```

---

### `npm install` zawiesza się

```bash
# Wyczyszcz cache
npm cache clean --force

# Spróbuj znowu
npm install

# Lub zamiast npm, użyj yarn
yarn install
```

---

## 🐳 Docker

### Jak uruchomić w Docker?

```bash
# Build obrazu
docker build -t hedencargo:latest .

# Uruchom kontener
docker run --env-file .env -d hedencargo:latest

# Lub użyj docker-compose
docker-compose up -d
```

[Pełny poradnik](PROJECT_SETUP.md#-docker)

---

### Jak zobaczyć logi kontenera?

```bash
docker logs -f hedencargo
```

---

### Jak zaaktualizować obraz?

```bash
# Build nowy obraz
docker build -t hedencargo:latest .

# Zatrzymaj stary kontener
docker stop hedencargo

# Usuń stary kontener
docker rm hedencargo

# Uruchom nowy
docker run --env-file .env -d hedencargo:latest
```

---

## 💾 Backupy & Baza Danych

### Jak zrobić backup MongoDB?

```bash
# Lokalne
mongodump --out ./backup

# Atlas - wykonuj z panelu
# Collections → Backup & Restore
```

---

### Jak przywrócić backup?

```bash
mongorestore ./backup
```

---

### Gdzie są automatyczne backupy?

```bash
ls backups/
# backup-2026-01-24T21-09-43-796Z/
# backup-2026-01-24T21-11-37-719Z/
```

---

## 👨‍💻 Developer FAQ

### Jak dodać nową komendę?

1. Utwórz plik `src/commands/mycommand.js`:
```javascript
const { SlashCommandBuilder } = require('discord.js');

module.exports = {
  data: new SlashCommandBuilder()
    .setName('mycommand')
    .setDescription('Opis komendy'),
  async execute(interaction) {
    await interaction.reply('Cześć!');
  },
};
```

2. Bot automatycznie załaduje komendę

[Pełny poradnik](CONTRIBUTING.md)

---

### Jak dodać nowy event?

1. Utwórz `src/events/myevent.js`
2. Bot automatycznie załaduje event

```javascript
module.exports = {
  name: 'messageCreate',
  async execute(message) {
    console.log(`Wiadomość: ${message.content}`);
  },
};
```

---

### Jak debugować?

```javascript
// ✅ Używaj logger
const logger = require('./utils/logger');
logger.info('Wiadomość debug', { data: something });

// ❌ Nie używaj console.log
console.log('...');  // Nie rejestruje poziom
```

---

## 🔒 Bezpieczeństwo

### Jak zgłosić lukę w bezpieczeństwie?

**NIE otwieraj publicznego issue!**

Napisz prywatnie do:
- 𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻 (Discord: 446740090757316608)
- Daniel [Daniek.] (Discord)

[SECURITY.md](SECURITY.md)

---

### Czy mogę udostępniać `.env`?

**NIE!** Nigdy nie commituj `.env` z tokenami!

```
# .gitignore
.env          # Zawiera sekrety!
.env.local
.env.*.local
```

---

## 📞 Pomoc & Kontakt

### Gdzie mogę szukać pomocy?

1. 📚 [README.md](README.md) - Ogólna dokumentacja
2. 🛠️ [PROJECT_SETUP.md](PROJECT_SETUP.md) - Instalacja
3. 🤖 [BOT_COMMANDS.md](../HedenCargoWeb/BOT_COMMANDS.md) - Komendy
4. 💬 Discord - Napisz do twórców

### Kim są autorzy?

- **𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻** | [GitHub](https://github.com/WilkorPLYT)
- **Daniel [Daniek.]** | [GitHub](https://github.com/daniekdan)

### Jak się skontaktować?

| Kontakt | Dane |
|---------|------|
| 💬 Discord | 𝓓𝓻𝓦𝓲𝓵𝓪𝓬𝓸𝓻 (446740090757316608) |
| 🐙 GitHub | [@WilkorPLYT](https://github.com/WilkorPLYT) |
| 🌐 Email | Czekaj na kontakt z tworzami |

---

## 🤝 Chcesz Wnieść Wkład?

Przeczytaj [CONTRIBUTING.md](CONTRIBUTING.md) - pokazujemy jak!

---

**Nie znalazłeś odpowiedzi?** 
Otwórz [issue](https://github.com/WilkorPLYT/HedenCargoWeb/issues) lub napisz do nas! 💬
