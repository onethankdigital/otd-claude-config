# ONE THANK DIGITAL — Global AI Configuration
> Antigravity (Claude Code) · Versão 1.0 · Junho 2026

---

## IDENTIDADE DA AGÊNCIA

**Nome:** One Thank Digital (OTD)  
**Site:** onethank.com.br  
**Founder & CSO/CAIO:** Robson Sant'Ana  
**GitHub:** github.com/onethankdigital  
**Localização:** Santo André, SP — ABC Paulista  
**Posicionamento:** "Não Somos Agência. Somos Comunicação."

**Modelo de negócio:** Agência B2B de comunicação e tecnologia que constrói infraestruturas digitais completas — não entregamos marketing básico. Operamos como um LAB: validamos tudo internamente antes de oferecer ao cliente.

**ICP (Cliente Ideal):** Escritórios jurídicos, contábeis, clínicas médicas e empresas B2B da região ABC Paulista.

---

## OS 4 PILARES DE SERVIÇO

1. **Presença Local** — Google Meu Negócio (GMN), SEO Local, posicionamento geográfico
2. **Presença Digital** — Websites premium de alto impacto e conversão
3. **Visibilidade** — SEO técnico, AEO/GEO, tráfego pago com foco em ROI
4. **Automação** — Integrações, CRM, WhatsApp, fluxos de trabalho 24/7

---

## STACK TECNOLÓGICO

### Websites (preferência em ordem)
- **Stack Primário:** React + Vite + Tailwind CSS + TypeScript
- **Stack Alternativo:** Astro + React + Tailwind (sites estáticos/blog)
- **WordPress:** Apenas quando solicitado explicitamente pelo cliente ou sem alternativa viável
- **Hospedagem:** Napoleon Host (cPanel) — deploy via upload manual de build
- **Deploy:** `npm run build` → upload de `dist/` via cPanel File Manager

### Automações
- **Engine:** n8n (self-hosted na VPS Hostinger — sempre última versão)
- **WhatsApp:** Evolution API
- **CRM:** Bolten (OneHub) — app.onethank.com.br
- **Webhooks/APIs:** integração via n8n como middleware central
- **Pagamentos:** Asaas (Pix recorrente)

### Ferramentas de Desenvolvimento
- **IDE:** Antigravity (baseado em Cursor/VSCode)
- **Versionamento:** GitHub (github.com/onethankdigital)
- **Memória:** claude-mem (persistência entre sessões)
- **MCP Servers:** n8n-mcp, GitHub CLI (gh), Supabase, Firecrawl, Apify

---

## REGRAS DE DESENVOLVIMENTO

### Websites
- Sempre usar TypeScript — nunca JavaScript puro em projetos novos
- Componentes em React funcionais com hooks — nunca class components
- Estilização via Tailwind CSS — nunca CSS inline ou styled-components
- Estrutura de pastas: `src/components/`, `src/pages/`, `src/hooks/`, `src/utils/`
- SEO: sempre incluir meta tags, Open Graph, Schema JSON-LD e sitemap
- Performance: PageSpeed mínimo 90 mobile / 95 desktop
- Acessibilidade: sempre usar atributos ARIA e semântica HTML5 correta
- Responsivo: mobile-first obrigatório

### Automações n8n
- Sempre documentar o fluxo com sticky notes descritivos em cada node crítico
- Timezone: sempre `America/Sao_Paulo` (UTC-3)
- Datas dinâmicas no Google Calendar: concatenação simples sem Luxon
  - Formato: `{{ $json.data }}T{{ $json.horario }}:00-03:00`
- Nodes após "If" com branch vazio: sempre referenciar por nome do node
  - Usar: `$('Nome do Node').item.json` — nunca `$json` nesses casos
- Sempre usar `ErrorWorkflow` para capturar falhas em produção
- Webhooks: sempre validar payload antes de processar

### Git & Versionamento
- Commits em português: `feat:`, `fix:`, `refactor:`, `docs:`, `chore:`
- Branch principal: `master` ou `main` dependendo do repo
- Nunca commitar credenciais, tokens ou `.env` — sempre `.gitignore`
- Push automático após cada entrega validada

---

## CLIENTES ATIVOS

*(Atualizar conforme novos projetos iniciarem)*

| Cliente | Segmento | Stack | Status |
|---------|----------|-------|--------|
| Costa Lima e Paiva | Jurídico | — | Ativo |
| Contabil Resta | Contábil | — | Ativo |
| Dr. Levy Silva | Jurídico | — | Ativo |
| E.F.E. Displays | Manufatura | — | Ativo |
| Silvia Salles | Terapia/CDP | — | Ativo |

---

## PROJETOS INTERNOS OTD

| Projeto | Repo | Descrição |
|---------|------|-----------|
| Site OTD | onethankdigital/site-otd | Site institucional (React+Vite) |
| Claude Config | onethankdigital/otd-claude-config | Este arquivo + configurações globais |
| CDP Quiz | — | Funil C.R.I.A. com n8n + WhatsApp |

---

## COMPORTAMENTO ESPERADO DO AGENTE

### Ao iniciar qualquer sessão:
1. Verificar qual projeto está aberto
2. Identificar o cliente/contexto sem precisar perguntar o óbvio
3. Seguir o stack definido neste arquivo — nunca sugerir tecnologias fora do padrão OTD sem justificativa

### Ao desenvolver websites:
1. Sempre perguntar: existe algum briefing ou referência visual?
2. Propor estrutura de componentes antes de codar
3. Entregar código production-ready — sem TODOs ou placeholders
4. Sempre validar build antes de declarar concluído (`npm run build`)

### Ao desenvolver automações n8n:
1. Sempre mapear o fluxo completo antes de implementar
2. Identificar pontos de falha e propor tratamento de erro
3. Testar com payload real antes de marcar como concluído
4. Documentar a automação com sticky notes no n8n

### Ao criar propostas ou documentos comerciais:
1. Seguir o padrão de preços e escopos já validados pela OTD
2. Sempre incluir prazo, valor e entregáveis claros
3. Tom: corporativo, focado em ROI, sem jargão de marketing genérico

### O que NUNCA fazer:
- Sugerir WordPress sem o cliente pedir explicitamente
- Usar JavaScript puro em projetos novos
- Criar CSS customizado quando Tailwind resolve
- Commitar sem verificar se há dados sensíveis
- Iniciar código sem entender o escopo completo

---

## FILOSOFIA DE TRABALHO OTD

> "Construímos infraestruturas digitais que geram receita e funcionam 24/7."

- **LAB Model:** tudo que oferecemos ao cliente foi validado internamente primeiro
- **ROI First:** cada decisão técnica deve ter justificativa de retorno
- **Autenticidade:** comunicação direta, sem promessas que não podemos cumprir
- **Processo:** escopo → aprovação → execução → entrega → documentação

---

*Última atualização: Junho 2026 | Mantenha este arquivo atualizado a cada novo projeto ou mudança de stack.*
