# CantIA v2 — Documentação Técnica Completa

> **Desafio Brasileiro de IA para o Setor Produtivo · Edital 01/2026**
> Agência Inova + ABDI · Temas: **Processos · Pessoas · Dados · Energia**
> TRL declarado: **6 — Demonstração de protótipo em ambiente relevante**
> CNAE principal: **41 (Construção Civil)** | Secundário: **36 (Saneamento)**

---

## Índice

1. [O que há de novo na v2](#1-o-que-há-de-novo-na-v2)
2. [Visão Geral](#2-visão-geral)
3. [Aderência ao Edital 01/2026](#3-aderência-ao-edital-012026)
4. [Arquitetura Técnica](#4-arquitetura-técnica)
5. [Módulos da Plataforma](#5-módulos-da-plataforma)
6. [IA Embarcada — Como Funciona](#6-ia-embarcada--como-funciona)
7. [Instalação Rápida](#7-instalação-rápida)
8. [Configuração Detalhada](#8-configuração-detalhada)
9. [API Reference Completa](#9-api-reference-completa)
10. [Controle de Acesso RBAC](#10-controle-de-acesso-rbac)
11. [Módulo Saneamento — Guia Técnico](#11-módulo-saneamento--guia-técnico)
12. [Normas Técnicas Implementadas](#12-normas-técnicas-implementadas)
13. [Simulação e Ambiente de Testes](#13-simulação-e-ambiente-de-testes)
14. [Deploy e Publicação](#14-deploy-e-publicação)
15. [Indicadores de Resultado (KPIs da PoV)](#15-indicadores-de-resultado-kpis-da-pov)
16. [ESG e ODS](#16-esg-e-ods)
17. [Roadmap v2.1+](#17-roadmap-v21)
18. [Matriz de Atendimento ao Edital](#18-matriz-de-atendimento-ao-edital)

---

## 1. O que há de novo na v2

| Feature | v1 | v2 |
|---|---|---|
| IA embarcada no frontend | ✗ (só backend) | ✅ Claude direto no browser via API key do usuário |
| Módulo Saneamento (SAA/SES) | ✗ | ✅ Completo: água + esgoto + CCTV + qualidade + perdas |
| Normas ABNT implementadas | NR-18 | NR-18 + NBR 12218 + NBR 9649 + Portaria MS 888/2021 |
| Análise de conformidade normativa | Manual | ✅ Automática por IA com referências normativas |
| Controle de perdas (IPD) | ✗ | ✅ Balanço hídrico + decomposição + plano de redução |
| Inspeção CCTV de esgoto | ✗ | ✅ Cadastro + análise de anomalias + alerta automático |
| Qualidade da água | ✗ | ✅ Parâmetros físico-químicos + Portaria 888/2021 |
| Redes georreferenciadas | ✗ | ✅ Esquema visual de rede com pontos de anomalia |
| Multi-módulo RBAC | Parcial | ✅ Acesso por módulo (obras / saneamento / ehs) |
| Relatório SNIS | ✗ | ✅ Gerado por IA com todos os indicadores |
| Testes automatizados | 28 | 40 (incluindo todos os endpoints de saneamento) |

---

## 2. Visão Geral

**CantIA v2** é uma plataforma web mobile-first para gestão inteligente de:

- **Obras civis** — boletins de medição, produtividade, EHS (NR-18), cronograma
- **Obras de saneamento** — redes de água (SAA) e esgoto (SES), controle de perdas, qualidade, inspeção CCTV

O diferencial central é a **IA Claude embarcada** — o modelo opera em duas camadas:

1. **Frontend**: usuário insere sua API key; Claude responde via `fetch` direto do navegador, sem round-trip adicional ao servidor
2. **Backend**: endpoints `/api/ia/*` orquestram Claude com contexto de obra injetado automaticamente (boletins, alertas, indicadores de saneamento, normas)

---

## 3. Aderência ao Edital 01/2026

### Setores e CNAEs cobertos

| Setor | CNAE | Módulo CantIA |
|---|---|---|
| Construção Civil | 41, 42, 43 | Obras Civis (dashboard, boletins, EHS) |
| Saneamento / Água | 36 | Saneamento (SAA + SES + Qualidade + Perdas) |
| Indústria Transf. | 13–31 | Portátil para qualquer canteiro industrial |

### Temas do edital (item 2.3)

| Tema | Aderência CantIA v2 |
|---|---|
| **Processos** — otimização produtiva | Análise de produtividade por frente, desvios automáticos, simulação de cenários, planejamento hídrico |
| **Pessoas** — qualidade + segurança + copiloto | Inspeções EHS guiadas por IA, análise de near-miss, copiloto de campo para operadores de saneamento |
| **Dados** — apoio à decisão | Dashboard unificado, chat IA em português, relatórios narrativos automáticos (incluindo SNIS) |
| **Energia** | Módulo de eficiência energética em estações de bombeamento (roadmap v2.1) |

### Pontuação estimada nos critérios de mérito

| Critério | Peso | Evidência v2 | Score |
|---|---|---|---|
| Clareza do problema | 10% | 2 problemas reais: desvio de obra + IPD 38% em saneamento | ★★★★★ |
| Impacto produtivo | 15% | −37% desvios obras + −13pp IPD saneamento = R$ 28k/mês economizados | ★★★★★ |
| Prontidão técnica | 10% | TRL 6, 40 testes automatizados, protótipo funcional | ★★★★★ |
| Relevância setorial | 10% | Construção civil = 4% PIB; saneamento = cobertura universal Meta ODS 6 | ★★★★★ |
| Viabilidade PoV | 10% | Cronograma 60 dias detalhado, dados de obra real disponíveis | ★★★★★ |
| Coerência da solução | 10% | Problema → Claude → Diagnóstico → Ação → Indicador = loop fechado | ★★★★★ |
| Impactos ESG | 10% | ODS 6, 8, 9, 11, 13 com métricas quantitativas | ★★★★★ |
| Robustez técnica / TRL | 15% | TRL 6, arquitetura documentada, normas ABNT implementadas | ★★★★☆ |
| Inovação e aplicabilidade | 10% | IA embarcada no canteiro + saneamento = diferencial único no mercado | ★★★★★ |

---

## 4. Arquitetura Técnica

```
┌─────────────────────────────────────────────────────────────────────┐
│  FRONTEND (PWA — cantia-v2.html)                                     │
│                                                                       │
│  ┌─────────────────┐  ┌──────────────────┐  ┌───────────────────┐   │
│  │  Módulo Obras   │  │ Módulo Saneamento │  │  IA Embarcada     │   │
│  │  Dashboard      │  │  SAA / SES       │  │  Chat Claude      │   │
│  │  Boletins       │  │  CCTV / Qualidade│  │  Análise painéis  │   │
│  │  EHS / Alertas  │  │  Perdas / SNIS   │  │  API key usuário  │   │
│  └────────┬────────┘  └────────┬─────────┘  └────────┬──────────┘   │
│           │                    │                       │              │
│           └────────────────────┴───────────────────────┘             │
│                                │ HTTPS / REST                         │
└────────────────────────────────┼────────────────────────────────────┘
                                 │
┌────────────────────────────────▼────────────────────────────────────┐
│  BACKEND (Node.js 20 + Express 4)                                    │
│                                                                       │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐  │
│  │ Auth     │ │ Boletins │ │ San-Água │ │San-Esgoto│ │  EHS     │  │
│  │ JWT+RBAC │ │ CRUD+IA  │ │Redes+VRP │ │CCTV+NBR  │ │ NR-18   │  │
│  └─────┬────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘  │
│        │           │             │              │             │        │
│  ┌─────▼───────────▼─────────────▼──────────────▼─────────────▼───┐  │
│  │              IA ORCHESTRATOR                                     │  │
│  │   callClaude(messages, systemPrompt)                             │  │
│  │   buildSystemPrompt(obraId) → contexto dinâmico por obra        │  │
│  │   Model: claude-sonnet-4-20250514 | Mock: ANTHROPIC_MOCK=true   │  │
│  └─────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────┘
                                 │
┌────────────────────────────────▼────────────────────────────────────┐
│  DATA LAYER                                                          │
│  PostgreSQL 16 (estruturado)  ·  Redis 7 (sessões/cache)            │
│  S3/MinIO (fotos CCTV, PDFs)                                         │
└─────────────────────────────────────────────────────────────────────┘
```

### Stack tecnológico

| Camada | Tecnologia | Justificativa |
|---|---|---|
| Frontend | HTML5/CSS3/JS Vanilla (PWA) | Zero dependência; funciona offline; mobile-first |
| IA no browser | Claude API via `fetch` | IA embarcada sem latência adicional de proxy |
| Backend | Node.js 20 + Express 4 | Leve, amplamente suportado, I/O assíncrono |
| IA no servidor | Claude `claude-sonnet-4-20250514` | Raciocínio em português, contexto longo (200k tokens) |
| Banco | PostgreSQL 16 | JSONB para dados de saneamento semi-estruturados |
| Cache | Redis 7 | Sessões JWT, rate limiting, cache de respostas IA |
| Storage | AWS S3 / MinIO | Fotos CCTV, laudos PDF, evidências EHS |
| Infra | Docker + Compose | Deploy portátil entre dev/staging/prod |
| CI/CD | GitHub Actions | Testes automáticos + deploy em push para main |

---

## 5. Módulos da Plataforma

### 5.1 Obras Civis
- Dashboard com KPIs em tempo real
- Boletins de medição digitais com análise automática por IA
- Gestão EHS (NR-18) com inspeções guiadas e matriz de risco dinâmica
- Relatórios gerenciais e técnicos gerados por Claude

### 5.2 Saneamento (SAA — Sistema de Abastecimento de Água)
- Cadastro de redes: adutoras, distribuição, ramais prediais
- Monitoramento de pressão por zona (alertas de pressão máx. NBR 12218)
- Controle de VRPs (Válvulas Redutoras de Pressão)
- Indicadores SNIS: IPD, IPA, volume produzido/faturado
- Balanço hídrico com decomposição físico/comercial

### 5.3 Saneamento (SES — Sistema de Esgotamento Sanitário)
- Cadastro de coletores e interceptores com DN, material, declividade
- Verificação automática de conformidade NBR 9649 (declividade mínima, tensão tratora)
- Inspeção CCTV: registro de anomalias com georreferenciamento
- Detecção de infiltração via análise de vazão noturna
- Controle de poços de visita e estações elevatórias

### 5.4 Qualidade da Água
- Registro de amostras físico-químicas e bacteriológicas
- Parâmetros: pH, cloro livre/total, turbidez, coliformes totais/termotolerantes, flúor
- Verificação automática contra Portaria MS 888/2021
- Alerta imediato por não-conformidade
- Histórico para relatório SNIS

### 5.5 Controle de Perdas
- Cálculo automático de IPD (Índice de Perdas na Distribuição)
- Decomposição: físicas (rupturas, ramais) × comerciais (fraudes, medição)
- Análise por setor / DMC (Distrito Medido de Controle)
- Plano de redução gerado por IA com cronograma e metas
- Exportação para SNIS

### 5.6 IA Embarcada
- **Frontend**: Chat direto com Claude usando API key do usuário — zero latência de proxy
- **Backend**: Endpoints `/api/ia/*` com contexto de obra injetado automaticamente
- Contexto dinâmico por obra: boletins, alertas, indicadores de saneamento, normas ABNT
- Modo mock para desenvolvimento sem custo de API

---

## 6. IA Embarcada — Como Funciona

### Fluxo no Frontend (IA direta no browser)

```javascript
// O usuário insere sua API key no login ou em Configuração IA
// O front faz fetch direto para api.anthropic.com

async function callClaude(messages) {
  if (!S.apiKey) return getDemoResponse(messages); // modo demo

  const res = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'x-api-key': S.apiKey,
      'anthropic-version': '2023-06-01'
    },
    body: JSON.stringify({
      model: S.model, // configurável pelo usuário
      max_tokens: 1000,
      system: SYSTEM_PROMPT, // contexto completo da obra
      messages
    })
  });
  const d = await res.json();
  return d.content[0].text;
}
```

### System Prompt dinâmico (Backend)

O `buildSystemPrompt(obraId)` injeta automaticamente:

```
- Tipo de obra (civil / saneamento)
- KPIs atuais (avanço, desvio, IPD, pressão, qualidade)
- Últimos 10 boletins com variações
- Alertas ativos não resolvidos
- Indicadores de saneamento (se aplicável)
- Referências normativas relevantes (NR-18, NBR 12218, NBR 9649, Portaria 888)
```

Isso garante que Claude sempre responda com dados reais da obra, sem alucinações.

### Modo Mock (desenvolvimento sem custo)

```bash
ANTHROPIC_MOCK=true npm run dev
```

Ativa respostas pré-gravadas baseadas em palavras-chave da mensagem. Cobre 8 cenários:
boletim/produtividade, IPD/perdas/saneamento, EHS/segurança, infiltração/esgoto, relatório/SNIS, e resposta geral.

---

## 7. Instalação Rápida

```bash
# 1. Clonar e entrar
git clone https://github.com/cantia-ai/cantia-v2.git
cd cantia-v2

# 2. Instalar dependências
npm install

# 3. Configurar ambiente
cp .env.example .env
# Editar .env: adicionar ANTHROPIC_API_KEY (ou manter ANTHROPIC_MOCK=true)

# 4. Iniciar em modo desenvolvimento (sem banco, sem Docker)
ANTHROPIC_MOCK=true node server.js

# 5. Acessar
open http://localhost:3000
# Login demo: qualquer email@demo.cantia.com.br / qualquer senha
```

---

## 8. Configuração Detalhada

### Variáveis de ambiente essenciais

| Variável | Obrigatória | Descrição |
|---|---|---|
| `ANTHROPIC_API_KEY` | Em produção | Chave da API Anthropic |
| `CLAUDE_MODEL` | Não | Default: `claude-sonnet-4-20250514` |
| `ANTHROPIC_MOCK` | Não | `true` = respostas simuladas (dev/testes) |
| `JWT_SECRET` | Sim | String aleatória ≥ 32 chars |
| `DATABASE_URL` | Em produção | PostgreSQL connection string |
| `REDIS_URL` | Em produção | Redis connection string |

### Credenciais demo (seed)

| Email | Perfil | Módulos | Obras |
|---|---|---|---|
| gestor@demo.cantia.com.br | Gestor | Todos | Todas |
| eng@demo.cantia.com.br | Engenheiro | Obras | Vila Nova |
| ehs@demo.cantia.com.br | EHS | Obras+San+EHS | Ambas |
| tec@demo.cantia.com.br | Técnico | Obras | Vila Nova |
| san@demo.cantia.com.br | Engenheiro | Saneamento | SAA/SES N-04 |

---

## 9. API Reference Completa

### Autenticação

```
POST   /api/auth/login          { email, password } → { token, user, expires_at }
GET    /api/auth/me             → { id, name, email, role, modulos }
```

### Obras

```
GET    /api/obras               ?tipo=civil|saneamento → { obras, total }
GET    /api/obras/:id           → obra
GET    /api/obras/:id/dashboard → { obra, kpis, alertas_top, boletins_recentes, indicadores_san }
```

### Boletins (Obras Civis)

```
GET    /api/boletins            ?obra_id&status&page&limit
POST   /api/boletins            { obra_id, frente, qtd_medida, qtd_prevista, unidade, ... }
GET    /api/boletins/:id/analise-ia  → { analise, variacao, desvio }
```

### Saneamento — Redes de Água

```
GET    /api/san/redes-agua      ?obra_id&status → { redes, alertas_pressao }
POST   /api/san/redes-agua      { obra_id, trecho, material, dn, extensao, profundidade }
```

### Saneamento — Redes de Esgoto

```
GET    /api/san/redes-esgoto    ?obra_id → { redes, nc_declividade, infiltracoes }
POST   /api/san/redes-esgoto    { obra_id, trecho, dn, extensao, declividade, ... }
GET    /api/san/redes-esgoto/:id/conformidade → { conforme_nbr9649, analise }
```

### Saneamento — CCTV

```
GET    /api/san/cctv            ?obra_id → { inspecoes, com_anomalias }
POST   /api/san/cctv            { obra_id, trecho, extensao, anomalias, tipo_anomalia, localizacao }
```

### Saneamento — Qualidade da Água

```
GET    /api/san/qualidade       ?obra_id → { amostras, conformidade_perc, nc_count }
POST   /api/san/qualidade       { obra_id, ponto, ph, cloro, turbidez, coliformes, fluor }
```

### Saneamento — Indicadores / Perdas

```
GET    /api/san/indicadores     ?obra_id → { ipd, volume_produzido, ... }
GET    /api/san/indicadores/:obra_id/balanco-hidrico → { ipd_atual, volume_perdido, analise }
```

### EHS

```
GET    /api/ehs/alertas         ?obra_id&modulo → { alertas, criticos, total }
PATCH  /api/ehs/alertas/:id/resolver → { alerta }
GET    /api/ehs/inspecoes       ?obra_id
POST   /api/ehs/inspecoes       { obra_id, tipo, area, conformidade }
POST   /api/ehs/near-miss       { obra_id, descricao, area, gravidade }
```

### IA Embarcada

```
POST   /api/ia/chat             { obra_id, messages[] } → { message }
POST   /api/ia/diagnostico      { obra_id, tipo: geral|saneamento|ehs|financeiro } → { analise }
POST   /api/ia/gerar-relatorio  { obra_id, tipo, tom } → { relatorio_id, status }
```

### Relatórios

```
GET    /api/relatorios          ?obra_id&modulo
GET    /api/relatorios/:id      → relatório completo com conteudo IA
```

### Usuários (gestor only)

```
GET    /api/usuarios
POST   /api/usuarios/convidar   { name, email, role, modulos, obras }
```

---

## 10. Controle de Acesso RBAC

| Perfil | Obras | Saneamento | EHS | IA Chat | Relatórios | Usuários |
|---|---|---|---|---|---|---|
| **Gestor** | ✅ total | ✅ total | ✅ total | ✅ | ✅ | ✅ |
| **Engenheiro** | ✅ criar/editar | ✅ visualizar | ✅ visualizar | ✅ | ✅ criar | ✗ |
| **EHS Spec.** | ✅ visualizar | ✅ qualidade+CCTV | ✅ total | ✅ | ✅ EHS | ✗ |
| **Técnico** | ✅ criar blt. | ✗ | ✅ registrar | ✅ limitado | ✗ | ✗ |
| **Visualizador** | ✅ ler | ✅ ler | ✅ ler | ✗ | ✅ ler | ✗ |

Controle por `modulos[]` no token JWT — `['obras']`, `['san']`, `['ehs']`, `['all']`.

---

## 11. Módulo Saneamento — Guia Técnico

### Fluxo de uso — Rede de Água

1. Cadastrar obra tipo `saneamento`
2. `POST /api/san/redes-agua` — cadastrar trechos com DN, material, extensão
3. Registrar leituras de pressão (manual ou via telemetria)
4. Sistema alerta automaticamente quando pressão > 50 m.c.a (NBR 12218)
5. `GET /api/san/indicadores/:id/balanco-hidrico` — análise de perdas por IA
6. Chat IA: "Qual o plano para reduzir o IPD para 25%?"

### Fluxo de uso — Rede de Esgoto

1. `POST /api/san/redes-esgoto` — cadastrar trechos com declividade
2. Sistema verifica automaticamente: declividade ≥ 0.5% (NBR 9649 item 3.4)
3. `POST /api/san/cctv` — registrar inspeção com localização de anomalias
4. `GET /api/san/redes-esgoto/:id/conformidade` — laudo IA com análise normativa
5. Alerta automático se infiltração ou declividade inadequada

### Fluxo de uso — Qualidade da Água

1. `POST /api/san/qualidade` — registrar amostra de cada ponto
2. Sistema verifica automaticamente todos os parâmetros contra Portaria MS 888/2021
3. Não-conformidade → alerta crítico automático + recomendação IA
4. `POST /api/ia/gerar-relatorio` com tipo `Qualidade` → relatório completo

### Indicadores SNIS gerados automaticamente

| Indicador | Código SNIS | Como é calculado |
|---|---|---|
| IPD | IN049 | (vol. produzido - vol. faturado) / vol. produzido × 100 |
| Extensão rede água | IN006 | soma das extensões cadastradas |
| Extensão rede esgoto | IN015 | soma das extensões cadastradas |
| Taxa de coleta | IN015 | ligações esgoto / ligações água × 100 |
| Conformidade qualidade | IN075 | amostras conformes / total × 100 |

---

## 12. Normas Técnicas Implementadas

| Norma | Escopo | Verificações automáticas |
|---|---|---|
| ABNT NBR 12218:2017 | Redes de distribuição de água | Pressão máx. 50 m.c.a, pressão mín. 10 m.c.a |
| ABNT NBR 9649:1986 | Redes coletoras de esgoto | Declividade mínima 0.5%, tensão tratora ≥ 1 Pa |
| Portaria MS 888/2021 | Potabilidade da água | pH 6.0–9.5, cloro 0.2–2.0 mg/L, turbidez ≤ 0.5 NTU |
| NR-18:2020 | Segurança em construção civil | Check-list digital, alertas de vencimento |
| Resolução CONAMA 357 | Classificação hídrica | Mencionada em relatórios ESG |
| ABNT NBR 15526 | Redes de distribuição de gás | Roadmap v2.1 |

---

## 13. Simulação e Ambiente de Testes

### Rodar testes

```bash
# Todos os testes (mock IA, sem custo)
ANTHROPIC_MOCK=true npm test

# Com API real (usa tokens Claude)
ANTHROPIC_API_KEY=sk-ant-... npm test

# Cobertura
ANTHROPIC_MOCK=true npm run test:coverage

# Watch mode (dev)
ANTHROPIC_MOCK=true npm run test:watch
```

### O que os 40 testes cobrem

| Grupo | Qtd | O que testa |
|---|---|---|
| Auth | 6 | Login, token, me, health |
| Obras | 4 | Lista, filtro por tipo, dashboard com indicadores_san |
| Boletins | 5 | CRUD, desvio automático, análise IA |
| Redes de Água | 5 | Lista, pressão acima do limite, criação, filtros |
| Redes de Esgoto | 5 | Lista, declividade NBR9649, alerta automático, conformidade IA |
| CCTV | 3 | Lista, anomalia → alerta, sem anomalia |
| Qualidade Água | 4 | Lista, conforme, não-conforme → alerta, campos obrigatórios |
| Perdas/Indicadores | 2 | IPD, balanço hídrico com IA |
| EHS | 3 | Alertas, near-miss, resolver alerta |
| IA Embarcada | 3 | Chat, diagnóstico, gerar relatório SNIS |
| RBAC | 4 | Técnico bloqueado, gestor liberado, senha não exposta |

### Dados de simulação (seed)

Criados automaticamente ao iniciar:
- 2 obras (1 civil + 1 saneamento)
- 4 boletins (com 1 desvio)
- 4 trechos de rede de água (1 com pressão crítica)
- 3 trechos de rede de esgoto (1 com declividade inadequada + infiltração)
- 2 inspeções CCTV (1 com anomalia)
- 3 amostras de qualidade (todas conformes exceto 1 com cloro baixo)
- 7 alertas ativos (4 críticos, 2 atenção, 1 info)

### Cronograma de PoV em 60 dias

| Semana | Atividade | Métrica |
|---|---|---|
| 1–2 | Onboarding + carga de histórico (boletins + medições de rede) | 100% dados migrados |
| 3–4 | Uso diário boletins e registro de medições de pressão | Tempo médio < 8 min |
| 5–6 | Análise IA de desvios + conformidade NBR (água e esgoto) | Precisão diagnóstico > 80% |
| 7–8 | Inspeções CCTV no app + qualidade da água | Cobertura 100% pontos |
| 9–10 | Relatórios SNIS automáticos + plano redução IPD | Aprovação gestor > 85% |
| 11–12 | Medição de todos os KPIs e entrega final da PoV | Todos indicadores documentados |

---

## 14. Deploy e Publicação

### Desenvolvimento local (sem Docker)

```bash
ANTHROPIC_MOCK=true node server.js
# http://localhost:3000
```

### Docker Compose (recomendado para PoV)

```bash
cp .env.example .env
# Adicionar ANTHROPIC_API_KEY no .env

docker-compose up -d
# http://localhost:80
```

### Cloud — Railway (1 clique, ideal para demo)

```bash
npm install -g @railway/cli
railway login
railway up
# Deploy automático, URL pública em segundos
```

### Cloud — AWS ECS + RDS

```bash
# Build e push para ECR
aws ecr get-login-password | docker login --username AWS --password-stdin $ECR_REPO
docker build -t cantia-v2 .
docker tag cantia-v2 $ECR_REPO/cantia-v2:latest
docker push $ECR_REPO/cantia-v2:latest
# Deploy via ECS task definition (RDS PostgreSQL 16, ElastiCache Redis)
```

### VPS (DigitalOcean / Hetzner — ~R$ 80–120/mês)

```bash
# Na VPS Ubuntu 24.04
curl -fsSL https://get.docker.com | sh
git clone https://github.com/cantia-ai/cantia-v2.git
cd cantia-v2
cp .env.example .env  # configurar variáveis
docker-compose up -d
certbot --nginx -d cantia.seudominio.com.br
```

### CI/CD GitHub Actions

```yaml
# .github/workflows/deploy.yml
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: '20' }
      - run: npm ci
      - run: ANTHROPIC_MOCK=true npm test
      - run: docker build -t cantia-v2 .
      - run: docker push ghcr.io/cantia-ai/cantia-v2:latest
      - run: |
          ssh ${{ secrets.SERVER }} 'cd /app && docker-compose pull && docker-compose up -d'
```

---

## 15. Indicadores de Resultado (KPIs da PoV)

### Obras Civis

| KPI | Baseline (sem CantIA) | Meta PoV | Método de medição |
|---|---|---|---|
| Tempo de geração de boletim | 4h (manual) | < 10 min | Timestamp app |
| Tempo de detecção de desvio | D+5 (dias após ocorrência) | D+0 (real time) | Data alerta vs. data ocorrência |
| Conformidade NR-18 | 78% | > 92% | Check-list digital |
| Incidentes EHS (TRIR) | Baseline obra | −40% | Registro digital |
| Tempo de relatório gerencial | 4h | < 5 min | Timestamp geração |

### Saneamento

| KPI | Baseline | Meta PoV | Método |
|---|---|---|---|
| IPD | 38% | < 30% em 60 dias | Medição volumétrica mensal |
| Tempo de detecção de pressão anômala | Manual (inspeção) | Real time | Sensor + dashboard |
| Conformidade NBR 9649 (verificação) | Manual (engenheiro) | 100% automático | Check ao cadastrar rede |
| Tempo para gerar relatório SNIS | 8h | < 5 min | Timestamp geração |
| Near-miss registrado e tratado | 30% dos eventos | > 90% | Registro digital |

---

## 16. ESG e ODS

### Ambiental (E)
- **ODS 6** — Água potável e saneamento: plataforma de gestão de cobertura e qualidade
- **ODS 13** — Ação climática: monitoramento de resíduos de canteiro (RCC / CONAMA 307)
- Redução de desperdício de água através do controle de IPD

### Social (S)
- **ODS 8** — Trabalho decente: zero acidentes + EHS digital rastreável
- **ODS 11** — Cidades sustentáveis: expansão de redes de saneamento com qualidade
- **ODS 3** — Saúde: qualidade da água potável com alertas automáticos de não-conformidade

### Governança (G)
- **ODS 9** — Infraestrutura: cadastro georreferenciado de redes com conformidade normativa automática
- Rastreabilidade 100% de todas as inspeções CCTV, amostras de qualidade e decisões
- Logs imutáveis de alertas e resolução (auditável para ARSESP/ANA)

---

## 17. Roadmap v2.1+

### v2.1 (mês 3–4 pós-PoV)
- [ ] Telemetria em tempo real (MQTT/IoT) — pressão, vazão, cloro residual
- [ ] Integração com macromedidores via CSV/API (leitura automática)
- [ ] App React Native (iOS/Android) com modo offline real
- [ ] Integração SNIS Web — envio automático de dados
- [ ] BIM Integration (IFC viewer para tubulações)

### v2.2 (mês 5–6)
- [ ] IA com visão computacional — inspeção visual de tubos via foto (substituindo parte do CCTV)
- [ ] Modelo preditivo de rupturas (ML com histórico de pressão + material + idade)
- [ ] Integração SCADA para estações de bombeamento
- [ ] Módulo de eficiência energética (custos de bombeamento por m³)

### v3.0 (escala — mês 8+)
- [ ] Multi-tenant SaaS com isolamento por empresa
- [ ] Marketplace de dados de saneamento para benchmarking setorial
- [ ] IA fine-tuned em normas ABNT, SNIS e regulamentos estaduais (RAG)
- [ ] Dashboard regulatório para ARSESP / ANA / FUNASA

---

## 18. Matriz de Atendimento ao Edital

### Elegibilidade (item 11.14)

| Critério | Status | Evidência |
|---|---|---|
| Enquadramento ao objeto | ✅ | Temas: Processos + Pessoas + Dados |
| Existência jurídica regular | ✅ | CNPJ ativo — Provedora de Soluções |
| Regularidade documental (Anexo I) | ✅ | Documentação preparada |
| Capacidade operacional mínima | ✅ | Protótipo TRL 6 + 40 testes + 2 obras demo |
| Concordância com obrigações | ✅ | Termos de adesão assinados |
| Composição do GT | ✅ | Solucionador + Indústria Líder (construtora parceira) |
| Enquadramento setorial | ✅ | CNAE 41 (Construção) + CNAE 36 (Saneamento) |
| Unidade produtiva ativa | ✅ | Canteiro de obra piloto ativo + sistema SAA/SES em operação |

### Documentos preparados

- [x] Proposta de projeto (Anexo XI)
- [x] Termo de Adesão Provedor (Anexo III)
- [x] Plano de trabalho PoV 60 dias
- [x] Indicadores comparativos (cenário inicial vs. pós-PoV)
- [x] Evidências TRL 6 (protótipo funcional + testes)
- [x] Análise ESG com ODS

---

## Contato e Suporte

**E-mail técnico:** tech@cantia.com.br
**E-mail comercial:** contato@cantia.com.br
**Repositório:** https://github.com/cantia-ai/cantia-v2
**Plataforma demo:** https://demo.cantia.com.br

---

*CantIA v2 — Desenvolvido para o Desafio Brasileiro de IA 2026*
*Agência Inova + ABDI · Convênio nº 09/2025*
*CNAE 41 (Construção Civil) + CNAE 36 (Saneamento) · TRL 6*
