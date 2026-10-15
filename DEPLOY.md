# Deploy Automático com GitHub + Cloudflare Pages

Este projeto é uma landing page Vite/React. O deploy recomendado é Cloudflare Pages conectado ao GitHub.

## Opção A — Git no dashboard Cloudflare (recomendado para preview automático)

1. Acesse [Workers & Pages](https://dash.cloudflare.com/?to=/:account/workers-and-pages) → **Create** → **Pages** → **Connect to Git**.
2. Autorize o app **Cloudflare Workers & Pages** no GitHub e selecione o repositório `lp-proteina-do-trigo-D`.
3. Configuração de build:

| Campo | Valor |
| --- | --- |
| Production branch | `main` |
| Framework preset | Vite |
| Build command | `npm ci && npm run build` |
| Build output directory | `dist` |
| Root directory | *(vazio)* |

4. **Save and Deploy**.

## Opção B — GitHub Actions (já configurado neste repo)

O workflow `.github/workflows/deploy-cloudflare.yml` publica em **Cloudflare Pages** no projeto `lp-proteina-do-trigo-d`.

### Secrets necessários (Settings → Secrets → Actions)

| Secret | Descrição |
| --- | --- |
| `CLOUDFLARE_API_TOKEN` | Token com permissão **Account → Cloudflare Pages → Edit** |
| `CLOUDFLARE_ACCOUNT_ID` | ID da conta Cloudflare |

Se você já usa o repositório **lp-proteina-do-trigo-B**, pode reutilizar os mesmos valores dos secrets.

### Disparar deploy

- Push na branch `main`, ou
- **Actions** → **Deploy LP Proteina D to Cloudflare Pages** → **Run workflow**

## Fluxo de atualização

```bash
git add .
git commit -m "Atualiza landing page"
git push origin main
```

## Rotas internas

O arquivo `public/_redirects` mantém a página funcionando em links internos e recarregamentos diretos.
