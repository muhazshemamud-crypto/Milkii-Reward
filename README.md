# Telegram Clone Online

Stack:
- HTML/CSS/JavaScript frontend
- Node.js + Express backend
- Socket.IO real-time chat
- Supabase Auth + PostgreSQL online database
- Chapa payment backend

## 1. Supabase
1. Create a Supabase project.
2. Open SQL Editor.
3. Run `supabase_schema.sql`.
4. Copy project URL, publishable/anon key and service-role key.

Supabase Auth supports email/password signup and login. Keep the service-role key ONLY on the server.

## 2. Configure backend
Copy `.env.example` to `.env` and fill:
- SUPABASE_URL
- SUPABASE_ANON_KEY
- SUPABASE_SERVICE_ROLE_KEY
- APP_URL
- CHAPA_SECRET_KEY
- CHAPA_WEBHOOK_SECRET

Never put a Chapa secret key in `index.html`.

## 3. Install and run
```bash
npm install
npm start
```
Open:
`http://localhost:5000`

For a real phone/online app, deploy this Node server over HTTPS. Set APP_URL to the public HTTPS address.

## 4. Chapa
The backend initializes Chapa transactions and redirects the user to `checkout_url`.
After payment, the callback and webhook verify the transaction before updating the payment record.

In the Chapa dashboard, configure the webhook URL:
`https://YOUR-DOMAIN/api/pay/chapa/webhook`

Set the same random webhook secret in `CHAPA_WEBHOOK_SECRET`.

## 5. Important
This is a working starter architecture, not the complete Telegram product. Features such as group/channel management, media storage, push notifications, end-to-end encryption, message reactions, typing indicators, read receipts, and production-grade moderation/admin tools still need separate implementation.
