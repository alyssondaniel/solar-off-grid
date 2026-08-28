# Plano de operacao para consumo medio de 0,650 kWh/dia

## Objetivo

Este documento corrige a premissa de consumo para media diaria de 0,650 kWh/dia (650 Wh/dia) na localizacao -5.0044471, -42.7762341.

## Base de calculo

- consumo medio diario: 0,650 kWh/dia
- potencia media equivalente: 0,650/24 ~= 0,027 kW (27 W continuos)
- campo atual: 4 x 610 W = 2,44 kWp
- bateria atual: 25,6 V 170 Ah = 4,352 kWh nominal

Estimativa solar local utilizada (PVGIS):

- geracao media com 2,44 kWp: ~10,4 kWh/dia
- fator medio local: ~4,27 kWh/kWp/dia
- pior mes aproximado: ~3,73 kWh/kWp/dia

## Diagnostico do sistema atual

- carga diaria requerida: 0,650 kWh/dia
- geracao media atual: ~10,4 kWh/dia
- excedente medio: ~9,75 kWh/dia

Conclusao:

- o inversor atual e mais que suficiente para essa carga
- o campo solar atual esta muito acima da energia diaria requerida
- a bateria atual tambem esta acima do necessario para autonomia

## Referencia de autonomia da bateria

Energia util por bateria (aprox.): ~3,6 kWh em AC, considerando perdas.

- 1 bateria: 3,6/0,650 ~= 5,5 dias de autonomia teorica
- 2 baterias: ~11 dias
- 3 baterias: ~16,6 dias

Observacao:

- autonomia real depende de perdas, perfil horario de carga e profundidade de descarga configurada

## Cenarios praticos para decisao

### Cenario 1 - manter o sistema atual

Perfil:

- objetivo: maximizar robustez e reserva energetica
- estrategia: manter 4 placas e 1 bateria

Resultado esperado:

- ampla margem de geracao diaria
- alta tolerancia a dias ruins e variacoes de consumo
- baixa probabilidade de falta de energia para essa carga media

### Cenario 2 - otimizar custo operacional

Perfil:

- objetivo: reduzir estresse de bateria e ciclos desnecessarios
- estrategia: manter sistema fisico e ajustar parametros de operacao

Ajustes recomendados:

- usar prioridade solar para alimentar carga e carregar bateria
- evitar descargas profundas frequentes
- revisar cortes de baixa tensao para preservar vida util

Resultado esperado:

- maior vida util da bateria
- menor aquecimento e menor desgaste por ciclagem
- operacao mais eficiente para consumo leve

## Comparativo rapido

| Item | Cenario 1 - Manter atual | Cenario 2 - Otimizar operacao |
| --- | --- | --- |
| Investimento inicial | Nenhum | Nenhum |
| Complexidade | Baixa | Baixa/Media |
| Folga energetica | Muito alta | Muito alta |
| Vida util de bateria | Boa | Melhor |
| Melhor para | Simplicidade | Eficiencia e longevidade |

## Ordem recomendada de decisao

1. Confirmar no historico de consumo que a media correta e 0,650 kWh/dia
2. Manter a infraestrutura atual sem expansao
3. Ajustar apenas parametros de operacao para aumentar vida util da bateria

Motivo da ordem:

- o sistema atual ja atende com ampla folga
- nao ha necessidade tecnica de ampliar placas ou banco de baterias para essa carga

## Arquitetura eletrica sugerida

Nao ha necessidade de mudanca estrutural para 0,650 kWh/dia.

Prioridade deve ser:

- manutencao preventiva
- configuracao conservadora da bateria
- monitoramento simples de geracao e estado de carga

## Lista de melhorias tecnicas

### Placas e lado FV

- manter o arranjo atual
- garantir limpeza periodica e inspecao visual
- revisar conectores e aperto em manutencoes programadas

### Baterias e lado DC

- evitar ciclos profundos sem necessidade
- manter parametros de carga dentro da faixa do fabricante
- acompanhar temperatura e estado de saude

### Inversor e configuracao

Os parametros atuais do SP-4200 podem ser mantidos como base.

Se o objetivo for preservar bateria:

- priorizar solar e rede conforme estrategia de uso
- ajustar limites para evitar descarga excessiva

## Sinais de que a operacao esta boa

- bateria fecha o dia com bom estado de carga
- baixa ocorrencia de alarmes
- temperatura dos componentes em faixa normal
- estabilidade de alimentacao das cargas

## Sinais de que precisa revisar ajustes

- bateria chegando com frequencia em tensao baixa
- alarmes recorrentes sem aumento relevante de carga
- variacao de autonomia sem mudanca de consumo

## Decisao rapida

Para media de 0,650 kWh/dia:

- nao expandir o sistema
- focar em ajuste fino e preservacao da bateria

Se o consumo real for maior que o informado, recalcular com base em kWh/dia medidos na fatura.
