# Configuracao do inversor - ANENJI ANJ-4000W-24V

## Objetivo

Documento detalhado de configuracao do ANENJI, equivalente ao documento expandido usado no pacote Sumry.

## Base tecnica usada

- modelo: ANJ-4000W-24V
- potencia nominal: 4200VA / 4200W
- banco de baterias: 24V
- carga AC maxima: 80A (default 30A)
- carga total PV+AC: 100A
- FV maximo: 4500W
- faixa FV: 60V a 500Vdc (Voc max)

## Parametros recomendados (menu real 4-2kw)

| Programa | Valor recomendado   |
| -------- | ------------------- |
| 01       | SBU priority        |
| 02       | 60A                 |
| 08       | 230V                |
| 09       | 60Hz                |
| 10       | manual              |
| 11       | 10A ou 20A          |
| 12       | 25.5V               |
| 13       | 26.5V               |
| 16       | Only Solar (padrao) |
| 26       | 28.2V a 28.4V       |
| 27       | 27.0V               |
| 29       | 24.0V               |
| 33       | disable             |
| 39       | disable             |
| 45       | 20%                 |

## Sequencia sugerida de configuracao

1. 01 -> SBU priority
2. 02 -> 60A
3. 08 -> 230V
4. 09 -> 60Hz
5. 10 -> manual
6. 11 -> 10A ou 20A
7. 12 -> 25.5V
8. 13 -> 26.5V
9. 16 -> Only Solar
10. 26 -> 28.2V a 28.4V
11. 27 -> 27.0V
12. 29 -> 24.0V
13. 33 -> disable
14. 39 -> disable
15. 45 -> 20%

## OSO/CSO (correspondencia pratica)

- uso normal: 16 em Only Solar
- contingencia: 16 em Solar and Utility
- com contingencia: limitar 11 em 10A ou 20A
- retorno: voltar 16 para Only Solar

## Limites de operacao

- faixa confortavel: ate 2500W
- faixa de atencao: 2500W a 3200W
- acima de 3200W na bateria: evitar

## Referencias

- anenji-opcoes-paginas-11-17-4-2kw.md
- anenji-manual-final-anj4000-24v.md
- anenji-passo-a-passo-painel-anj4000-24v.md
- anenji-checklist-configuracao-anj4000-24v.md
