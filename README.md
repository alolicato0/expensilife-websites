# expensilife-websites

Sito vetrina statico per ExpensiLife — privacy policy + terms pubblici.

## File
- `index.html` — landing page
- `privacy.html` — informativa privacy (carica `PRIVACY.md` via JS)
- `terms.html` — termini di servizio (carica `TERMS.md` via JS)
- `PRIVACY.md` — sorgente markdown
- `TERMS.md` — sorgente markdown

## Deploy con Cloudflare Pages
1. **Cloudflare Dashboard** → Workers & Pages → Create → Pages → Connect to Git
2. Seleziona questo repo `expensilife-websites`, branch `main`
3. Build settings: lascia tutto vuoto (sito statico, niente build command, niente output dir)
4. Deploy
5. Vai sul progetto → Custom domains → Add `expensilife.org`
6. Cloudflare configura DNS automaticamente

## URL pubblici (dopo deploy)
- `https://expensilife.org/`
- `https://expensilife.org/privacy.html`
- `https://expensilife.org/terms.html`

## Aggiornamento contenuti legali
Modifica solo `PRIVACY.md` o `TERMS.md` e fai commit. Il sito si aggiorna automaticamente al prossimo deploy.
