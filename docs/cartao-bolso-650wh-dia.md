# Cartao de bolso - 0,650 kWh/dia

## Uso imediato

- perfil: 0,650 kWh/dia (650 Wh/dia)
- potencia media: ~27 W
- objetivo: preservar bateria e evitar ciclos desnecessarios

## Setpoints essenciais

| Programa | Valor             |
| -------- | ----------------- |
| 01       | SBU               |
| 02       | 80A               |
| 03       | APL               |
| 05       | USE               |
| 08       | 230V              |
| 09       | 60                |
| 11       | 10A (se usar CSO) |
| 12       | 24.5V             |
| 13       | 27.0V             |
| 16       | OSO (padrao)      |
| 26       | 28.4V             |
| 27       | 27.0V             |
| 29       | 22.8V             |
| 33       | EdS               |

## Regra OSO/CSO

- manter OSO no uso normal
- trocar para CSO so em sequencia de dias sem sol
- quando usar CSO, limitar programa 11 em 10A ou 20A
- voltar para OSO assim que a geracao solar normalizar

Regra rapida de acionamento do CSO:

- 1 dia ruim: manter OSO
- 2 a 3 dias ruins seguidos: pode usar CSO temporariamente
- normalizou o sol: retornar para OSO no mesmo dia

## 3 regras de operacao

1. Cargas mais pesadas durante o dia.
2. A noite, manter cargas leves/moderadas.
3. Evitar picos simultaneos (micro-ondas + air fryer + bomba).

## Acao rapida por sintoma

| Sintoma                      | Acao                                  |
| ---------------------------- | ------------------------------------- |
| troca frequente rede/bateria | subir programa 12 para 24.5V          |
| bateria descarrega cedo      | reduzir picos e revisar programa 16   |
| rede carrega sem querer      | confirmar programa 16 em OSO          |
| muitos ciclos de bateria     | transferir consumo para horario solar |

## Decisao direta

- nao expandir sistema para 0,650 kWh/dia
- manter configuracao conservadora
- foco em vida util da bateria
