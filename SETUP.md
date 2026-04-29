# 🚀 SETUP — Routines Advogado Sharp

> **O que vai mudar no teu dia:** acordar e ter o Sharp já te entregando análise dos casos via Telegram + Email. Sem PC ligado, sem volta-1000-vezes.

---

## ✅ O que JÁ tá pronto (eu fiz)

- [x] CLAUDE.md das Routines (identidade Sharp criminalista cloud)
- [x] **Routine 1**: Briefing matinal Sharp (06h BRT diário)
- [x] **Routine 2**: Monitor prazos críticos (08h, 14h, 20h BRT)
- [x] **Routine 3**: Análise novo CNJ (webhook)
- [x] **Routine 4**: Pesquisa concorrentes (segunda 08h BRT)
- [x] Telegram bot configurado (`@claudaogerentebot`)
- [x] Gmail conectado (envio email)
- [x] SSH key VPS funcionando

## ⏸ Pendências TUAS (10-15 min)

### 1. Criar repositório GitHub (1 minuto)

Vai em https://github.com/new e cria:
- **Nome**: `advogado-sharp-routines`
- **Visibilidade**: Private
- **Sem README, sem .gitignore** (eu já fiz)
- Clica "Create repository"

Depois me manda a URL (será algo tipo `https://github.com/SEU_USER/advogado-sharp-routines`).

Eu faço o `git push` da pasta `Routines/` pra esse repo.

### 2. Logar em Claude Routines (1 minuto)

Vai em **https://claude.ai/code/routines** com tua conta Max.

### 3. Conectar GitHub no Routines (2 minutos)

- Clicar em "Add connector" → GitHub
- Autorizar acesso ao repo `advogado-sharp-routines`

### 4. Configurar SECRETS no Routines (3 minutos)

Adiciona estes secrets (lugar seguro, criptografados):

| Nome | Valor |
|---|---|
| `TELEGRAM_BOT_TOKEN` | Token do `@claudaogerentebot` (eu te mando depois pelo chat seguro) |
| `SSH_PRIVATE_KEY` | Conteúdo de `~/.ssh/betao_vps` (privada SSH do teu PC — copia tudo `-----BEGIN... END-----`) |
| `SSH_HOST` | `76.13.234.164` |
| `SSH_USER` | `root` |
| `DATAJUD_API_KEY` | (se renovar token DataJud, cola aqui) |

### 5. Criar 4 Routines (5 minutos cada — total 20 min)

Pra cada uma das 4 routines em `Routines/prompts/`:

a) Clica "Create Routine"
b) Nome: o título do arquivo (ex: "Briefing Matinal Sharp")
c) Cola o **PROMPT** do arquivo MD correspondente
d) Configura o **TRIGGER** (schedule ou webhook conforme indicado)
e) Conecta GitHub repo: `advogado-sharp-routines`
f) Salva e ativa

---

## 📊 Após ativar — o que esperar

### Dia 1 (manhã seguinte)
- 06h BRT: chega Telegram + Email com briefing matinal
- 08h BRT: monitor prazos rodou silencioso (provavelmente sem alerta)

### Dia 2-7
- Validar consumo de tokens (deve ser ~150-200K/dia)
- Validar qualidade dos briefings
- Ajustar prompts se necessário

### Dia 10 (upgrade pra Max 20x R$ 1.100)
- Tokens 5x maiores → cabe mais Routines + mais clientes
- Adicionar webhook DJEN automático
- Adicionar onboarding novo cliente automático

---

## 🆘 Se algo der errado

### Routine falha com erro 401 DataJud
Token DataJud expirou. Renovar em:
https://datajud-wiki.cnj.jus.br/api-publica/acesso

### Routine não conecta SSH
Verificar `SSH_PRIVATE_KEY` secret tá correto (key inteira, não path).

### Telegram não recebe mensagem
Verificar `TELEGRAM_BOT_TOKEN` + `chat_id` 7093001840.

### Email não chega
Verificar Gmail MCP conectado + permissão de envio.

---

## 🔄 Migração futura (quando WhatsApp tiver pronto)

Trocar nas 4 routines o trecho:
```bash
curl ".../sendMessage" -d "chat_id=7093001840"
```

Por:
```bash
# Z-API ou Evolution API
curl "https://api.z-api.io/instances/<ID>/token/<TOKEN>/send-text" \
  -d '{"phone": "5527999999999", "message": "..."}'
```

5 minutos de trabalho pra trocar nas 4.

---

## 💰 Custo estimado

**Hoje (plano Max R$ 550):**
- 4 routines × ~30K tokens/dia = ~120K tokens/dia
- Limite: 422K/dia
- **Folga: 70%**

**Dia 10 (plano Max 20x R$ 1.100):**
- 4 routines + 5 clientes pagantes
- Cabe tudo confortável
