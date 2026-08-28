# Guia rapido - Sumry SP-4200

## Sistema

- Inversor Sumry SP-4200, 24 V, 3800 W
- 4 placas de 610 W = 2440 Wp
- Bateria Felicity LiFePO4 25,6 V 170 Ah = 4,4 kWh

## Parametros finais

| Parametro                        | Valor                |
| -------------------------------- | -------------------- |
| Output source priority           | `01 SBU`             |
| Maximum charging current         | `02 80A`             |
| AC input range                   | `03 APL`             |
| Battery type                     | `05 USE`             |
| Output voltage                   | `08 230V`            |
| Output frequency                 | `09 60`              |
| Maximum utility charging current | `11 10A` a `80A`     |
| Back to utility                  | `12 25.5V`           |
| Back to battery                  | `13 26.5V`           |
| Charger source priority          | `16 OSO` ou `16 CSO` |
| Bulk / Absorption                | `26 28.4V`           |
| Float                            | `27 27.0V`           |
| Low DC cut-off                   | `29 24.0V`           |
| Equalization                     | `33 EdS`             |

## Limites do sistema

- carga continua confortavel: ate `2500 W`
- carga continua aceitavel: ate `3000 W`
- acima de `3000 W`: evitar ou usar com apoio da rede
- o limitador real do sistema e a bateria, nao o inversor

## Arranjo recomendado

- placas em `4S1P`
- confirmar `Voc` total da string abaixo de `450 Vdc`

## Codigos principais do menu

- `01 SBU` = prioridade da saida
- `02 80A` = corrente maxima total de carga
- `03 APL` = faixa de entrada AC
- `05 USE` = tipo de bateria
- `08 230V` = tensao de saida
- `09 60` = frequencia
- `12 25.5V` = volta para rede
- `13 26.5V` = volta para bateria
- `16 OSO` = apenas solar carrega a bateria
- `16 CSO` = solar primeiro, rede carrega quando nao houver solar
- `26 28.4V` = bulk
- `27 27.0V` = float
- `29 24.0V` = corte por baixa tensao
- `33 EdS` = equalizacao desligada

## Observacao de ajuste no painel

- no seu equipamento, os programas `12` e `13` andam em degraus de `0.5V`
- por isso, os valores praticos anti-zero ficam em `12 25.5V` e `13 26.5V`

## Regra de bypass (programa 23)

- dia a dia: manter bypass desativado (`bYd`)
- contingencia de continuidade: habilitar temporariamente bypass e retornar para `bYd` quando normalizar

## Sequencia final no painel

1. `01 SBU`
2. `02 80A`
3. `03 APL`
4. `05 USE`
5. `08 230V`
6. `09 60`
7. `11 10A` ou `11 20A`, se precisar limitar carga pela rede
8. `12 25.5V`
9. `13 26.5V`
10. `16 OSO`
11. `26 28.4V`
12. `27 27.0V`
13. `29 24.0V`
14. `33 EdS`

Opcional:

- `16 CSO` se quiser que a rede carregue a bateria quando nao houver solar
- `11 10A` ou `11 20A` para limitar a carga pela rede

## Regras rapidas

- usar cargas pesadas durante o dia, com sol
- evitar combinar air fryer, micro-ondas, ferro e bomba na bateria
- nao usar chuveiro eletrico pela bateria
- manter a rede disponivel para apoio noturno se houver consumo alto

## Combinacoes praticas

### Tranquilas

- iluminacao + TV + roteador + ventilador
- iluminacao + TV + geladeira + ventilador
- notebooks + TV + geladeira

### Aceitaveis com atencao

- geladeira + micro-ondas
- geladeira + air fryer
- bomba pequena + cargas leves

### Risco alto

- micro-ondas + air fryer + geladeira
- ferro + air fryer + cargas leves
- bomba + micro-ondas + geladeira

## Sequencia de energizacao

1. ligar bateria
2. esperar o inversor inicializar
3. ligar solar
4. ligar rede AC, se usada
5. conectar as cargas

## Sequencia de desligamento

1. desligar cargas
2. desligar rede AC
3. desligar solar
4. desligar bateria por ultimo

## Se der problema

- chaveamento excessivo: subir `12` para `25.5V`

Perfis alternativos para Felicity FLA24170-EU:

- equilibrado: `12 25.0V`, `13 26.5V`, `29 23.5V`
- ultra conservador: `12 25.5V`, `13 27.0V`, `29 24.5V`
- bateria alta por muito tempo: reduzir `Bulk` para `28.2 V`
- cortes do BMS: reduzir cargas de pico e cargas simultaneas
- rede carregando sem querer: usar `16 OSO`

## Referencias

Para detalhes tecnicos, consultar `configuracao-inversor-sumry-sp4200.md`.

Para uma versao consolidada e mais limpa, consultar `manual-final-sumry-sp4200.md`.
