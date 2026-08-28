# Opcoes das paginas 11 a 17 - ANENJI 4-2kw

## Fonte

- arquivo: 4-2kw.pdf (ANENJI)
- paginas: 11 a 17
- objetivo: mapear programas e opcoes reais de menu

Observacao de degrau real no painel:

- programas 12 e 13 podem operar em passos de `0.5V`
- no perfil anti-zero, usar `12 25.5V` e `13 26.5V`

## Programas identificados e recomendacao

| Programa | Descricao (manual)                        | Opcoes visiveis                                           | Recomendacao para seu cenario                                     |
| -------- | ----------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------------------- |
| 01       | Output source priority                    | Utility first / Solar first / SBU priority / SUF priority | usar SBU priority                                                 |
| 02       | Maximum charging current (total)          | faixa configuravel, default 60A                           | usar 60A (conservador)                                            |
| 06       | Auto restart when overload occurs         | disable / enable(default)                                 | manter enable                                                     |
| 07       | Auto restart when over temperature occurs | disable / enable(default)                                 | manter enable                                                     |
| 08       | Output voltage                            | 220V / 230V(default) / 240V                               | usar 230V                                                         |
| 09       | Output frequency                          | 50Hz(default) / 60Hz                                      | usar 60Hz                                                         |
| 10       | Auto bypass                               | manual(default) / auto                                    | usar manual no dia a dia; auto so em contingencia de continuidade |
| 11       | Maximum utility charging current          | faixa 2A ate max AC                                       | usar 10A ou 20A                                                   |
| 12       | Back to utility (SBU)                     | faixa de tensao configuravel                              | usar 25.5V                                                        |
| 13       | Back to battery (SBU)                     | faixa de tensao configuravel                              | usar 26.5V                                                        |
| 16       | Charger source priority                   | Solar first / Solar and Utility(default) / Only Solar     | usar Only Solar no dia a dia                                      |
| 25       | Modbus ID                                 | 001(default)~247                                          | manter default se nao usar monitoramento                          |
| 26       | Bulk charging voltage (CV)                | 24V: default 28.2V, range 24.0~30.0V                      | usar 28.2V a 28.4V                                                |
| 27       | Floating charging voltage                 | 24V default 27.0V                                         | usar 27.0V                                                        |
| 29       | Low DC cut-off voltage                    | configuravel (modelo 24V)                                 | usar 24.0V                                                        |
| 33       | Battery equalization                      | enable/disable                                            | usar disable para LiFePO4                                         |
| 34       | Battery equalization voltage              | 24V default 29.2V                                         | ignorar se 33=disable                                             |
| 35       | Battery equalized time                    | default 60 min                                            | ignorar se 33=disable                                             |
| 36       | Battery equalized timeout                 | default 120 min                                           | ignorar se 33=disable                                             |
| 37       | Equalization interval                     | default 30 days                                           | ignorar se 33=disable                                             |
| 39       | Equalization activated immediately        | enable / disable(default)                                 | manter disable                                                    |
| 45       | Low DC cut-off SOC                        | default 20% (3%~30%)                                      | manter 20%                                                        |
| 46       | Maximum discharge current protection      | default OFF                                               | manter OFF ate ajuste tecnico dedicado                            |

## Perfis de uso

### Perfil diario (preservar bateria)

- 01: SBU priority
- 02: 60A
- 03 | APL
- 05 | USE
- 06 | LTD
- 07 | LTD
- 08: 230V
- 09: 60Hz
- 10: manual - bypass
- 11: 10A (ou 20A)
- 12: 25.5V - sai da bateria pra concersionária
- 13: 26.5V
- 16: Only Solar
- 18 | nd1
- 19 | BEP
- 20 | LOF
- 23 | byd - bypass quando tiver alta potencia
- 26: 28.2V a 28.4V | 24.7
- 27: 27.0V | 24
- 29: 24.0V | 20
- 32 | Aut
- 33: disable
- 39: disable
- 45: 20%

### Perfil contingencia (nublado + rede instavel)

- manter configuracao acima
- se necessario suporte da rede para carga da bateria: 16 em Solar and Utility por periodo curto
- reduzir programa 11 para 10A ou 20A
- ao normalizar, voltar 16 para Only Solar

## Observacoes

- para sua bateria LiFePO4, evitar equalizacao (33 disable)
- manter uma carga pesada por vez continua sendo a regra principal
- os itens 34/35/36/37/39 so ganham efeito pratico se equalizacao estiver ativada
