# SerenaMind 3.1 Secure Pilot

Dit pakket vervangt de vastlopende browserregistratie door twee Supabase Edge Functions.

## 1. Database
Voer `supabase-schema-v3.1.sql` uit in Supabase SQL Editor.

## 2. Edge Functions installeren
Installeer de Supabase CLI, log in en voer in deze projectmap uit:

```bash
supabase link --project-ref agnsklwkmaudqmbmcxuj
supabase functions deploy register-username --no-verify-jwt
supabase functions deploy login-username --no-verify-jwt
```

Supabase levert `SUPABASE_URL`, `SUPABASE_ANON_KEY` en `SUPABASE_SERVICE_ROLE_KEY` automatisch aan Edge Functions. Zet de service-role key nooit in GitHub of `config.js`.

## 3. Website
Upload de bestanden uit de hoofdmap naar GitHub Pages. Upload de map `supabase` ook naar GitHub als broncode, maar nooit geheimen.

## 4. Test
Open de website, registreer met een nieuwe gebruikersnaam, bewaar de herstelcode en log in. Bekijk foutlogs onder Supabase > Edge Functions > Logs.

## Beveiligingsstatus
Dit is een secure-pilotfundament, geen gecertificeerd zorgplatform. De accountfuncties zijn server-side. `crypto-vault.js` demonstreert lokale AES-GCM-versleuteling, maar sleuteloverdracht, sleutelrotatie, herstel, apparaten en echte gedeelde kluizen moeten nog worden voltooid en onafhankelijk worden getest.
