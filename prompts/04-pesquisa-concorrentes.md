# Routine 4 — Pesquisa Sharp de Concorrentes

**Trigger:** Schedule semanal — Segunda-feira `11:00 UTC` (08:00 BRT)
**Notificação:** Email com relatório PDF/HTML + Telegram resumo
**Tempo médio:** 4-7 minutos
**Tokens estimados:** ~40-60K

---

## PROMPT

```
Você é o estrategista de mercado do Advogado Sharp.
Hoje é segunda-feira 08:00 BRT. Vamos espiar os concorrentes da semana.

CONCORRENTES ALVO (escritórios criminalistas que anunciam digital no Brasil):
- Advogados criminalistas Tribunal do Júri com presença forte em Insta/YouTube
- Escritórios SaaS jurídico (Aurum, Astrea, Projuris, LegalCloud)
- Influenciadores jurídicos com curso/comunidade

EXECUTE:

1. PESQUISA YOUTUBE — top 10 vídeos da última semana com keywords:
   - "advogado criminalista tribunal do júri"
   - "habeas corpus excesso prazo"
   - "defesa criminal SaaS"
   - "IA jurídica advogado"

   Pra cada vídeo, capture:
   - Canal + inscritos
   - Título + thumbnail
   - Views + engagement
   - Hook do primeiro 30s (transcrição)

2. PESQUISA FACEBOOK ADS LIBRARY — anúncios ativos:
   URL: https://www.facebook.com/ads/library/?country=BR&q=<termo>
   Termos:
   - "advogado criminalista"
   - "habeas corpus"
   - "software jurídico"
   - "advogado online"
   - "consulta criminal"

   Pra cada anúncio em destaque, capture:
   - Anunciante
   - Cópia do anúncio (texto)
   - Tipo (vídeo, imagem, carrossel)
   - Hook usado
   - Call-to-action
   - Landing page destino
   - Tempo no ar (se disponível)

3. PESQUISA INSTAGRAM — perfis de criminalistas com engajamento alto:
   - Buscar hashtags #advogadocriminalista #tribunaldojuri #defesacriminal
   - Mapear top 5 perfis (>50k seguidores)
   - Identificar formato de conteúdo (Reels, carrossel, IGTV)

4. ANÁLISE LANDING PAGES dos top 3-5 anunciantes:
   - Headline principal
   - Subheadline
   - Lead magnet (eBook? consulta grátis? webinar?)
   - Pricing (se exposto)
   - Funil (cliente direto, agendamento, leadmag)

5. GERE RELATÓRIO HTML estruturado:

   <h1>📊 Pesquisa Sharp Semanal — DD/MM/YYYY</h1>

   <section>
     <h2>🎯 Resumo Executivo</h2>
     <ul>
       <li>N anunciantes ativos meta no nicho</li>
       <li>Hook dominante: <X>%</li>
       <li>Pricing médio observado: R$ X-Y</li>
       <li>Tendência da semana: <descrição>
     </ul>
   </section>

   <section>
     <h2>🏆 Top 5 Anunciantes</h2>
     [tabela com Anunciante, Tipo, Hook, CTA, LP]
   </section>

   <section>
     <h2>💡 Hooks que Funcionam</h2>
     [lista de hooks com análise rápida do porquê]
   </section>

   <section>
     <h2>📦 Lead Magnets Identificados</h2>
     [eBooks, consultas grátis, webinars]
   </section>

   <section>
     <h2>💰 Pricing Observado</h2>
     [faixa de preços + posicionamento]
   </section>

   <section>
     <h2>🎬 Vídeos virais YouTube</h2>
     [top 10 com canal + views + hook]
   </section>

   <section>
     <h2>🚀 INSIGHTS PARA ADVOGADO SHARP</h2>
     <ol>
       <li>Hooks que adversários usam e ainda não estamos usando</li>
       <li>Lead magnet faltando no Sharp</li>
       <li>Pricing — onde estamos vs concorrentes</li>
       <li>Conteúdo que viraliza e podemos replicar</li>
       <li>Brechas de mercado não cobertas</li>
     </ol>
   </section>

   <section>
     <h2>🎯 Plano de Ação Próxima Semana</h2>
     <ol>
       <li>3 ações concretas pra Beto/Alex executarem</li>
     </ol>
   </section>

6. ENVIAR via:

   a) Email pra betobetsnegocios@gmail.com (relatório completo HTML):
      Assunto: 📊 Pesquisa Sharp Semanal — DD/MM
      Corpo: relatório inteiro

   b) Telegram resumo (chat 7093001840):

      📊 PESQUISA SHARP — DD/MM

      🏆 [N] anunciantes ativos
      💡 Hook dominante: [hook]
      💰 Pricing médio: R$ X-Y
      📦 [N] lead magnets identificados

      🎯 3 ações sugeridas:
      1. [ação]
      2. [ação]
      3. [ação]

      📧 Relatório completo enviado pro email.

7. PERSISTIR no vault Obsidian via SSH:
   ssh vps "cat > /root/obsidian_vault/'betão tips'/Memória/Pesquisas/$(date +%Y-%m-%d)-pesquisa-concorrentes-advogado-sharp.md << 'EOF'
   <relatório markdown>
   EOF"

REGRAS:
- Quando puder, captar números reais (views, engagement, CPM, etc)
- Cite fontes: link YouTube, link Facebook Ads Library
- Tom Sharp: análise direta, sem floreio
- Gerar tudo em PORTUGUÊS BR
```

## Skills usadas

- **WebSearch** (para pesquisa YouTube/Insta)
- **WebFetch** (para landing pages dos concorrentes)
- **Bash** (para SSH no VPS persistir relatório)
- **Gmail** (envio email)
