# 🚀 Przewodnik Konfiguracji Projektu

Kompletny poradnik do uruchomienia HEDEN Cargo Bot lokalnie i w produkcji.

## 📋 Spis Treści

- [Wymagania](#-wymagania)
- [Instalacja Lokalna](#-instalacja-lokalna)
- [Konfiguracja Discord](#-konfiguracja-discord)
- [Konfiguracja MongoDB](#-konfiguracja-mongodb)
- [Uruchamianie](#-uruchamianie)
- [Docker](#-docker)
- [Troubleshooting](#-troubleshooting)

---

## 🔧 Wymagania

### Minimalne
- **Node.js** 18.0.0+
- **npm** 9.0.0+ lub **yarn** 3.0.0+
- **MongoDB** 4.4+
- **Git**

### Zalecane
- **Visual Studio Code** lub inny edytor
- **Docker & Docker Compose** (dla konteneryzacji)
- **Postman** (dla testowania API)

### Walidacja Wersji

```bash
node --version      # v18.0.0+
npm --version       # 9.0.0+
mongod --version    # 4.4+
git --version       # 2.34.0+
```

---

## 📦 Instalacja Lokalna

### Krok 1: Klonuj Repozytorium

```bash
git clone https://github.com/WilkorPLYT/HedenCargoWeb.git
cd HedenCargoWeb
```

### Krok 2: Zainstaluj Zależności

```bash
npm install
# lub
yarn install
```

### Krok 3: Utwórz Plik `.env`

```bash
cp .env.example .env
```

Otwórz `.env` w edytorze i wypełnij wartości (patrz. sekcja poniżej).

### Krok 4: Zainstaluj MongoDB

#### Opcja A: Lokalnie

**Windows:**
```bash
# Pobierz z https://www.mongodb.com/try/download/community
# Zainstaluj installer
# Weryfikuj z MongoDB Compass
```

**macOS:**
```bash
brew tap mongodb/brew
brew install mongodb-community
brew services start mongodb-community
```

**Linux (Ubuntu/Debian):**
```bash
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-6.0.list
apt-get update
apt-get install -y mongodb-org
sudo systemctl start mongod
```

#### Opcja B: MongoDB Atlas (Cloud)

1. Przejdź na [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Zaloguj się lub utwórz konto
3. Utwórz nowy cluster (Free Tier jest ok)
4. Wygeneruj connection string
5. Skopiuj do `.env` jako `MONGODB_URI`

---

## 🔐 Konfiguracja Discord

### Krok 1: Utwórz Aplikację Discord

1. Przejdź na [Discord Developer Portal](https://discord.com/developers/applications)
2. Kliknij "New Application"
3. Nazwij ją "HEDEN Cargo Bot"
4. Zaakceptuj ToS

### Krok 2: Utwórz Bota

1. Przejdź na zakładkę "Bot"
2. Kliknij "Add Bot"
3. Pod "TOKEN" kliknij "Copy"
4. Wklej do `.env` jako `DISCORD_TOKEN`

### Krok 3: Skonfiguruj Uprawnienia

1. Przejdź na "OAuth2" → "URL Generator"
2. Wybierz scopes:
   ```
   ✅ bot
   ✅ applications.commands
   ```
3. Wybierz uprawnienia:
   ```
   ✅ Manage Channels
   ✅ Send Messages
   ✅ Manage Messages
   ✅ Read Message History
   ✅ Use Slash Commands
   ✅ Manage Roles
   ✅ Connect (voice)
   ✅ Speak (voice)
   ```
4. Skopiuj wygenerowany URL

### Krok 4: Dodaj Bota na Serwer

1. Wejdź na wygenerowany URL z kroku 3
2. Wybierz serwer (musi być twój serwer testowy)
3. Zaakceptuj uprawnienia

### Krok 5: Pobierz IDs

Włącz **Tryb Dewelopera** w Discord:
- Settings → Advanced → Developer Mode

Potem PPM na:
- **Serwer** → "Copy Server ID" → `GUILD_ID`
- **Twój profil** → "Copy User ID" → `OWNER_ID`
- **Aplikacja** → General Information → Copy "Application ID" → `APPLICATION_ID`

### Plik `.env` Discord:

```env
DISCORD_TOKEN=your_bot_token_here
APPLICATION_ID=your_app_id_here
GUILD_ID=your_server_id_here
OWNER_ID=your_user_id_here
```

---

## 📊 Konfiguracja MongoDB

### Plik `.env` MongoDB:

```env
# Lokalne
MONGODB_URI=mongodb://localhost:27017/hedencargo

# Lub Atlas Cloud
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/hedencargo?retryWrites=true&w=majority
```

### Tworzenie Backupów

```bash
# Zrzucić bazę danych
mongodump --out ./backup

# Przywrócić bazę danych
mongorestore ./backup

# Atlas - automatyczne backupy są w consoli
```

---

## ▶️ Uruchamianie

### Tryb Development (z auto-reload)

```bash
npm run dev
```

Wymaga zainstalowania `nodemon`:
```bash
npm install --save-dev nodemon
```

### Tryb Produkcji

```bash
npm start
```

### Logi

```bash
# Powinno pokazać:
⚙️  HEDEN Cargo Bot - Uruchamianie...
[OK] ✓ Zalogowano jako HEDEN Cargo#1234
[INFO] Discord.js v14.8.0
[OK] ✓ Bot gotowy do pracy!
```

---

## 🐳 Docker

### Budowanie Obrazu

```bash
docker build -t hedencargo:latest .
```

### Uruchamianie Kontenera

```bash
docker run --env-file .env \
  --name hedencargo \
  -d hedencargo:latest
```

### Docker Compose

```bash
docker-compose up -d
```

### Logi Kontenera

```bash
docker logs -f hedencargo
```

---

## 🔍 Troubleshooting

### Bot się nie startuje

**Błąd:** `DISCORD_TOKEN is not provided`
```bash
# Sprawdź czy .env ma DISCORD_TOKEN
cat .env | grep DISCORD_TOKEN
```

**Rozwiązanie:** Upewnij się że token jest w `.env`

---

### MongoDB Connection Error

**Błąd:** `connect ECONNREFUSED 127.0.0.1:27017`

```bash
# Sprawdź czy MongoDB działa
mongosh  # Powinno się połączyć

# Jeśli nie, uruchom MongoDB:
# Windows: Uruchom mongod.exe
# macOS: brew services start mongodb-community
# Linux: sudo systemctl start mongod
```

---

### Port Już Używany

**Błąd:** `EADDRINUSE :::6969`

Zmień port w `.env`:
```env
PORT=7000
```

Lub zamknij proces:
```bash
# Windows
netstat -ano | findstr :6969
taskkill /PID <PID> /F

# macOS/Linux
lsof -i :6969
kill -9 <PID>
```

---

### Bot Online Ale Nie Odpowiada na Komendy

1. **Sprawdź czy kanały istnieją:**
   ```bash
   # W config.js - sprawdź nazwy kanałów
   ```

2. **Sprawdź logi w kanale Logs:**
   ```
   W config.js szukaj channel.logs
   ```

3. **Sprawdź uprawnienia bota:**
   - Settings serwera → Roles → @HEDEN Cargo Bot
   - Powinien być na górze listy ról

---

### Błędy Express/API Server

Jeśli serwer Express się nie startuje:

```bash
# Sprawdź czy PORT jest dostępny
netstat -ano | findstr :6969

# Zmień PORT w .env
PORT=3000
npm run server
```

---

## ✅ Weryfikacja Instalacji

```bash
# Test 1: Node.js
node -e "console.log('Node.js OK')"

# Test 2: npm packages
npm list discord.js mongodb

# Test 3: Discord
npm start
# Sprawdź czy bot pojawił się online na serwerze

# Test 4: MongoDB
mongosh --eval "db.version()"
```

---

## 📚 Dodatkowe Zasoby

- [Node.js Dokumentacja](https://nodejs.org/docs/)
- [Discord.js Guide](https://discordjs.guide/)
- [MongoDB Dokumentacja](https://docs.mongodb.com/)
- [Express.js Getting Started](https://expressjs.com/getting-started)

---

Powodzenia! 🚀

Jeśli masz problemy, skontaktuj się z:
- 𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻 (Discord: `446740090757316608`)
- Daniel [Daniek.] (@daniekdan)
