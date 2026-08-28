# Operacao rapida para 0,650 kWh/dia

## Perfil considerado

- consumo medio diario: 0,650 kWh/dia (650 Wh/dia)
- potencia media equivalente: ~27 W continuos
- sistema: Sumry SP-4200 + 4 placas de 610 W + bateria 25,6 V 170 Ah

Para esse perfil, o sistema atual ja opera com ampla folga. O foco deve ser preservar a bateria.

## Setpoints recomendados (uso diario)

| Programa | Valor recomendado | Motivo                                             |
| -------- | ----------------- | -------------------------------------------------- |
| 01       | SBU               | prioriza bateria/solar na saida                    |
| 02       | 80A               | limite global de carga conforme configuracao atual |
| 03       | APL               | tolerancia adequada para entrada AC                |
| 05       | USE               | permite ajuste manual de tensoes                   |
| 08       | 230V              | padrao da instalacao                               |
| 09       | 60                | padrao local                                       |
| 11       | 10A (se usar CSO) | reduz carga AC agressiva na bateria                |
| 12       | 24.5V             | reduz chaveamento e protege bateria                |
| 13       | 27.0V             | retorno conservador para bateria                   |
| 16       | OSO (padrao)      | evita rede carregando bateria                      |
| 26       | 28.4V             | bulk dentro da faixa recomendada                   |
| 27       | 27.0V             | float conservador                                  |
| 29       | 22.8V             | evita descarga profunda excessiva                  |
| 33       | EdS               | equalizacao desligada para LiFePO4                 |

## Quando trocar OSO para CSO

Trocar temporariamente para CSO apenas se:

- houver varios dias seguidos com baixa geracao solar
- for necessario garantir carga minima da bateria para carga critica

Ao usar CSO:

- manter programa 11 em 10A ou 20A para limitar corrente da rede
- voltar para OSO quando o periodo ruim passar

## Rotina curta de operacao

1. De dia, concentrar cargas mais pesadas no horario de sol.
2. A noite, manter apenas cargas leves/moderadas.
3. Evitar picos simultaneos desnecessarios (micro-ondas + air fryer + bomba).

## Checklist semanal (2 minutos)

- verificar se a bateria termina o dia com boa carga
- verificar se houve alarmes recorrentes
- verificar aquecimento anormal em cabos/terminais
- confirmar programa 16 no modo desejado (OSO ou CSO)

## Acao rapida por sintoma

| Sintoma                                      | Ajuste inicial                                  |
| -------------------------------------------- | ----------------------------------------------- |
| troca frequente entre rede e bateria         | subir programa 12 para 24.5V                    |
| bateria descarrega cedo sem aumento de carga | reduzir picos simultaneos e revisar programa 16 |
| rede carregando quando nao deveria           | confirmar programa 16 em OSO                    |
| muitos ciclos da bateria sem necessidade     | priorizar cargas no periodo solar               |

## Decisao direta

Para media de 0,650 kWh/dia:

- manter infraestrutura atual
- nao expandir placas nem banco de baterias agora
- focar em operacao conservadora para maior vida util da bateria
