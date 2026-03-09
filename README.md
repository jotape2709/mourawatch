# MouraWatch 📡

Monitor em tempo real de APIs públicas brasileiras. Dashboard web com dados ao vivo, log de eventos, scan de servidores e painel de segurança (WebSec).

## ✨ Funcionalidades

- **Dashboard** — status ao vivo de 10 APIs públicas brasileiras (BrasilAPI, IBGE, AwesomeAPI)
- **Scan de Servidores** — teste de alcance HTTP a servidores com explicação detalhada sobre CORS e limitações do navegador
- **Log de Eventos** — registro completo de todas as verificações com tipo, latência e mensagem legível
- **WebSec** — painel de segurança mostrando todos os cabeçalhos HTTP ativos e o `vercel.json` pronto para uso

## 🔌 APIs Integradas

| Serviço | Endpoints | CORS |
|---|---|---|
| BrasilAPI | Bancos, CEP, Feriados, Taxas BCB, DDD, Câmbio PTAX | ✅ |
| IBGE | Estados, Municípios | ✅ |
| AwesomeAPI | USD/BRL, EUR/BRL, GBP/BRL, BTC/BRL | ✅ |

## 🔒 Segurança

Todos os cabeçalhos de segurança são aplicados via `vercel.json`:

- `Content-Security-Policy` — previne XSS
- `X-Frame-Options: DENY` — previne clickjacking
- `X-Content-Type-Options: nosniff` — previne MIME sniffing
- `Strict-Transport-Security` — força HTTPS por 2 anos
- `Referrer-Policy: strict-origin-when-cross-origin`
- `Permissions-Policy` — desabilita câmera, microfone, geolocalização

## 🚀 Deploy no Vercel

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/mourawatch.git
cd mourawatch

# 2. Deploy direto pelo CLI
npx vercel

# Ou conecte o repositório no dashboard da Vercel: vercel.com/new
```

O `vercel.json` já está configurado com todos os cabeçalhos de segurança — nenhuma configuração adicional é necessária.

## 📁 Estrutura

```
mourawatch/
├── index.html      # Estrutura HTML + navegação
├── style.css       # Estilos (design system dark)
├── app.js          # Lógica completa da aplicação
├── vercel.json     # Cabeçalhos de segurança HTTP
└── README.md       # Este arquivo
```

## ⚠️ Sobre o Scan de Servidores

Navegadores web **não podem fazer ping ICMP** nem conectar a servidores sem CORS habilitado. O MouraWatch testa a **acessibilidade HTTP** — se um servidor responde (mesmo com 4xx/5xx), ele está online. Se a requisição falha por CORS, o servidor provavelmente está no ar mas não foi projetado para chamadas de páginas web.

Para monitoramento de infra real (CPU, RAM, disco), é necessário um agente como **Prometheus Node Exporter**, **Zabbix Agent** ou **Uptime Kuma** rodando no servidor alvo.

## 📄 Licença

MIT
