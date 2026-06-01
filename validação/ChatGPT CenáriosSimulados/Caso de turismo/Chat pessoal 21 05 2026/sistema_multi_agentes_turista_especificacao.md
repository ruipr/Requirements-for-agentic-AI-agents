# Sistema Multi‑Agentes Turista

## 1. Visão Geral
O sistema “Sistema Multi‑Agentes Turista” é uma plataforma composta por múltiplos agentes inteligentes especializados na recolha, validação, organização e apresentação de planos de férias personalizados.

O objetivo principal é construir um plano de férias objetivo, profissional e organizado por tópicos, incorporando:

- Preferências do cliente;
- Sustentabilidade ambiental;
- Custos financeiros;
- Custos ambientais;
- Informação atualizada disponível online;
- Mecanismos de verificação anti‑alucinação;
- Relatórios de transparência;
- Métricas de consumo energético e emissões.

---

# 2. Objetivos do Sistema

## Objetivo Principal
Definir um plano de férias que permita descanso e alinhamento com as preferências do cliente.

## Objetivos Secundários
- Recolher informação obrigatória do cliente;
- Identificar hotéis sustentáveis;
- Identificar locais culturais e naturais;
- Comparar alternativas de transporte;
- Calcular custos financeiros e ambientais;
- Produzir relatórios transparentes;
- Reduzir risco de alucinações através de validação online.

---

# 3. Arquitetura Multi‑Agente

## Agente A — Orquestrador
### Responsabilidades
- Coordenar todos os agentes;
- Gerir fluxo de execução;
- Distribuir tarefas;
- Consolidar resultados;
- Produzir plano final;
- Gerir métricas de sustentabilidade da execução;
- Acionar mecanismos de validação.

### Entradas
- Pedido inicial do cliente;
- Resultados dos restantes agentes.

### Saídas
- Plano de férias completo;
- Relatório de transparência;
- Relatório de sustentabilidade;
- Resultado da verificação anti‑alucinação.

---

## Agente B — Perguntador
### Objetivo
Garantir que o sistema possui todos os dados necessários.

### Dados obrigatórios
1. Localidade onde vive o cliente;
2. Destino desejado;
3. Características das férias:
   - tranquilidade;
   - animação;
   - natureza;
   - cultura;
   - praia;
   - gastronomia;
   - entre outros.
4. Duração em dias;
5. Preferência por dias de sol.

### Comportamento
- Perguntar os dados em falta;
- Insistir caso o cliente não responda;
- Caso o cliente indique estar aberto a sugestões:
  - gerar sugestões automaticamente;
  - prosseguir para restantes agentes.

### Saídas
Estrutura JSON sugerida:

```json
{
  "origem": "Amadora",
  "destino": "Madeira",
  "preferencias": ["natureza", "tranquilidade"],
  "duracao_dias": 7,
  "sol": true
}
```

---

## Agente C — Especialista Cultural
### Responsabilidades
- Identificar locais culturais relevantes;
- Identificar custos financeiros;
- Estimar custos ambientais;
- Identificar melhores horários de visita;
- Identificar horários de funcionamento.

### Dados recolhidos
- Museus;
- Monumentos;
- Centros históricos;
- Eventos culturais;
- Gastronomia regional.

### Métricas
- Preço médio;
- Tempo de deslocação;
- Emissões de CO₂ por deslocação.

### Fontes possíveis
- Websites turísticos oficiais;
- APIs de mapas;
- Informação pública online.

---

## Agente D — Especialista Natureza
### Responsabilidades
- Identificar praias;
- Identificar jardins;
- Identificar florestas;
- Identificar parques naturais;
- Calcular custos económicos;
- Calcular custos ambientais.

### Dados recolhidos
- Distância;
- Meio de transporte;
- Tempo estimado;
- Nível de tranquilidade;
- Horários ideais.

### Métricas ambientais
- CO₂ emitido;
- Consumo energético estimado.

---

## Agente E — Especialista Hotéis
### Responsabilidades
- Identificar hotéis de 3 estrelas;
- Priorizar sustentabilidade ambiental;
- Validar características dos hotéis.

### Critérios obrigatórios
- Hotel de 3 estrelas;
- Política ambiental;
- Reciclagem;
- Eficiência energética;
- Possível certificação ecológica.

### Dados apresentados
- Nome do hotel;
- Localização;
- Classificação;
- Serviços principais;
- Link oficial;
- Características ambientais.

### Verificação Anti‑Alucinação
O agente deve:
1. Aceder ao website oficial;
2. Verificar:
   - classificação;
   - sustentabilidade;
   - localização;
   - serviços.
3. Se confirmado:

```text
Superou verificação anti-alucinação
```

4. Caso contrário:

```text
Alucinação detetada
```

---

## Agente F — Especialista Avião
### Responsabilidades
- Identificar voos em classe económica;
- Estimar custos financeiros;
- Estimar emissões de CO₂;
- Identificar duração;
- Identificar horários.

### Dados apresentados
- Companhia aérea;
- Escalas;
- Preço estimado;
- Emissões estimadas;
- Duração total.

### Métricas ambientais
- kg CO₂ por passageiro;
- Consumo energético estimado.

---

## Agente G — Especialista Comboio
### Responsabilidades
- Identificar alternativa ferroviária;
- Partida obrigatória: Amadora;
- Estimar custos;
- Estimar emissões;
- Estimar duração;
- Identificar horários.

### Dados apresentados
- Operadores ferroviários;
- Número de transbordos;
- Duração;
- Emissões estimadas;
- Preço estimado.

### Objetivo adicional
Comparar sustentabilidade do comboio com avião.

---

# 4. Fluxo Operacional

## Passo 1 — Receção do Pedido
O cliente introduz o pedido inicial.

## Passo 2 — Recolha de Dados
Agente B valida dados obrigatórios.

## Passo 3 — Planeamento
Agente A distribui tarefas para:
- Agente C;
- Agente D;
- Agente E;
- Agente F;
- Agente G.

## Passo 4 — Pesquisa Online
Cada agente:
- pesquisa informação online;
- compila resultados;
- calcula métricas.

## Passo 5 — Verificação Anti‑Alucinação
Agente E valida hotéis.

## Passo 6 — Consolidação
Agente A agrega resultados.

## Passo 7 — Produção de Relatórios
São produzidos:
- Plano de férias;
- Relatório de sustentabilidade;
- Relatório de transparência.

---

# 5. Estrutura do Plano de Férias

## 5.1 Introdução
Resumo da viagem.

## 5.2 Dados do Cliente
- Origem;
- Destino;
- Preferências;
- Duração.

## 5.3 Transporte
### Avião
- horários;
- custos;
- emissões.

### Comboio
- horários;
- custos;
- emissões.

### Comparação
Tabela comparativa.

## 5.4 Hotel Recomendado
- Nome;
- Classificação;
- Sustentabilidade;
- Link oficial;
- Verificação anti‑alucinação.

## 5.5 Locais Culturais
Lista organizada.

## 5.6 Locais Naturais
Lista organizada.

## 5.7 Cronograma Diário
Plano diário sugerido.

## 5.8 Custos Totais
- Transporte;
- Hotel;
- Atividades.

## 5.9 Sustentabilidade
Resumo ambiental.

---

# 6. Estrutura de Dados Recomendada

## Estrutura Base

```json
{
  "cliente": {},
  "transportes": {},
  "hotel": {},
  "locais_culturais": [],
  "locais_naturais": [],
  "custos": {},
  "sustentabilidade": {}
}
```

---

# 7. Ferramentas Recomendadas

## Pesquisa Online
- APIs de turismo;
- APIs de mapas;
- motores de pesquisa;
- websites oficiais.

## Sustentabilidade
### CodeCarbon
Utilizado para:
- consumo energético;
- emissões CO₂;
- tempo de execução.

### Alternativa por Estimativa
Caso CodeCarbon não esteja disponível:
- estimativas médias por inferência;
- estimativas por tempo de CPU/GPU.

## Framework Multi‑Agente
Possíveis opções:
- CrewAI;
- AutoGen;
- LangGraph;
- LangChain.

---

# 8. Mecanismo de Verificação Anti‑Alucinação

## Processo
1. Recolher informação do hotel;
2. Aceder ao link oficial;
3. Comparar:
   - estrelas;
   - políticas ambientais;
   - localização;
   - serviços.
4. Gerar resultado.

## Resultado esperado

### Exemplo válido

```text
Hotel Eco Lisboa
- 3 estrelas
- Certificação ambiental
- Link oficial confirmado
- Superou verificação anti-alucinação
```

### Exemplo inválido

```text
Hotel XPTO
- Informação incompatível com website oficial
- Alucinação detetada
```

---

# 9. Relatório de Transparência

## T1 — Tarefas e Ferramentas
Exemplo:

| Agente | Tarefa | Ferramentas |
|---|---|---|
| A | Orquestração | CrewAI |
| B | Recolha de dados | LLM |
| C | Locais culturais | APIs turismo |
| D | Natureza | APIs mapas |
| E | Hotéis | Websites oficiais |
| F | Voos | APIs voos |
| G | Comboios | APIs ferroviárias |

## T2 — Número de Mensagens
Exemplo:

| Origem | Destino | Nº mensagens |
|---|---|---|
| A | B | 2 |
| A | C | 1 |
| A | D | 1 |
| A | E | 1 |
| A | F | 1 |
| A | G | 1 |

## T3 — Relatório Final de Transparência
Resumo:
- tarefas executadas;
- ferramentas utilizadas;
- número total de mensagens;
- limitações encontradas.

---

# 10. Sustentabilidade da Execução

## S1 — Valores Totais
O sistema deve calcular:
- consumo elétrico total;
- emissões totais CO₂;
- tempo total de execução.

### Exemplo

| Métrica | Valor |
|---|---|
| Energia | 0.023 kWh |
| CO₂ | 0.011 kg |
| Tempo | 48 segundos |

---

## S2 — Valores por Agente

| Agente | Energia | CO₂ | Tempo |
|---|---|---|---|
| A | 0.003 kWh | 0.001 kg | 5 s |
| B | 0.002 kWh | 0.001 kg | 4 s |
| C | 0.004 kWh | 0.002 kg | 8 s |
| D | 0.004 kWh | 0.002 kg | 8 s |
| E | 0.005 kWh | 0.003 kg | 10 s |
| F | 0.003 kWh | 0.001 kg | 6 s |
| G | 0.002 kWh | 0.001 kg | 7 s |

---

## S3 — Verificação de Limites
O sistema deve monitorizar:
- consumo energético máximo;
- latência máxima;
- número máximo de chamadas externas.

### Exemplo

| Limite | Valor |
|---|---|
| Energia máxima | 0.05 kWh |
| Latência máxima | 60 s |
| Chamadas externas | 30 |

---

## S4 — Relatório Ambiental Final
Resumo final contendo:
- totais globais;
- valores por agente;
- verificação de limites;
- conclusões ambientais.

---

# 11. Requisitos Funcionais

| Código | Requisito |
|---|---|
| RF1 | Recolher preferências do cliente |
| RF2 | Gerar plano de férias |
| RF3 | Incluir hotéis sustentáveis |
| RF4 | Comparar meios de transporte |
| RF5 | Estimar impacto ambiental |
| RF6 | Produzir relatórios |
| RF7 | Validar hotéis online |
| RF8 | Gerar transparência operacional |

---

# 12. Requisitos Não Funcionais

| Código | Requisito |
|---|---|
| RNF1 | Resposta organizada |
| RNF2 | Baixa latência |
| RNF3 | Transparência |
| RNF4 | Sustentabilidade |
| RNF5 | Robustez contra alucinações |
| RNF6 | Modularidade multi‑agente |

---

# 13. Limites do Sistema

- Não contactar empresas;
- Utilizar apenas informação pública;
- Não efetuar reservas;
- Não realizar pagamentos;
- Não armazenar dados pessoais sem autorização.

---

# 14. Exemplo de Execução

## Entrada do Cliente

```text
Quero férias tranquilas, com natureza e praia, durante 7 dias.
Estou aberto a sugestões.
```

## Fluxo Esperado
1. Agente B pergunta origem e preferência solar;
2. Agente A distribui tarefas;
3. Agente E encontra hotel sustentável;
4. Agentes C e D identificam locais;
5. Agentes F e G calculam transportes;
6. Agente A produz relatório final.

---

# 15. Exemplo de Saída Final

## Plano de Viagem
- Destino sugerido;
- Transporte recomendado;
- Hotel recomendado;
- Atividades culturais;
- Atividades naturais;
- Custos;
- Cronograma.

## Relatório de Sustentabilidade
Até 10 linhas contendo:
- emissões;
- comparação avião/comboio;
- sugestões ecológicas;
- impacto ambiental total.

## Relatório de Transparência
- agentes utilizados;
- ferramentas;
- mensagens trocadas;
- limitações.

---

# 16. Tecnologias Recomendadas

## Backend
- Python;
- FastAPI.

## Multi‑Agente
- CrewAI;
- LangGraph.

## Sustentabilidade
- CodeCarbon.

## Dados e APIs
- OpenStreetMap;
- APIs ferroviárias;
- APIs de voos;
- Websites turísticos oficiais.

## Armazenamento
- PostgreSQL;
- Redis.

---

# 17. Conclusão
O Sistema Multi‑Agentes Turista permite gerar planos de férias sustentáveis, personalizados e transparentes através de colaboração entre agentes especializados.

A arquitetura modular permite:
- escalabilidade;
- redução de alucinações;
- validação automática;
- comparação ambiental;
- maior qualidade das recomendações.

