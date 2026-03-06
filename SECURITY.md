# 🔒 Polityka Bezpieczeństwa

## Raportowanie Luk w Bezpieczeństwie

Jeśli odkryjesz lukę w bezpieczeństwie w tym projekcie, **prosimy nie otwierać publicznego issue**. 

Zamiast tego, skontaktuj się z opiekunami projektu **prywatnie**:

### Kontakt

📧 **Discord:**
- 𝓓𝓻𝓦𝓲𝓵𝓴𝓸𝓻 (ID: `446740090757316608`)
- Daniel [Daniek.] (@daniekdan)

### Informacje Do Podania

Kiedy raportujesz lukę, dodaj:

```
1. Opis podatności
   - Co jest podatne
   - Jak to odkryłeś
   
2. Kroki do reprodukcji
   - Krok 1...
   - Krok 2...
   
3. Potencjalny wpływ
   - Co może się stać
   - Czy uruchamia się automatycznie
   
4. Sugesze naprawę (opcjonalnie)
   - Jak to naprawić
```

## Proces Naprawienia

1. **Potwierdzenie** (24h) - Potwierdzamy otrzymanie raportu
2. **Ocena** (48h) - Oceniamy lukę i jej wagę
3. **Naprawa** (1-7 dni) - Pracujemy nad naprawą
4. **Test** - Testujemy naprawę
5. **Release** - Wydajemy patch/minor release
6. **Ujawnienie** - Publicznie ujawniamy informacje o luce

## Bezpieczeństwo Zależności

Monitorujemy bezpieczeństwo pakietów npm:

```bash
# Sprawdź podatności
npm audit

# Napraw podatności
npm audit fix
```

## Best Practices

### Dla Developerów

1. **Nigdy nie commituj `.env` z sekretami**
2. **Używaj zmiennych środowiskowych** dla:
   - Tokenów Discord
   - Haseł MongoDB
   - API keys

3. **Weryfikuj dane od użytkowników**
   ```javascript
   // ❌ Źle
   const result = eval(userInput);
   
   // ✅ Dobrze
   const result = validator.validate(userInput);
   ```

4. **Używaj rate limiting** dla endpointów
   ```javascript
   const rateLimit = require('express-rate-limit');
   
   const limiter = rateLimit({
     windowMs: 15 * 60 * 1000, // 15 minut
     max: 100 // limit 100 requestów
   });
   
   app.use('/api/', limiter);
   ```

5. **Loguj bezpiecznie** (bez haseł/tokenów)
   ```javascript
   // ❌ Źle
   console.log('Token:', token);
   
   // ✅ Dobrze
   logger.info('User authenticated', { userId: user.id });
   ```

### Dla Administratorów

1. **Aktualizuj zależności regularnie**
   ```bash
   npm update
   npm audit fix
   ```

2. **Monitoruj GitHub Security Alerts**
   - Włącz Dependabot
   - Przegląd alertów bezpieczeństwa

3. **Backupuj dane regularnie**
   - Automatyczne backupy MongoDB
   - Przechowuj w bezpiecznym miejscu

4. **Zarządzaj uprawnieniami**
   - Najmniejsze uprawnienia (principle of least privilege)
   - Regularnie audytuj dostęp

## Bezpieczeństwo Discord Token

⚠️ **NIGDY nie udostępniaj:**
- `DISCORD_TOKEN`
- `MONGODB_URI` z hasłem
- `APPLICATION_ID` + token razem

**JEŚLI token wyciekł:**

1. Natychmiast regeneruj token w [Developer Portal](https://discord.com/developers/applications)
2. Zaktualizuj `.env`
3. Restartuj bota
4. Sprawdź logi czy nie było nieautoryzowanego dostępu

## HTTPS i Szyfrowanie

### Dla Web Dashboard

- Zawsze używaj **HTTPS** w produkcji
- Certyfikaty: Let's Encrypt (darmowe)

```javascript
const https = require('https');
const fs = require('fs');

const options = {
  key: fs.readFileSync('path/to/private-key.pem'),
  cert: fs.readFileSync('path/to/certificate.pem')
};

https.createServer(options, app).listen(3000);
```

### MongoDB Connection

```env
# Musi być HTTPS connection string
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/db?ssl=true
```

## Compliance

Projekt spełnia:
- ✅ GDPR (General Data Protection Regulation)
- ✅ Discord Terms of Service
- ✅ Mozilla Web Security Guidelines

## Aktualizacje Bezpieczeństwa

Informacje o aktualizacjach bezpieczeństwa:
- GitHub Security Advisories
- [npm Security Announcements](https://www.npmjs.com/advisories)
- [Node.js Security Releases](https://nodejs.org/en/security/)

## Historia Wydań

| Wersja | Status | Data |
|--------|--------|------|
| 1.0.0 | Bezpieczna | 2026-03-06 |

---

**Dziękuję za pomoc w utrzymaniu bezpieczeństwa tego projektu!** 🔒

Ostatnia aktualizacja: Marzec 2026
