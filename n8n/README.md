# HEEKTOR Support – etap 1: Telegram → n8n → Telegram

`heektor-telegram-controller.json` to workflow do zaimportowania w n8n
(Workflows → ⋯ → Import from File). Zawiera: Telegram Trigger (Message) →
`AUTHORIZED OWNER?` (user ID + chat ID) → odpowiedź „✅ HEEKTOR Support działa”.
Nie czyta Gmaila i niczego nie wysyła mailem.

## Co musisz zrobić sam (wymaga Twoich kont)
1. Załóż/otwórz n8n Cloud.
2. Telegram → `@BotFather` → `/newbot` → nazwa `HEEKTOR Support`, username kończący się na `bot`.
3. Token wklej **tylko** w n8n: Credentials → Telegram API → Access Token (nie wklejaj go do czatu ani repo).
4. Zaimportuj plik JSON, w obu node'ach Telegram wybierz utworzone credential.
5. Uruchom test triggera, napisz do bota `siema`, odczytaj `message.from.id` i `message.chat.id`.
6. Wpisz je w:
   - Telegram Trigger → Additional Fields → *Restrict to User IDs* / *Restrict to Chat IDs*,
   - node `AUTHORIZED OWNER?` w miejsce `TWOJ_USER_ID` i `TWOJ_CHAT_ID`.
7. Opublikuj (Active) i napisz do bota – powinien odpowiedzieć.

Dopóki w IF zostają placeholdery, workflow odrzuca wszystko (fail-closed).

Następny krok: Gmail (Inbox + Unread + Sent, bez AI i bez wysyłki).
