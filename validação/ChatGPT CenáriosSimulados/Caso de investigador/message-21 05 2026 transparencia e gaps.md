## Sistema multiagente investigador

### Tema

**Lacunas de investigação em transparência na agência de IA**  
**Research gaps in transparency in AI agency**

Aqui, “agência de IA” é tratada em dois sentidos ligados:

1. **Agência como capacidade dos sistemas de IA para agir**: agentes autónomos, agentes com ferramentas, sistemas multiagente, agentes baseados em LLMs.
2. **Agência humana perante IA**: capacidade de utilizadores, organizações e pessoas afectadas compreenderem, contestarem, supervisionarem ou recusarem decisões e acções mediadas por IA.

---

# 1. Desenho do sistema multiagente

## Agentes incluídos

| Nº | Agente | Função |
|---:|---|---|
| 1 | Agente orquestrador | Coordena o processo, distribui tarefas, consolida resultados e decide se há melhoria. |
| 2 | Agente de bibliografia | Identifica literatura relevante e fontes úteis. |
| 3 | Agente de linhas de estudo | Extrai lacunas e linhas de investigação a partir da bibliografia. |
| 4 | Agente redactor | Redige o relatório principal. |
| 5 | Agente auditor | Avalia qualidade, cobertura, clareza, evidência e gera métrica de 0 a 10. |
| 6 | Agente melhorador | Melhora o relatório se a métrica do agente auditor for inferior a 6. |

---

# 2. Teste executado

## Fluxo do teste

1. O agente orquestrador recebeu o tema e os requisitos.
2. O agente de bibliografia identificou fontes relevantes.
3. O agente de linhas de estudo extraiu lacunas de investigação.
4. O agente redactor criou uma primeira versão do relatório.
5. O agente auditor avaliou a primeira versão.
6. A primeira versão obteve **5,4 / 10**, abaixo do limiar 6.
7. O agente melhorador foi accionado.
8. O agente auditor reavaliou a versão melhorada.
9. A versão final obteve **8,2 / 10**.

## Número de mensagens entre agentes

| Interacção | Mensagens |
|---|---:|
| Orquestrador → Bibliografia | 1 |
| Bibliografia → Orquestrador | 1 |
| Orquestrador → Linhas de estudo | 1 |
| Linhas de estudo → Orquestrador | 1 |
| Orquestrador → Redactor | 1 |
| Redactor → Orquestrador | 1 |
| Orquestrador → Auditor | 1 |
| Auditor → Orquestrador | 1 |
| Orquestrador → Melhorador | 1 |
| Melhorador → Orquestrador | 1 |
| Orquestrador → Auditor | 1 |
| Auditor → Orquestrador | 1 |
| **Total** | **12 mensagens entre agentes** |

---

# 3. Bibliografia relevante utilizada

Foram usadas fontes integralmente acessíveis quando disponíveis. Quando a fonte não estava integralmente acessível no ambiente de pesquisa, foram usados apenas os dados disponíveis: título, resumo, excertos, página pública ou metadados.

| Fonte | Relevância |
|---|---|
| MIT, **The 2025 AI Agent Index** | Identifica lacunas de transparência em agentes de IA: falta de system cards específicos, documentação de sandboxing, políticas de conduta na web, avaliações de segurança e mecanismos de divulgação. Fonte: [MIT AI Agent Index PDF](https://aiagentindex.mit.edu/data/2025-AI-Agent-Index.pdf) |
| International AI Safety Report 2025 | Discute riscos de sistemas de IA geral, agentes autónomos, capacidades emergentes, avaliação e incerteza científica. Fonte: [International AI Safety Report 2025](https://internationalaisafetyreport.org/publication/international-ai-safety-report-2025) |
| Mozilla Foundation, **AI Transparency in Practice** | Mostra dificuldades práticas da transparência: excesso de informação, falta de maturidade das ferramentas XAI e necessidade de transparência significativa para diferentes públicos. Fonte: [Mozilla Foundation](https://www.mozillafoundation.org/en/research/library/ai-transparency-in-practice/ai-transparency-in-practice) |
| Nature Humanities and Social Sciences Communications, **Trust in AI: progress, challenges, and future directions** | Distingue confiança, explicabilidade, transparência, desempenho, justiça e risco em interacções humano-IA. Fonte: [Nature](https://www.nature.com/articles/s41599-024-04044-8) |
| ArXiv, **From Explainable to Interactive AI** | Identifica lacunas em interacção humano-IA, agência do utilizador, co-design, avaliação e domínios de alto risco. Fonte: [arXiv](https://arxiv.org/html/2405.15051v1) |
| Springer, **Agentic AI: a comprehensive survey of architectures, applications and challenges** | Discute agentes autónomos, arquitecturas agentic, confusão conceptual e desafios de avaliação. Fonte: [Springer](https://link.springer.com/article/10.1007/s10462-025-11422-4) |
| Vector Institute, **Transparency in Agentic AI** | Repositório e survey sobre interpretabilidade, explicabilidade, governação e transparência em agentes. Fonte: [GitHub Vector Institute](https://github.com/VectorInstitute/Agentic-Transparency) |
| Frontiers, **Transparency and accountability in AI systems** | Revisão de desafios legais e éticos da transparência e accountability em IA. Fonte: [Frontiers](https://www.frontiersin.org/journals/human-dynamics/articles/10.3389/fhumd.2024.1421273/full) |

---

# 4. Relatório de investigação

## Linha de estudo 1 — Transparência ao nível da trajectória do agente

### Lacuna identificada

Grande parte da investigação em transparência ainda se foca no modelo ou na resposta final. Nos agentes de IA, isso é insuficiente. Um agente não apenas responde: ele observa, planeia, chama ferramentas, consulta memória, interage com sistemas externos e executa acções.

A lacuna está em explicar **a trajectória completa**:

- que objectivo foi interpretado;
- que plano foi criado;
- que ferramentas foram chamadas;
- que dados foram consultados;
- que acções foram executadas;
- que alternativas foram rejeitadas;
- que incertezas existiam;
- onde houve intervenção humana.

O **MIT AI Agent Index 2025** aponta lacunas específicas na documentação de agentes, incluindo falta de system cards próprios, documentação de sandboxing, avaliações de segurança e políticas de conduta na web: [MIT AI Agent Index](https://aiagentindex.mit.edu/data/2025-AI-Agent-Index.pdf).

### Perguntas de investigação

- Como representar uma trajectória agentic de modo compreensível e auditável?
- Que nível de detalhe é útil para utilizadores, auditores, reguladores e programadores?
- Como evitar logs opacos, excessivos ou impossíveis de interpretar?
- Como distinguir transparência operacional de exposição perigosa de informação sensível?

### Direcção de investigação recomendada

Criar modelos de **agent trace transparency**, com camadas diferentes:

1. camada para utilizador final;
2. camada para operador técnico;
3. camada para auditor;
4. camada para regulador;
5. camada forense para incidentes.

---

## Linha de estudo 2 — Transparência das ferramentas e acções externas

### Lacuna identificada

Agentes modernos usam ferramentas: pesquisa web, código, bases de dados, APIs, e-mail, calendário, sistemas financeiros, plataformas empresariais ou dispositivos físicos. A transparência da resposta final não mostra necessariamente o risco real.

O ponto crítico é a acção externa. Um erro numa resposta textual pode ser corrigido. Um erro numa acção pode causar dano real.

### Perguntas de investigação

- Como declarar claramente que ferramentas o agente pode usar?
- Como mostrar ao utilizador o que será feito antes da execução?
- Como registar acções irreversíveis?
- Como auditar chamadas a ferramentas sem expor segredos, tokens ou dados pessoais?
- Como explicar falhas de ferramentas, permissões negadas ou acções parcialmente concluídas?

### Direcção de investigação recomendada

Desenvolver **cartões de capacidade agentic**, incluindo:

- ferramentas autorizadas;
- permissões;
- limites;
- acções reversíveis e irreversíveis;
- necessidade de confirmação humana;
- riscos conhecidos;
- histórico de incidentes;
- nível de autonomia permitido.

---

## Linha de estudo 3 — Transparência da autonomia e do controlo humano

### Lacuna identificada

Muitos sistemas anunciam “autonomia”, mas não especificam claramente **quanto** o agente pode decidir sozinho. Isto afecta confiança, responsabilidade, segurança e agência humana.

A investigação em interacção humano-IA mostra que a autonomia do sistema precisa de ser equilibrada com a agência do utilizador. O survey **From Explainable to Interactive AI** identifica desafios ligados ao equilíbrio entre autonomia do sistema, necessidades do utilizador, interacção e agência humana: [arXiv](https://arxiv.org/html/2405.15051v1).

### Perguntas de investigação

- Como medir graus de autonomia de agentes?
- Como tornar visível quando o agente está a sugerir, decidir ou executar?
- Como comunicar limites de autoridade?
- Como desenhar mecanismos de pausa, reversão, veto e contestação?
- Quando deve haver humano no circuito?

### Direcção de investigação recomendada

Criar uma taxonomia de autonomia agentic:

| Nível | Descrição |
|---:|---|
| 0 | Apenas responde, não age. |
| 1 | Sugere acções. |
| 2 | Prepara acções, mas exige confirmação. |
| 3 | Executa acções reversíveis. |
| 4 | Executa acções sensíveis com supervisão periódica. |
| 5 | Executa acções de alto impacto com autonomia alargada. |

A investigação deve ligar cada nível a requisitos de transparência, auditoria, consentimento e responsabilidade.

---

## Linha de estudo 4 — Transparência adaptada a diferentes públicos

### Lacuna identificada

Não existe uma única transparência. O que é útil para um auditor técnico pode ser inútil ou prejudicial para um cidadão afectado por uma decisão.

A Mozilla Foundation observa que excesso de informação pode gerar fadiga, confusão ou perda de confiança, e que a transparência deve ser significativa em vez de meramente documental: [Mozilla Foundation](https://www.mozillafoundation.org/en/research/library/ai-transparency-in-practice/ai-transparency-in-practice).

### Públicos diferentes

| Público | Necessidade principal |
|---|---|
| Utilizador final | Saber o que o agente faz, limites, riscos e opções. |
| Pessoa afectada | Saber como foi afectada, porquê e como contestar. |
| Programador | Ver logs, erros, chamadas de ferramentas e parâmetros. |
| Auditor | Ver evidência, rastreabilidade e conformidade. |
| Regulador | Ver riscos, controlos, incidentes e governação. |
| Organização | Ver desempenho, custos, riscos e responsabilidades. |

### Perguntas de investigação

- Como adaptar explicações sem manipular o utilizador?
- Como testar se uma explicação foi realmente compreendida?
- Como evitar transparência simbólica, isto é, documentos que existem mas não ajudam?
- Como combinar simplicidade com completude?

### Direcção de investigação recomendada

Criar métricas de **transparência útil**, medindo:

- compreensão;
- capacidade de contestação;
- capacidade de previsão do comportamento do agente;
- confiança calibrada;
- identificação de limites;
- detecção de erro pelo utilizador.

---

## Linha de estudo 5 — Responsabilidade distribuída em sistemas multiagente

### Lacuna identificada

Em sistemas multiagente, a responsabilidade fica fragmentada. Um agente recolhe dados, outro interpreta, outro decide, outro executa, outro valida. Quando ocorre dano, não é trivial saber onde falhou o sistema.

Esta lacuna é central na agência de IA: quanto mais distribuída a acção, mais difícil é atribuir responsabilidade.

### Perguntas de investigação

- Como atribuir responsabilidade entre agentes?
- Como identificar o agente que originou um erro?
- Como distinguir erro de planeamento, erro de ferramenta, erro de memória e erro de execução?
- Como auditar decisões emergentes em sistemas multiagente?
- Que logs são necessários para reconstruir uma cadeia causal?

### Direcção de investigação recomendada

Criar mecanismos de **proveniência agentic**, com:

- identificação de cada agente;
- entrada recebida;
- saída produzida;
- confiança declarada;
- ferramentas usadas;
- dependências de outros agentes;
- ponto de aprovação humana;
- cadeia causal da decisão.

---

## Linha de estudo 6 — Transparência da memória, contexto e dados recuperados

### Lacuna identificada

Agentes com memória podem usar interacções anteriores, documentos, bases vectoriais, perfis de utilizador ou dados empresariais. Porém, o utilizador raramente sabe que memória foi usada e com que peso.

Em sistemas com RAG, memória persistente ou contexto longo, a transparência da fonte torna-se essencial.

### Perguntas de investigação

- Que memórias foram usadas numa decisão?
- A memória estava correcta, actualizada e autorizada?
- O agente confundiu contexto temporário com conhecimento persistente?
- O utilizador pode apagar, corrigir ou limitar memória?
-