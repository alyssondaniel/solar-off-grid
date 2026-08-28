# Manual final - Sumry SP-4200

## Escopo

Este documento consolida a configuracao recomendada para o conjunto abaixo:

- inversor Sumry SP-4200, 24 V, 3800 W
- 4 modulos solares de 610 W, total de 2440 Wp
- 1 bateria Felicity LiFePO4 25,6 V 170 Ah, 4,4 kWh

O objetivo e operar com boa estabilidade, priorizar o solar e preservar a bateria.

## Resumo executivo

### Parametros finais recomendados

| Parametro                        | Valor                |
| -------------------------------- | -------------------- |
| Output source priority           | `01 SBU`             |
| Maximum charging current         | `02 80A`             |
| AC input range                   | `03 APL`             |
| Battery type                     | `05 USE`             |
| Output voltage                   | `08 230V`            |
| Output frequency                 | `09 60`              |
| Maximum utility charging current | `11 10A` a `11 80A`  |
| Back to utility                  | `12 25.5V`           |
| Back to battery                  | `13 26.5V`           |
| Charger source priority          | `16 OSO` ou `16 CSO` |
| Bulk / Absorption                | `26 28.4V`           |
| Float                            | `27 27.0V`           |
| Low DC cut-off                   | `29 24.0V`           |
| Equalization                     | `33 EdS`             |

### Limites reais do sistema

- uso continuo confortavel na bateria: ate `2500 W`
- uso continuo aceitavel: ate `3000 W`
- acima de `3000 W`: evitar ou usar com apoio da rede
- o limitador real do sistema e a bateria, nao o inversor

### Arranjo recomendado das placas

- usar `4S1P`, ou seja, 4 placas em serie
- confirmar `Voc` total do string abaixo de `450 Vdc`

## Identificacao no inversor pelas paginas 17 a 21

Com base nas paginas 17 a 21 do manual, estes sao os programas e codigos relevantes para identificar cada ajuste direto no display.

| Funcao                         | Programa | Codigo / Optional Item                | Recomendacao                       |
| ------------------------------ | -------- | ------------------------------------- | ---------------------------------- |
| Prioridade da saida            | `01`     | `SUB` / `SBU`                         | usar `01 SBU`                      |
| Corrente maxima total de carga | `02`     | `10A` a `110A`                        | usar `02 80A`                      |
| Faixa de entrada AC            | `03`     | `APL` / `UPS`                         | usar `03 APL`                      |
| Tipo de bateria                | `05`     | `AGn` / `FLd` / `USE` / `LIb` / `485` | usar `05 USE`                      |
| Tensao de saida                | `08`     | `220V` / `230V` / `240V`              | usar `08 230V`                     |
| Frequencia de saida            | `09`     | `50` / `60`                           | usar `09 60`                       |
| Corrente de carga pela rede    | `11`     | `10A` a `80A`                         | usar so se quiser limitar carga AC |
| Volta para rede em `SBU`       | `12`     | `22.0V` a `25.5V`                     | usar `12 25.5V`                    |
| Volta para bateria em `SBU`    | `13`     | `FUL` ou `24.0V` a `29.0V`            | usar `13 26.5V`                    |
| Prioridade da fonte de carga   | `16`     | `CSO` / `SNU` / `OSO`                 | usar `16 OSO` ou `16 CSO`          |
| Tensao de bulk                 | `26`     | ajustavel em `0.1V`                   | usar `26 28.4V`                    |
| Tensao de float                | `27`     | ajustavel em `0.1V`                   | usar `27 27.0V`                    |
| Corte por baixa tensao         | `29`     | ajustavel em `0.1V`                   | usar `29 24.0V`                    |

### Perfis de tensao para bateria Felicity FLA24170-EU

| Perfil            | Programa 12 | Programa 13   | Programa 29   |
| ----------------- | ----------- | ------------- | ------------- |
| Equilibrado       | `25.0V`     | `26.5V`       | `23.5V`       |
| Anti-zero         | `25.5V`     | `26.5V`       | `24.0V`       |
| Ultra conservador | `25.5V`     | `27.0V`       | `24.5V`       |
| Equalizacao       | `33`        | `EEN` / `EdS` | usar `33 EdS` |

### Interpretacao correta do programa `16`

- `16 CSO`: solar first. O solar carrega primeiro, e a rede carrega apenas quando nao houver solar.
- `16 SNU`: solar and utility. Solar e rede carregam ao mesmo tempo.
- `16 OSO`: only solar. Apenas o solar carrega a bateria, mesmo com rede disponivel.

Para o seu caso:

- usar `16 OSO` se voce quer impedir carga da bateria pela rede
- usar `16 CSO` se aceita rede carregando a bateria apenas na ausencia de solar

### Regra de bypass para sobrecarga (programa `23`)

- operacao diaria: manter bypass desativado (`bYd`) para preservar previsibilidade da estrategia
- contingencia de continuidade: habilitar bypass temporariamente e retornar para `bYd` apos normalizacao

### Observacao de degrau no painel

- neste equipamento, os programas `12` e `13` podem operar em passos de `0.5V`
- por isso, os setpoints praticos validos sao `12 25.5V` e `13 26.5V`

## Base tecnica da recomendacao

### Inversor

- potencia nominal: `4200 VA / 3800 W`
- banco de baterias: `24 Vdc`
- carga solar maxima: `110 A`
- janela MPPT: `55 a 450 Vdc`
- `Voc` FV maximo: `450 Vdc`
- saida AC: `230 Vac`, `50/60 Hz`

### Bateria

- quimica: `LiFePO4`
- tensao nominal: `25,6 V`
- energia nominal: `4,4 kWh`
- faixa de operacao: `22,4 a 28,8 V`
- corrente maxima continua: `120 A`
- potencia maxima de carga/descarga: `3000 W`

### Consequencia pratica

Embora o inversor suporte mais de `3000 W`, a bateria e quem limita o uso continuo. Por isso, a configuracao deve proteger a descarga e evitar operacao prolongada em alta carga fora do horario solar.

## Como configurar no painel

Aplicar nesta ordem, ja organizada por `option/code`:

1. `01 Output source priority` -> `SBU`
2. `02 Maximum charging current` -> `80 A`
3. `03 AC input range` -> `APL`
4. `05 Battery type` -> `USE`
5. `08 Output voltage` -> `230 V`
6. `09 Output frequency` -> `60 Hz`
7. `11 Maximum utility charging current` -> usar apenas se precisar limitar a carga AC
8. `12 Back to utility` -> `25.2 V`
9. `13 Back to battery` -> `26.4 V`
10. `16 Charger source priority` -> `OSO` ou `CSO`
11. `26 Bulk / Absorption` -> `28.4 V`
12. `27 Float` -> `27.0 V`
13. `29 Low DC cut-off` -> `24.0 V`
14. `33 Equalization` -> `EdS`

### Roteiro final programa por programa

Se a ideia for configurar olhando apenas o numero do programa e o codigo do display, use esta sequencia:

1. `01` -> selecionar `SBU`
2. `02` -> selecionar `80A`
3. `03` -> selecionar `APL`
4. `05` -> selecionar `USE`
5. `08` -> selecionar `230V`
6. `09` -> selecionar `60`
7. `11` -> ajustar apenas se quiser limitar carga pela rede
8. `12` -> ajustar para `25.5V`
9. `13` -> ajustar para `26.5V`
10. `16` -> selecionar `OSO` para apenas solar carregar a bateria
11. `26` -> ajustar para `28.4V`
12. `27` -> ajustar para `27.0V`
13. `29` -> ajustar para `24.0V`
14. `33` -> selecionar `EdS`

Se voce quiser permitir apoio da rede na carga da bateria apenas quando nao houver solar, troque apenas este item:

- `16` -> usar `CSO` no lugar de `OSO`

Se quiser limitar a carga pela rede quando `16 CSO` estiver ativo, ajuste tambem:

- `11` -> escolher o menor valor que atenda sua necessidade, por exemplo `10A` ou `20A`

## Estrategia de operacao

### Durante o dia

- concentrar cargas mais pesadas no horario de maior irradiacao
- usar micro-ondas, air fryer e bomba preferencialmente com sol
- aproveitar o solar para atender a casa e recuperar a bateria

### Durante a noite

- manter cargas leves e moderadas sempre que possivel
- evitar combinar equipamentos resistivos e motores
- considerar `2500 W` como faixa de atencao e `3000 W` como teto pratico

### Em dias nublados

- reduzir consumo pesado
- se necessario, usar `16 CSO` e ajustar `11` para o menor valor aceitavel
- nao aprofundar descarga apenas para sustentar cargas fortes

## Cargas e combinacoes

### Tranquilas

- iluminacao + TV + roteador + ventilador
- iluminacao + TV + geladeira + ventilador
- notebooks + TV + geladeira

### Aceitaveis com atencao

- geladeira + micro-ondas
- geladeira + air fryer
- bomba pequena + cargas leves

### Nao recomendadas na bateria

- micro-ondas + air fryer + geladeira
- ferro + air fryer + cargas leves
- bomba + micro-ondas + geladeira
- chuveiro eletrico

## Autonomia pratica

Usando como base cerca de `3.5 a 3.9 kWh` uteis:

- `300 W`: `11 a 13 horas`
- `500 W`: `7 a 8 horas`
- `1000 W`: `3.5 a 4 horas`
- `2000 W`: `1.7 a 2 horas`

Equipamentos resistivos pesados normalmente sao usados por minutos, nao por horas, entao a leitura correta e de consumo equivalente.

## Ligacao e protecoes

### Ligacao resumida

```text
4 placas em serie -> PV+ / PV-
Bateria 25,6 V -> BAT+ / BAT-
Rede AC -> AC INPUT
Saida do inversor -> quadro de cargas
```

### Protecoes recomendadas

- seccionadora DC no lado FV
- DPS DC compativel com a tensao do string
- fusivel DC ou disjuntor DC entre bateria e inversor
- disjuntor AC na entrada da rede
- disjuntor AC na saida para o quadro
- aterramento conforme norma local

### Cabos e criterio inicial

- string FV: cabo solar apropriado
- bateria para inversor: `35 mm2` minimo em trecho curto; `50 mm2` preferivel
- rever bitola final conforme distancia, queda de tensao e metodo de instalacao

## Comissionamento rapido

### Antes de energizar

- conferir polaridade da bateria
- conferir polaridade do string solar
- conferir aperto dos terminais
- conferir protecoes DC e AC

### Sequencia de energizacao

1. ligar bateria
2. esperar inicializacao do inversor
3. ligar solar
4. ligar rede AC, se usada
5. conectar cargas

### Sequencia de desligamento

1. desligar cargas
2. desligar rede AC
3. desligar solar
4. desligar bateria por ultimo

## Ajustes rapidos se algo sair do esperado

| Sintoma                              | Ajuste inicial                           |
| ------------------------------------ | ---------------------------------------- |
| Troca frequente entre rede e bateria | subir `Back to utility` para `24.4 V`    |
| Bateria alta por muitas horas        | reduzir `Bulk` para `28.2 V`             |
| Corte do BMS em pico                 | reduzir combinacoes de cargas pesadas    |
| Rede carregando sem necessidade      | usar `16 OSO` ou revisar `16 CSO` e `11` |

## Referencias

- `configuracao-inversor-sumry-sp4200.md`: documento detalhado
- `guia-rapido-sumry-sp4200.md`: consulta imediata
