# lucasgrieger.com.br

Página estática de manutenção. Sem build step — o site é o `index.html`.

## Estrutura

- `index.html` — a página (HTML + CSS inline, fonte Montserrat via Google Fonts)
- `vercel.json` — rewrites (qualquer rota cai na página), headers de cache e `noindex`
- `robots.txt` — bloqueia indexação enquanto o site está em manutenção

## Deploy

### Opção A — drag & drop (mais rápido)

1. Acesse https://vercel.com/new
2. Arraste a pasta do projeto para a área de upload
3. Framework Preset: **Other**. Build Command e Output Directory: deixe em branco.

### Opção B — GitHub (deploy automático a cada push)

```
git init
git add .
git commit -m "Página de manutenção"
git branch -M main
git remote add origin git@github.com:USUARIO/lucasgrieger.com.br.git
git push -u origin main
```

Depois, em https://vercel.com/new, importe o repositório. Preset **Other**, sem build command.

### Opção C — CLI (requer Node.js)

```
npx vercel        # preview
npx vercel --prod # produção
```

## Domínio

No projeto da Vercel: Settings → Domains → adicione `lucasgrieger.com.br` e `www.lucasgrieger.com.br`.
No painel do registrador (Registro.br), aponte:

- `A` em `@` → `76.76.21.21`
- `CNAME` em `www` → `cname.vercel-dns.com`

## Ao sair da manutenção

Remova o bloco `X-Robots-Tag: noindex` do `vercel.json`, apague o `Disallow: /` do `robots.txt`
e remova a meta tag `robots` do `index.html`.
