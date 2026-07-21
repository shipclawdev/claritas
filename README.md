# Claritas

> Portal técnico de Engenharia de Prompt e Documentação Markdown.
> Technical portal for Prompt Engineering and Markdown Documentation.
>
> Mantido por / Maintained by **ShipClaw**

---

## 🇧🇷 Sobre o Projeto

Claritas é um portal de documentação que une **Markdown** (sintaxe universal para documentação técnica) e **Engenharia de Prompt** (comunicação estruturada com modelos de linguagem), com fundamentação em especificações oficiais (CommonMark, GFM) e literatura acadêmica.

Construído sob política **zero-build, zero-dependency** — o HTML abre diretamente no navegador, sem compilação, sem bundlers, sem runtime JavaScript externo.

## 🇬🇧 About

Claritas is a documentation portal that combines **Markdown** (universal syntax for technical documentation) and **Prompt Engineering** (structured communication with language models), grounded in official specifications (CommonMark, GFM) and academic literature.

Built under a **zero-build, zero-dependency** policy — the HTML opens directly in the browser, no compilation, no bundlers, no external JavaScript runtime.

---

## Stack Tecnológica / Tech Stack

| Camada / Layer | Tecnologia / Technology |
|--------|-----------|
| **Frontend** | HTML5 Semântico + CSS3 Puro + JavaScript Vanilla ES6+ |
| **Design** | CSS Grid, Flexbox, Variáveis CSS, Dark Mode |
| **Tipografia / Typography** | Inter + Playfair Display via Google Fonts |
| **Backend (API)** | Cloudflare Workers + Hono |
| **Modelo de IA / AI Model** | Workers AI (Llama 3.1 8B / Llama 3.2 3B) |
| **Streaming** | Server-Sent Events (SSE) |
| **Deploy** | Cloudflare Pages (site) + Wrangler (Worker) |
| **Segurança / Security** | Content-Security-Policy, X-Frame-Options, Referrer-Policy |

---

## Funcionalidades / Features

- **Roteador SPA** com allowlist defensiva e fallback para `#home`
- **Playground de Prompt** — chat com Workers AI em tempo real (SSE)
- **Token Simulator** — otimização automática de prompts via IA
- **Contador de Tokens** — estimativa de custo por modelo
- **Sidebar Markdown** com tracking por scroll e profundidade visual
- **Dark Mode** com persistência via `localStorage`
- **Design responsivo** com hamburger menu e slide-in navigation
- **CSP rigorosa** — sem `eval`, sem CDN, sem dependências externas (exceto fontes)

---

## Como Usar / Getting Started

### 🇧🇷 Frontend
Abra `site/index.html` no navegador. Nenhuma instalação necessária.

### 🇬🇧 Frontend
Open `site/index.html` in your browser. No installation required.

### 🇧🇷 Servidor estático (para CSP)
```bash
cd site
python -m http.server 8080
```
Acesse `http://localhost:8080`

### 🇬🇧 Static server (for CSP)
```bash
cd site
python -m http.server 8080
```
Open `http://localhost:8080`

### 🇧🇷 Playground com Workers AI
```bash
cd worker-playground
npm install
npx wrangler dev
```

### 🇬🇧 Playground with Workers AI
```bash
cd worker-playground
npm install
npx wrangler dev
```

### 🇧🇷 Deploy do Worker
```bash
cd worker-playground
npx wrangler deploy
```

### 🇬🇧 Worker Deploy
```bash
cd worker-playground
npx wrangler deploy
```

> 🇧🇷 O site é deployado automaticamente via **Cloudflare Pages** conectado ao repositório GitHub.
> 🇬🇧 The site is automatically deployed via **Cloudflare Pages** connected to the GitHub repository.

---

## API (Cloudflare Worker)

### `POST /api/complete`
🇧🇷 Proxy SSE para Workers AI (Llama 3.1 8B / Llama 3.2 3B).
🇬🇧 SSE proxy to Workers AI (Llama 3.1 8B / Llama 3.2 3B).

**Request:**
```json
{
  "model": "llama-3.1-8b",
  "messages": [
    { "role": "system", "content": "..." },
    { "role": "user", "content": "Explique Markdown" }
  ]
}
```

**Response:** 🇧🇷 Stream de tokens via SSE. / 🇬🇧 Token stream via SSE.

### `GET /api/health`
🇧🇷 Health check. / 🇬🇧 Health check.
Retorna / Returns `{ "status": "ok" }`.

---

## Segurança / Security

- **Content-Security-Policy** restritiva / restrictive (no `'unsafe-eval'`, no CDN)
- **Zero `innerHTML`** com dados de usuário — toda saída dinâmica usa `textContent`
- **Allowlist de rotas** — rejeição automática de rotas inválidas
- **Links externos** com `target="_blank" rel="noopener noreferrer"`
- **Nenhuma chave de API no código** — secrets gerenciados via `wrangler secret`

---

## Licença / License

🇧🇷 Código aberto mantido por **ShipClaw**.  
🇬🇧 Open source maintained by **ShipClaw**.

🇧🇷 Código-fonte livre para reuso educacional, desde que mantidas as meta tags de segurança.  
🇬🇧 Source code free for educational reuse, provided security meta tags are preserved.
