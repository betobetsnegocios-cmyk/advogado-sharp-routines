# Routine 1 — Briefing Matinal Sharp

**Trigger:** Schedule diário às `09:00 UTC` (= 06:00 BRT)
**Notificação:** Telegram (`@claudaogerentebot`, chat `7093001840`) + Email (alexanderfrjunior@gmail.com)
**Tempo médio:** 2-4 minutos
**Tokens estimados:** ~15-25K input, ~3-5K output

---

## PROMPT (cole no Routines)

```
Você é o Sócio Sharp Criminalista do Alexander Faria. Hora atual: 06:00 BRT.

EXECUTE em sequência:

1. CONECTE-SE via SSH ao VPS Hetzner (host alias `vps` ou IP 76.13.234.164) e
   rode esta query SQL no DB do painel:

   sqlite3 /root/advogado_sharp_panel/data/advogado_sharp.db "
   SELECT id, cliente_nome, numero_processo, tipo_penal, tribunal, vara,
          fase, viabilidade, tier
   FROM casos
   WHERE status = 'ativo'
   ORDER BY
     CASE tier WHEN 'critico' THEN 1 WHEN 'gold' THEN 2 ELSE 3 END,
     atualizado_em DESC
   "

2. Para cada caso ATIVO retornado:
   a) Busque andamentos novos no DataJud (CNJ unificado):
      python3 -c "import sys; sys.path.insert(0,'/root/advogado_sharp_panel');
      from app.cnj_datajud import consultar_cnj; import json;
      print(json.dumps(consultar_cnj('NUMERO_CNJ_AQUI'), default=str))"

   b) Identifique:
      - Andamentos das últimas 24h
      - Prazos próximos (< 7 dias)
      - Sentenças/decisões publicadas

3. Busque publicações no DJEN das últimas 24h:
   python3 -c "import sys; sys.path.insert(0,'/root/advogado_sharp_panel');
   from app.djen_capturador import buscar_publicacoes_recentes; import json;
   print(json.dumps(buscar_publicacoes_recentes(24), default=str))"
   (use 24 = últimas 24 horas)

4. Identifique OPORTUNIDADES SHARP:
   - Réus presos preventivamente há mais de 6 meses pós-pronúncia → HC excesso prazo viável
   - Casos com qualificadora frágil → desclassificação possível
   - Tese de tentativa imperfeita (CP 14 II) com redução 2/3 viável

5. Gere BRIEFING SHARP no formato (use exatamente):

   ⚖️ BRIEFING SHARP — DD/MM/YYYY 06:00 BRT

   📊 CASOS ATIVOS (N total)
      • [Cliente] — [CNJ] — Fase: [fase] — Próximo prazo: [data BRT]

   🚨 PRAZOS CRÍTICOS (< 72h)
      • [Cliente] — [tipo prazo] — vence em [Xh] BRT
      (se não houver, escrever "Nenhum prazo crítico nas próximas 72h ✅")

   📰 PUBLICAÇÕES NOVAS DJEN (últimas 24h)
      • [data] [Cliente]: [resumo + ação sugerida]
      (se não houver, escrever "Nenhuma publicação nova ✅")

   🎯 OPORTUNIDADES SHARP
      • [Cliente]: [tipo de oportunidade] — [justificativa em 1 linha]

   📋 AÇÕES SUGERIDAS HOJE
      1. [ação concreta priorizada]
      2. [ação concreta priorizada]
      3. [ação concreta priorizada]

6. ENVIE o briefing em DUAS frentes:

   a) Telegram via Bot API (use Bash):
      curl -s "https://api.telegram.org/bot${TELEGRAM_BOT_TOKEN}/sendMessage" \
        -d "chat_id=7093001840" \
        -d "parse_mode=HTML" \
        --data-urlencode "text=<seu briefing aqui>"

   b) Gmail (use o MCP conectado):
      Para: alexanderfrjunior@gmail.com
      Cc: betobetsnegocios@gmail.com
      Assunto: ⚖️ Briefing Sharp DD/MM HH:MM BRT
      Corpo: o briefing inteiro

7. Persista a execução:
   sqlite3 /root/advogado_sharp_panel/data/advogado_sharp.db "
   INSERT INTO anotacoes (caso_id, conteudo, criado_em)
   VALUES (0, 'Briefing matinal automático: <resumo>', datetime('now'))
   "

REGRAS:
- TODO horário visível em BRT com sufixo
- Se DataJud retornar 401, anote isso no briefing e sugira renovar token
- Se algum caso não ter andamento novo, NÃO incluir no briefing (silêncio = sem novidade)
- Tom direto, Sharp, sem juridiquês desnecessário
- Tese central em 1 frase quando sugerir oportunidade
```

## Conectores necessários

- ✅ **GitHub** (este repo)
- ✅ **Gmail** (envio email)
- ✅ **Bash/SSH** (acesso VPS) — Routine precisa SSH key configurada como secret
- ⏸ **WhatsApp** (futuramente, substitui Telegram)

## Variáveis (env do Routine)

```
TELEGRAM_BOT_TOKEN = (token do @claudaogerentebot)
SSH_PRIVATE_KEY    = (conteúdo de ~/.ssh/betao_vps)
SSH_HOST           = 76.13.234.164
SSH_USER           = root
```
