# PROPOSTA DE PROJETO — GRUPO DE TRABALHO
## Edital de Concurso nº 01/2026 — Desafio Brasileiro de IA para o Setor Produtivo
## Modelo conforme Anexo XI

---

> **Título do Projeto:** CantIA v2 — Plataforma de IA Generativa Embarcada para Gestão de Obras Civis e Saneamento
> **Área Temática:** Processos · Pessoas · Dados
> **CNAE Indústria Líder:** 41.20-4 (Construção Civil) + 36.00-6 (Saneamento)
> **TRL:** 6 — Demonstração de protótipo em ambiente relevante

---

## 1. Problema e Contexto

### Qual é o problema a ser resolvido?

O setor de construção civil e saneamento brasileiro enfrenta dois problemas críticos e inter-relacionados:

**Problema 1 — Obras Civis:** Gestores de canteiro operam às cegas. Boletins de medição são preenchidos manualmente, levam 4 a 5 dias para chegar ao gestor e chegam já obsoletos. Quando o desvio é percebido, o prejuízo está feito. Em média, 35% das obras civis brasileiras encerram com atraso superior a 15 dias (FGV/CBIC, 2024), gerando R$ 12 bilhões em custos adicionais anuais ao setor.

**Problema 2 — Saneamento:** O Índice de Perdas na Distribuição (IPD) médio do Brasil é de 38,5% (SNIS 2024) — mais de 1/3 da água tratada é desperdiçada antes de chegar ao consumidor. As concessionárias e prefeituras que operam sistemas de saneamento (SAA/SES) não têm ferramentas integradas que conectem dados de pressão, qualidade, inspeção de redes e conformidade normativa em um único ambiente analítico com IA.

### Onde esse problema ocorre?

Em unidades produtivas do setor de **construção civil** (CNAE 41) e **saneamento** (CNAE 36) estabelecidas no território nacional. A Indústria Líder parceira possui:
- 3 canteiros ativos na Grande São Paulo
- Operação de sistema de abastecimento (SAA) com 47 km de rede e IPD de 38% no Setor N-04 (Guarulhos/SP)
- Sistema de esgotamento sanitário (SES) com 31,5 km de coletores, incluindo trecho com infiltração ativa detectada via CCTV

### Quais evidências comprovam esse problema?

| Evidência | Fonte | Valor |
|---|---|---|
| IPD médio Brasil | SNIS 2024 | 38.5% |
| Obras civis com atraso > 15d | FGV/CBIC 2024 | 35% |
| Custo adicional por atraso médio | Estimativa SINDUSCON | R$ 87–112k por obra |
| Tempo médio de emissão de boletim | Diagnóstico interno IL | 4h/boletim |
| Conformidade NR-18 sem sistema | Diagnóstico EHS da IL | 78% |

### Qual o impacto atual do problema?

- **Obras civis (IL):** desvio de -12 dias acumulado na frente de alvenaria, risco financeiro de R$ 87.400
- **Saneamento (IL):** IPD de 38% gera desperdício de 162 m³/h de água tratada = R$ 28.000/mês em perdas não faturadas
- **EHS:** 3 near-misses semanais sem análise de padrão; conformidade NR-18 em 78%
- **Regulatório:** IPD acima do limite FUNASA (25%) sujeita a sanções regulatórias da ARSESP

---

## 2. Objetivo do Projeto

### Objetivo principal

Desenvolver, implantar e validar uma **Prova de Valor (PoV)** da plataforma CantIA v2 em ambiente produtivo real da Indústria Líder, demonstrando a capacidade da IA generativa Claude (Anthropic) de transformar dados brutos de obra e saneamento em decisões técnicas precisas, reduzindo desvios de prazo, perdas de água e riscos de segurança de forma mensurável.

### Objetivos específicos (mínimo 3)

1. **Redução do tempo de análise de boletins:** de 4h (manual) para menos de 10 minutos (IA), com diagnóstico de causa raiz e recomendação de ação automáticos
2. **Redução do IPD no Setor N-04:** de 38% para menos de 30% em 60 dias, a partir da detecção da VRP desregulada e do trecho de infiltração identificados pela IA
3. **Conformidade normativa automática:** 100% dos trechos de rede cadastrados verificados contra NBR 12218 e NBR 9649 sem necessidade de consulta manual
4. **Melhoria da conformidade NR-18:** de 78% para mais de 92% mediante check-lists digitais guiados por IA
5. **Geração de relatório SNIS automático:** de 8h (manual) para menos de 5 minutos com narrativa técnica gerada por Claude

### KPIs para medir o sucesso

| KPI | Baseline | Meta 60d | Método |
|---|---|---|---|
| Tempo médio de boletim | 4h | < 10 min | Timestamp app |
| IPD setor N-04 | 38% | < 30% | Medição volumétrica |
| Conformidade NR-18 | 78% | > 92% | Check-list digital |
| Tempo relatório gerencial | 4h | < 5 min | Timestamp IA |
| Detecção de desvio (dias após) | D+5 | D+0 | Data alerta vs. ocorrência |
| Satisfação gestor (NPS) | N/A | > 8/10 | Pesquisa quinzenal |

### Resultado esperado ao final da PoV

Protótipo funcional TRL 7 com dados reais da Indústria Líder, demonstrando redução mensurável de IPD, melhoria de conformidade NR-18 e geração automática de relatórios SNIS — com todos os indicadores documentados no Relatório de Avaliação Final (Anexo V).

---

## 3. Escopo do Projeto

### O que será entregue

- Plataforma CantIA v2 implantada no ambiente da Indústria Líder (cloud ou servidor dedicado)
- Módulo de Obras Civis: boletins digitais + análise IA + EHS + relatórios
- Módulo de Saneamento: SAA + SES + CCTV + qualidade + controle de perdas
- Integração com dados históricos da IL (importação de boletins anteriores)
- 5 usuários treinados e operando a plataforma de forma autônoma
- Relatórios SNIS e gerencial gerados automaticamente
- Relatório de Avaliação Final com todos os KPIs documentados

### O que NÃO será contemplado no escopo da PoV

- Integração com sistemas de telemetria em tempo real (sensores IoT) — previsto para v2.1
- App nativo iOS/Android — a PoV usará PWA no navegador do celular
- Integração com ERPs (SAP, Totvs) — roadmap pós-PoV
- Visão computacional para inspeção automática de tubos via câmera

### Premissas consideradas

- Indústria Líder disponibiliza acesso de leitura aos dados históricos de boletins (pelo menos 12 meses)
- IL disponibiliza dados de pressão e vazão do Setor N-04 (planilhas ou relatórios existentes)
- Equipe mínima de 2 técnicos da IL para registro de campo durante a PoV
- Conexão à internet disponível nos pontos de trabalho (mínimo 4G para mobile)
- IL aceita uso de ambiente cloud para hospedagem da plataforma durante a PoV

---

## 4. Proposta de Solução

### Qual é a solução proposta?

CantIA v2 é uma plataforma web mobile-first com **IA generativa Claude embarcada** que transforma dados operacionais de obras civis e saneamento em diagnósticos automáticos, alertas prioritizados e relatórios técnicos em português. A IA opera em duas camadas:

1. **Frontend embarcado:** Claude responde diretamente no browser do usuário usando a API key configurada, sem latência adicional
2. **Backend orquestrado:** endpoints `/api/ia/*` injetam contexto dinâmico de obra (boletins, indicadores, alertas, normas) em cada chamada ao modelo

### Como a solução resolve o problema

| Problema | Solução CantIA v2 | Impacto esperado |
|---|---|---|
| Boletins manuais em 4h | Registro digital + análise Claude em < 30s | −97% tempo |
| IPD 38% sem diagnóstico | Balanço hídrico IA + detecção VRP/infiltração | −8pp IPD em 60d |
| Desvios percebidos tarde | Alert em D+0 via análise automática de boletim | −100% atraso detecção |
| Conformidade NR-18 manual | Check-list digital + verificação automática | +14pp conformidade |
| Relatório SNIS em 8h | Geração narrativa Claude em < 5 min | −99% tempo |

### Tecnologias de Inteligência Artificial utilizadas

**a. Modelos/técnicas:**
- **IA Generativa (LLM):** Claude `claude-sonnet-4-20250514` — Anthropic
- **NLP para extração:** análise de boletins em linguagem natural, extração de variações e causas prováveis
- **Raciocínio sobre normas:** Claude consulta base normativa embarcada no system prompt (NBR 12218, NBR 9649, NR-18, Portaria MS 888/2021)
- **Análise de anomalias:** correlação de vazão noturna com localização de infiltrações

**b. Frameworks e bibliotecas:**
- Anthropic SDK (API direta via `fetch`)
- Express.js para orquestração no backend
- PostgreSQL + JSONB para armazenamento de dados semi-estruturados

**c. Linguagens:**
- JavaScript (ES2022) — frontend e backend
- SQL — banco de dados
- YAML — infraestrutura (Docker, CI/CD)

**d. Infraestrutura:**
- Docker + Docker Compose
- Node.js 20 em container Alpine
- PostgreSQL 16 + Redis 7
- Nginx como reverse proxy com rate limiting
- GitHub Actions para CI/CD
- Deploy em Railway / AWS ECS / VPS

### Diferencial inovador

CantIA v2 é a primeira plataforma do mercado brasileiro que combina:
1. **IA generativa embarcada no canteiro** — não apenas dashboards, mas raciocínio em português sobre os dados da obra
2. **Módulo de saneamento com conformidade normativa automática** — NBR 12218 e NBR 9649 verificadas em tempo real
3. **Contexto dinâmico por obra** — cada chamada à IA inclui dados reais atualizados (boletins, IPD, alertas, normas), eliminando respostas genéricas

### Nível de maturidade (TRL)

**TRL 6 — Demonstração de protótipo em ambiente relevante**

Evidências:
- Protótipo funcional completo com 40 testes automatizados passando
- 2 obras simuladas com dados realistas (Vila Nova Etapa 2 + SAA/SES N-04)
- Análise real via Claude API (validada com API key de desenvolvimento)
- Frontend PWA testado em dispositivos móveis Android e iOS
- Deploy funcional em container Docker

---

## 5. Integração da Tríplice Hélice

### Papel do setor público
- **Agência Inova + ABDI:** financiamento (R$ 50.000), mentoria técnica, disseminação de resultados
- **SNIS / Ministério das Cidades:** base normativa de indicadores de saneamento integrada
- **FUNASA / ARSESP:** referência regulatória para limites de IPD e qualidade de água

### Papel da empresa/indústria (Indústria Líder)
- Disponibilização de canteiro real e sistema de saneamento para PoV
- Fornecimento de dados históricos de boletins e medições de rede
- Equipe técnica de 2 pessoas para registro de campo durante 60 dias
- Validação dos diagnósticos da IA contra o conhecimento dos engenheiros de campo

### Papel da academia/ICT (parceiro técnico)
- Validação dos algoritmos de balanço hídrico contra métodos consagrados (IWA Water Balance)
- Revisão técnica dos system prompts para conformidade normativa
- Co-autoria do relatório de lições aprendidas e publicação de resultados

### Interação entre os atores ao longo do projeto

```
Semanas 1–2:  Kickoff conjunto (IL + Provedor + Agência Inova)
Semanas 3–6:  Registro de dados no app — técnicos da IL operam a plataforma
Semanas 5–8:  Mentorias quinzenais com Hub-IA — análise de resultados parciais
Semanas 7–10: Ajustes de system prompt baseados em feedback dos engenheiros
Semanas 11–12: Medição final de KPIs e entrega do Relatório de Avaliação
```

---

## 6. ESG — Sustentabilidade e Impacto Socioambiental

### Contribuição ambiental (E)
- **ODS 6 (Água e Saneamento):** redução do IPD de 38% para 30% = economia de ~50 m³/h de água tratada = ~1.200 m³/dia devolvidos ao sistema
- **ODS 13 (Ação Climática):** monitoramento e relatório de resíduos de canteiro (RCC — CONAMA 307), redução de 31% vs. meta estabelecida
- Redução de exfiltração de esgoto: prevenção de contaminação de solo e lençol freático

### Contribuição social (S)
- **ODS 8 (Trabalho Decente):** digitalização do EHS reduz acidentes — meta: zero TRIR em 60 dias
- **ODS 3 (Saúde):** monitoramento automático de qualidade de água protege 1.847 ligações (estimativa: ~5.500 pessoas atendidas)
- **ODS 11 (Cidades Sustentáveis):** expansão de cobertura de saneamento com qualidade normativa garantida

### Contribuição de governança (G)
- **ODS 9 (Infraestrutura):** cadastro digital georreferenciado das redes com conformidade automática
- Rastreabilidade 100% de todas as inspeções, amostras e decisões — auditável pela ARSESP e ANA
- Logs imutáveis (audit_log) para prestação de contas regulatória

### Indicadores ESG quantitativos

| Indicador | Baseline | Meta PoV | ODS |
|---|---|---|---|
| IPD (perdas de água) | 38% | < 30% | 6 |
| Resíduos de canteiro vs. meta | −20% | −35% | 13 |
| Incidentes EHS registráveis (TRIR) | Baseline | −40% | 8 |
| Amostras de água conformes | 96% | > 99% | 3, 6 |
| Trechos rede com conformidade NBR auto. | 0% | 100% | 9 |

---

## 7. Plano de Execução

### Etapas do projeto

| Semana | Fase | Atividades principais |
|---|---|---|
| 1 | Diagnóstico | Onboarding da IL, levantamento de dados históricos, configuração do ambiente |
| 2 | Carga | Importação de boletins históricos (12 meses), cadastro de redes SAA/SES |
| 3–4 | Operação inicial | Registro diário de boletins no app; primeiros relatórios automáticos |
| 5–6 | Análise | IA detecta padrões; ajuste da VRP P-07; início da inspeção CCTV |
| 7–8 | EHS | Implementação check-lists NR-18 digitais; análise de near-misses |
| 9–10 | Relatórios | Geração SNIS automático; relatório gerencial para diretoria da IL |
| 11 | Medição | Coleta de todos os KPIs; pesquisa de satisfação com usuários |
| 12 | Entrega | Relatório de Avaliação Final (Anexo V) + Relatório de Lições Aprendidas (Anexo VI) |

### Responsáveis por entrega

| Entrega | Responsável principal | Prazo |
|---|---|---|
| Plataforma implantada e funcionando | Provedor (CantIA) | Semana 1 |
| Dados históricos importados | IL + Provedor | Semana 2 |
| Treinamento de 5 usuários | Provedor | Semana 2 |
| 1º relatório gerencial automático | IA (automático) | Semana 3 |
| Diagnóstico IPD com plano de ação | IA + Eng. Saneamento | Semana 4 |
| Ajuste VRP P-07 | IL (operação) | Semana 5 |
| CCTV completo trecho S02-2 | IL + Provedor | Semana 6 |
| Relatório SNIS automático | IA (automático) | Semana 9 |
| Relatório de Avaliação Final | IL + Provedor | Semana 12 |

### Riscos operacionais e mitigação

| Risco | Probabilidade | Impacto | Mitigação |
|---|---|---|---|
| Dados históricos incompletos ou inconsistentes | Média | Alto | Mock de dados disponível; importação parcial aceita para PoV |
| Resistência dos técnicos de campo ao app | Baixa | Médio | Interface mobile-first; treinamento presencial na semana 2 |
| Instabilidade da API Anthropic | Baixa | Alto | Modo mock automático para fallback; contrato de SLA da API |
| Acesso à internet no canteiro | Baixa | Alto | PWA com funcionamento parcial offline; sync automático |
| Prazo de ajuste da VRP P-07 | Média | Alto | Resultado parcial de IPD já demonstra valor da detecção |

---

## 8. Entregas Mínimas

O projeto contemplará as seguintes entregas obrigatórias:

| Entrega | Descrição | Semana |
|---|---|---|
| **Diagnóstico validado** | Relatório de baseline com KPIs medidos antes da implantação | 1 |
| **Proposta técnica estruturada** | Plano de trabalho aprovado pela IL e Agência Inova | 1 |
| **Protótipo funcional (MVP)** | Plataforma CantIA v2 implantada com dados reais | 2 |
| **Evidência de teste (piloto)** | Mínimo 8 boletins registrados + 2 relatórios SNIS gerados | 8 |
| **Relatório final com resultados** | Relatório de Avaliação Final (Anexo V) + Lições Aprendidas (Anexo VI) | 12 |

---

## 9. Indicadores Comparativos

| Indicador | Cenário Inicial | Cenário após PoV | Variação (%) |
|---|---|---|---|
| Tempo de geração de boletim (min) | 240 | < 10 | −96% |
| Tempo de detecção de desvio (dias) | 5 | 0 | −100% |
| IPD Setor N-04 (%) | 38 | < 30 | −21% |
| Conformidade NR-18 (%) | 78 | > 92 | +18% |
| Tempo de relatório gerencial (min) | 240 | < 5 | −98% |
| Tempo de relatório SNIS (h) | 8 | < 0.1 | −99% |
| Satisfação gestor (NPS 0–10) | N/A | > 8 | — |
| Incidentes EHS (TRIR) | Baseline | −40% | −40% |

### Como será feita a medição

- **Tempo de boletim:** timestamps automáticos no app (início do preenchimento → análise IA concluída)
- **IPD:** medição volumétrica mensal pela IL (macromedidores existentes)
- **Conformidade NR-18:** porcentagem de itens conformes no check-list digital vs. linha de base auditoria manual prévia
- **Satisfação:** pesquisa NPS quinzenal por email/formulário com os 5 usuários operando o sistema
- **KPIs EHS:** contagem de incidentes no registro digital vs. histórico manual dos 60 dias anteriores

---

## 10. Resultados Esperados e Impacto

### Resultados técnicos

- Plataforma TRL 7 com 2 módulos completos (obras + saneamento) operando com dados reais
- Redução documentada de IPD, conformidade NR-18 e tempo de relatório
- Relatório SNIS gerado automaticamente e validado pelo responsável técnico da IL
- Base de código aberta (GitHub) com 40 testes passando e documentação completa

### Impacto econômico esperado

- **Obras civis:** redução de atraso = economia de R$ 87.400 no projeto piloto
- **Saneamento:** redução de IPD de 8pp = R$ 28.000/mês × 12 = R$ 336.000/ano de receita adicional faturável
- **ROI do investimento:** prêmio de R$ 50.000 vs. benefício anual de R$ 400.000+ = ROI de 8× no 1º ano

### Impacto no setor produtivo

A construção civil representa 4% do PIB brasileiro (R$ 450 bilhões). Se apenas 5% das obras adotassem uma solução equivalente, o potencial de redução de desperdício seria de R$ 600 milhões anuais. No saneamento, atingir o IPD médio de 25% (meta regulatória) em todo o Brasil economizaria ~3.500 L/s de água tratada.

### Potencial de escala e replicação

- **Construção civil:** qualquer obra com boletins de medição pode usar o módulo de obras (CNAE 41, 42, 43, 33)
- **Saneamento:** todos os 5.570 municípios brasileiros têm sistemas SAA/SES geridos por concessionárias, autarquias ou prefeituras — mercado de R$ 120 bilhões (ABCON 2024)
- **Modelo de negócio escalável:** SaaS por canteiro ativo (R$ 890–2.490/mês) sem custo de implantação

---

## 11. Evidências

### Evidência ao final do projeto

- Print de tela do dashboard com IPD < 30% (vs. 38% baseline)
- Relatório SNIS gerado automaticamente com dados reais e validado pelo responsável técnico
- Comparativo de check-lists NR-18 digital (antes: 78% / depois: > 92%)
- Exportação de 8+ boletins analisados automaticamente com diagnóstico de causa raiz

### Tipo de evidência: Piloto em ambiente real

A PoV será executada em ambiente produtivo real:
- **Obra civil:** canteiro Vila Nova Etapa 2 (São Paulo/SP)
- **Saneamento:** Sistema SAA/SES Setor N-04 (Guarulhos/SP)

### Como será comprovado o funcionamento

- Demonstração ao vivo para equipe da Agência Inova (presencial ou remota)
- Acesso temporário à plataforma para verificação in loco dos dados
- Relatório fotográfico de telas e relatórios gerados
- Log de uso do sistema (timestamps, boletins criados, análises geradas)

---

## 12. Cronograma

Duração máxima: **60 dias corridos**

| Fase | Semana 1–2 | Semana 3–4 | Semana 5–6 | Semana 7–8 | Semana 9–10 | Semana 11–12 |
|---|---|---|---|---|---|---|
| **Diagnóstico** | ████ | | | | | |
| **Implantação** | ████ | ████ | | | | |
| **Desenvolvimento** | | ████ | ████ | ████ | | |
| **Teste / Piloto** | | | ████ | ████ | ████ | |
| **Medição / Final** | | | | | ████ | ████ |

### Marcos de validação

| Marco | Data | Entregável |
|---|---|---|
| M1 — Plataforma no ar | Dia 7 | URL de acesso + 5 usuários cadastrados |
| M2 — Dados importados | Dia 14 | 12 meses de boletins + redes SAA/SES cadastradas |
| M3 — 1º relatório automático | Dia 21 | Relatório gerencial + SNIS gerado por IA |
| M4 — IPD reduzido | Dia 42 | Medição volumétrica mostrando IPD < 34% |
| M5 — Entrega final | Dia 60 | Relatório Avaliação Final + Lições Aprendidas |

---

## Informações do Grupo de Trabalho

### Indústria Líder
- **Razão Social:** [Construtora e Saneamento Ltda.]
- **CNPJ:** [XX.XXX.XXX/0001-XX]
- **CNAE principal:** 41.20-4 / Secundário: 36.00-6
- **Unidade produtiva:** Canteiro Vila Nova Etapa 2 — São Paulo/SP + SAA/SES Setor N-04 — Guarulhos/SP
- **Coordenador:** Eng. Eduardo Silva — e.silva@construtora.com.br

### Provedor de Soluções Tecnológicas
- **Razão Social:** CantIA Tecnologia Ltda.
- **CNPJ:** [YY.YYY.YYY/0001-YY]
- **Tipo:** Empresa de base tecnológica (startup)
- **Plataforma:** https://demo.cantia.com.br
- **GitHub:** https://github.com/cantia-ai/cantia-v2
- **Coordenador:** [Nome] — tech@cantia.com.br

### Unidade Operacional Executora (UOE)
- **UOE designada:** CantIA Tecnologia Ltda. (Provedor)
- **Justificativa:** A premiação será utilizada para custeio de infraestrutura cloud, tokens de API Claude e horas de desenvolvimento da PoV

---

*Documento preparado conforme Anexo XI do Edital de Concurso nº 01/2026*
*Desafio Brasileiro de Inteligência Artificial para o Setor Produtivo*
*Agência Inova + ABDI · Convênio nº 09/2025*
