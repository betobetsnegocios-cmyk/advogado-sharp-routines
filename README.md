# Advogado Sharp — Routines (Cloud Agent 24/7)

Funcionários IA que rodam 24/7 na nuvem da Anthropic, sem PC ligado, sem VPS sobrecarregada.

## 📁 Estrutura

```
Routines/
├── CLAUDE.md            ← Identidade Sharp Criminalista (lido pelo agente)
├── README.md            ← Este arquivo
├── SETUP.md             ← Passo-a-passo de configuração
├── .gitignore           ← Ignora secrets/logs
└── prompts/
    ├── 01-briefing-matinal.md       ← Diário 06h BRT
    ├── 02-monitor-prazos.md         ← 3x/dia (08, 14, 20h BRT)
    ├── 03-analise-cnj.md            ← Webhook (sob demanda)
    └── 04-pesquisa-concorrentes.md  ← Semanal (segunda 08h)
```

## 🎯 O que cada Routine faz

| Routine | Quando roda | O que entrega |
|---|---|---|
| **Briefing Matinal** | Diário 06h BRT | Resumo casos ativos, prazos, oportunidades — Telegram + Email |
| **Monitor Prazos** | 3x ao dia | Alerta se prazo < 72h |
| **Análise CNJ** | Webhook sob demanda | Análise Sharp completa de novo processo + persiste no DB |
| **Pesquisa Concorrentes** | Segunda 08h | Relatório semanal anúncios + hooks + pricing dos concorrentes |

## 💰 Custo

Cabe **dentro do plano Max R$ 550/mês** atual. Sem cobrança extra Anthropic.

Estimativa: **~150-250K tokens/dia** (Max 5x cobre 422K).

## 🚀 Como começar

Ver `SETUP.md` — 10-15 minutos do teu tempo, eu já fiz tudo o resto.

---

*Bootstrap: 2026-04-29 · Beto + Claude (Sócio Sharp)*
