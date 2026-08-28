# Folha de parede A4 - ANENJI ANJ-4000W-24V

## Objetivo

Folha unica para ficar ao lado do inversor, com decisao rapida de operacao e emergencia.

## Limites do sistema (visual rapido)

- confortavel: ate 2500W
- atencao: 2500W a 3200W (curto tempo)
- evitar: acima de 3200W na bateria
- regra central: no maximo 1 carga pesada por vez

## Setpoints obrigatorios (menu real 4-2kw)

| Programa | Valor alvo          | OK  |
| -------- | ------------------- | --- |
| 01       | SBU priority        | [ ] |
| 02       | 60A                 | [ ] |
| 08       | 230V                | [ ] |
| 09       | 60Hz                | [ ] |
| 10       | manual              | [ ] |
| 11       | 10A ou 20A          | [ ] |
| 12       | 25.5V               | [ ] |
| 13       | 26.5V               | [ ] |
| 16       | Only Solar (padrao) | [ ] |
| 26       | 28.2V a 28.4V       | [ ] |
| 27       | 27.0V               | [ ] |
| 29       | 24.0V               | [ ] |
| 33       | disable             | [ ] |
| 39       | disable             | [ ] |
| 45       | 20%                 | [ ] |

## Semaforo de decisao de carga

| Estado   | Regra                             |
| -------- | --------------------------------- |
| VERDE    | cargas leves livres               |
| AMARELO  | 1 carga pesada por vez            |
| VERMELHO | cortar carga pesada imediatamente |

Evitar sempre:

- maquina + air fryer
- maquina + fogao de inducao
- air fryer + fogao de inducao

## OSO e CSO (sem duvida)

- OSO: programa 16 em Only Solar (uso normal)
- CSO: programa 16 em Solar and Utility (contingencia)
- quando CSO: limitar programa 11 em 10A ou 20A
- normalizou sol/rede: voltar programa 16 para Only Solar

## Protocolo de emergencia (30 segundos)

1. desligar cargas pesadas
2. manter so essenciais por 10 a 15 min
3. religar uma carga por vez

## Checklist de retorno ao normal

- [ ] rede estabilizada
- [ ] sem alarme no inversor
- [ ] programa 16 voltou para Only Solar
- [ ] programa 11 ajustado para 10A ou 20A so se necessario
- [ ] cargas religadas em sequencia

## Fonte

- 4-2kw.pdf, paginas 11 a 17
- base detalhada: anenji-opcoes-paginas-11-17-4-2kw.md
