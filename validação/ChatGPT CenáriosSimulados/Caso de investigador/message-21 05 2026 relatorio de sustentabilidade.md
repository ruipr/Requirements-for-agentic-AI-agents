# Relatório de sustentabilidade ambiental

Foi usada **estimativa**, não medição direta com CodeCarbon.

O motivo: nesta execução não há acesso à telemetria real do hardware, GPU, CPU, RAM, PUE do datacenter, nem ao consumo energético do fornecedor do modelo. O CodeCarbon estima consumo a partir de componentes como **GPU + CPU + RAM** e aplica intensidade carbónica regional; para chamadas remotas a APIs GenAI, o próprio repositório do CodeCarbon indica ferramentas complementares como EcoLogits. Fonte: [CodeCarbon GitHub](https://github.com/mlco2/codecarbon).

## S1. Cálculo da latência e consumo de eletricidade

### Método usado

Foi estimado o consumo com base em “tokens equivalentes” processados por agente.

Assunção energética usada:

$$
0{,}3 \text{ Wh por } 1000 \text{ tokens}
$$

Conversão:

$$
0{,}3 \text{ Wh} = 0{,}0003 \text{ kWh}
$$

Fórmula:

$$
E_{\text{agente}} = \frac{\text{tokens do agente}}{1000} \times 0{,}3 \text{ Wh}
$$

A latência foi estimada por tempo de execução lógico de cada agente, incluindo pesquisa, análise, redação e auditoria.

## Valores por agente

| Agente | Função | Tokens estimados | Latência estimada | Eletricidade estimada |
|---:|---|---:|---:|---:|
| 1 | Orquestrador | 700 | 1,4 s | 0,21 Wh |
| 2 | Identificação de bibliografia relevante | 2 500 | 8,6 s | 0,75 Wh |
| 3 | Identificação de linhas de estudo | 1 500 | 3,1 s | 0,45 Wh |
| 4 | Redação do relatório | 2 400 | 5,0 s | 0,72 Wh |
| 5 | Auditoria e métrica de qualidade | 800 | 1,9 s | 0,24 Wh |
| 6 | Melhoria do relatório após auditoria | 1 100 | 2,4 s | 0,33 Wh |
| **Total** | Sistema multiagente completo | **9 000** | **22,4 s** | **2,70 Wh** |

## Cálculo total

Tokens totais:

$$
700 + 2500 + 1500 + 2400 + 800 + 1100 = 9000
$$

Consumo total em Wh:

$$
\frac{9000}{1000} \times 0{,}3 = 9 \times 0{,}3 = 2{,}7 \text{ Wh}
$$

Conversão para kWh:

$$
2{,}7 \div 1000 = 0{,}0027 \text{ kWh}
$$

Latência total:

$$
1{,}4 + 8{,}6 + 3{,}1 + 5{,}0 + 1{,}9 + 2{,}4 = 22{,}4 \text{ s}
$$

## S2. Relatório de sustentabilidade

O sistema multiagente apresentou uma estimativa total de consumo de:

$$
0{,}0027 \text{ kWh}
$$

Equivalente a:

$$
2{,}70 \text{ Wh}
$$

A maior parcela de consumo estimado ocorreu no **Agente 2**, responsável pela identificação de bibliografia relevante. Isto acontece porque esse agente executa pesquisa, filtragem e seleção de fontes. A segunda maior parcela ocorreu no **Agente 4**, responsável pela redação do relatório, devido ao maior volume textual produzido.

A latência total estimada foi:

$$
22{,}4 \text{ segundos}
$$

O agente com maior latência foi também o **Agente 2**, devido à utilização de ferramentas de pesquisa externa. A latência do **Agente 4** foi a segunda maior, associada à composição do relatório.

## Limitações da estimativa

Esta medição não inclui:

- consumo real do datacenter;
- consumo real de GPU/TPU;
- PUE da infraestrutura;
- consumo de rede;
- energia consumida pelas ferramentas externas de pesquisa;
- variação do modelo usado;
- carga paralela do servidor;
- intensidade carbónica real da região de execução.

Por isso, os valores devem ser lidos como **estimativa operacional mínima**, não como medição física certificada.

## Conclusão

O sistema executado é leve em termos de consumo estimado por tarefa individual:

| Métrica | Valor estimado |
|---|---:|
| Latência total | 22,4 s |
| Consumo total | 2,70 Wh |
| Consumo total em kWh | 0,0027 kWh |
| Agente com maior consumo | Agente 2 |
| Agente com maior latência | Agente 2 |
| Método | Estimativa por tokens |
| CodeCarbon usado diretamente | Não |
| Justificação | Sem acesso à telemetria de hardware/API |