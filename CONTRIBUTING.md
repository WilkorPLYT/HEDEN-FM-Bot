# 🤝 Przewodnik Wkładu (Contributing Guide)

Dziękuję za zainteresowanie wkładem w projekt **HEDEN Cargo Bot**! 

## 📋 Spis Treści

- [Jak Zacząć](#-jak-zacząć)
- [Proces Pull Request](#-proces-pull-request)
- [Wytyczne Kodowania](#-wytyczne-kodowania)
- [Raportowanie Błędów](#-raportowanie-błędów)
- [Kwestie i Dyskusje](#-kwestie-i-dyskusje)

---

## 🚀 Jak Zacząć

### 1. Fork Repozytorium

Kliknij przycisk **Fork** w górnym prawym rogu

### 2. Sklonuj Do Lokalnego Repo

```bash
git clone https://github.com/YOUR_USERNAME/HedenCargoWeb.git
cd HedenCargoWeb
```

### 3. Stwórz Nową Gałąź (Branch)

```bash
git checkout -b feature/twoja-nowa-funkcja
# lub
git checkout -b bugfix/napraw-tego-bledy
```

Nazwy gałęzi:
- `feature/nazwa-funkcji` - dla nowych funkcji
- `bugfix/nazwa-bledu` - dla napraw
- `docs/nazwa-zmiany` - dla dokumentacji
- `refactor/nazwa-zmiany` - dla refaktoringu

### 4. Zainstaluj Zależności

```bash
npm install
```

### 5. Utwórz `.env.local` Dla Testowania

```bash
cp .env.example .env.local
# Edytuj z testowymi danymi
```

---

## 📤 Proces Pull Request

### Przygotowanie PR

1. **Upewnij się że kod jest sformatowany:**
   ```bash
   npm run format  # (jeśli dostępne)
   ```

2. **Sprawdź czy nie ma błędów linting:**
   ```bash
   npm run lint  # (jeśli dostępne)
   ```

3. **Przetestuj zmiany:**
   ```bash
   npm test  # (jeśli dostępne)
   npm start
   ```

### Commitowanie

Używaj jasnych i opisowych commitów:

```bash
# ✅ Dobry commit
git commit -m "feat: dodaj system backupu MongoDB"
git commit -m "fix: napraw błąd przy zatważdzaniu zleceń"
git commit -m "docs: aktualizuj README"

# ❌ Zły commit
git commit -m "fix stuff"
git commit -m "zmiany"
```

Prefiks commitów:
- `feat:` - Nowa funkcja
- `fix:` - Naprawienie błędu
- `docs:` - Zmiany w dokumentacji
- `style:` - Formatowanie kodu (bez lógiki)
- `refactor:` - Refactoring kodu
- `test:` - Dodanie testów
- `chore:` - Aktualizacja zależności

### Wypchnij Zmiany

```bash
git push origin feature/twoja-funkcja
```

### Utwórz Pull Request

1. Przejdź na GitHub
2. Kliknij "Compare & pull request"
3. Wypełnij opis zmian
4. Czekaj na recenzję

---

## 💻 Wytyczne Kodowania

### JavaScriptą/Node.js

```javascript
// ✅ Preferuj const/let, nie var
const config = require('./config');
let count = 0;

// ✅ Używaj arrow functions
const sumNumbers = (a, b) => a + b;

// ✅ Dodawaj JSDoc dla funkcji
/**
 * Przesyła embed do kanału Discord
 * @param {Channel} channel - Kanał Discord
 * @param {Object} embed - Embed do wysłania
 * @returns {Promise<Message>}
 */
async function sendEmbed(channel, embed) {
  return channel.send({ embeds: [embed] });
}

// ✅ Obsługuj błędy
try {
  await connectDatabase();
} catch (error) {
  console.error('Błąd połączenia:', error);
  process.exit(1);
}

// ❌ Unikaj console.log, użyj logger
// Używaj: logger.info(), logger.error(), logger.warn()
```

### Struktura Kodu

```
src/
├── commands/        # Komendy Discord
│   ├── ticket.js
│   └── voice.js
├── events/          # Event handlery
│   ├── voiceStateUpdate.js
│   └── messageCreate.js
├── models/          # Modele danych/funkcje
│   ├── Ticket.js
│   └── VoiceStats.js
├── services/        # Biznesowa logika
│   ├── ticketService.js
│   └── statsService.js
└── utils/           # Funkcje pomocnicze
    ├── logger.js
    └── validators.js
```

---

## 🐛 Raportowanie Błędów

### Szablonowy Bug Report

1. Otwórz zakładkę **Issues**
2. Kliknij **New Issue**
3. Opisz problem:

```markdown
## Opis Problemu
Krótki opis czego się nie dzieje

## Kroki Do Reprodukcji
1. Zrób to...
2. Potem to...
3. Błąd się pojawia

## Oczekiwane Zachowanie
Powinno się...

## Obecne Zachowanie
Ale się...

## Dodatkowe Informacje
- Node.js wersja: X.X.X
- OS: Windows/Linux/Mac
- Discord.js: X.X.X
```

---

## 💬 Kwestie i Dyskusje

### Przed Wysłaniem Issues, Sprawdź:

- ✅ Czy problem nie istnieje już?
- ✅ Czy czytasz najnowszą dokumentację?
- ✅ Czy problem dotyczy tego repozytorium?

### Gdzie Szukać Pomocy:

- **Dokumentacja:** [README.md](README.md)
- **Komendy Bota:** [BOT_COMMANDS.md](BOT_COMMANDS.md)
- **FAQ:** W sekcji Wiki (jeśli dostępne)
- **Discord:** Skontaktuj się bezpośrednio

---

## ✅ Checklist Przed PR

- [ ] Brancha oparta o `main`
- [ ] Kod jest sformatowany
- [ ] Committy mają jasne wiadomości
- [ ] Tests pacowały (jeśli dostępne)
- [ ] Dokumentacja zaktualizowana
- [ ] Nie ma console.log debugera
- [ ] `.env` nie został commitowany

---

## 📞 Pytania?

Skontaktuj się z:
- **Waticiami Głównym:** 𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻 #446740090757316608
- **Współautorem:** Daniel [Daniek.] (@daniekdan)

---

Dziękuję za wkład! 🚀
