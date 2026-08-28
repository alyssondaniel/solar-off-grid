# Manual final - ANENJI ANJ-4000W-24V

## Escopo

Este documento consolida a operacao recomendada para o sistema com:

- inversor ANENJI ANJ-4000W-24V
- banco de bateria 24 V (Felicity 25.6 V, 4.4 kWh)
- mesmos equipamentos e cargas informados no cenario anterior

## Dados tecnicos confirmados na etiqueta

- potencia nominal: 4200 VA / 4200 W
- entrada DC: 24 Vdc, 158 A
- saida AC: 230 Vac, 50/60 Hz, 18.3 A, 1 fase
- carga AC maxima: 80 A (default 30 A)
- carga maxima PV+AC: 100 A
- potencia FV maxima: 4500 W
- tensao FV minima: 60 Vdc
- tensao FV maxima (Voc): 500 Vdc
- protecao: IP21 (uso interno)

## Limite real de operacao

No seu sistema, o limitador pratico continuo segue sendo a bateria.

Com bateria de 4.4 kWh e limite de 3000 W no banco:

- faixa confortavel: ate 2500 W simultaneos
- faixa de atencao: 2500 a 3200 W (tempo curto)
- acima de 3200 W: evitar na bateria

## Configuracao operacional recomendada

Quando o firmware apresentar menu equivalente ao modelo anterior, manter os mesmos principios:

- prioridade de fonte: solar/bateria para uso normal
- priorizar apenas solar para carga da bateria no dia a dia (OSO, quando existir)
- usar modo com rede para carga da bateria (CSO, quando existir) apenas em contingencia
- limitar corrente de carga AC para 10 A ou 20 A quando houver necessidade de preservar bateria

## Programas de ajuste (paginas 11 a 17 do 4-2kw.pdf)

| Programa | Ajuste recomendado     |
| -------- | ---------------------- |
| 01       | SBU priority           |
| 02       | 60A                    |
| 08       | 230V                   |
| 09       | 60Hz                   |
| 10       | manual                 |
| 11       | 10A ou 20A             |
| 12       | 25.5V                  |
| 13       | 26.5V                  |
| 16       | Only Solar (dia a dia) |
| 26       | 28.2V a 28.4V          |
| 27       | 27.0V                  |
| 29       | 24.0V                  |
| 33       | disable                |
| 39       | disable                |
| 45       | 20%                    |

Observacao:

- em contingencia, 16 pode ser mudado temporariamente para Solar and Utility
- se usar Solar and Utility, limitar 11 em 10A ou 20A

Perfis de tensao para Felicity FLA24170-EU:

- equilibrado: 12 em 25.0V, 13 em 26.5V, 29 em 23.5V
- anti-zero: 12 em 25.5V, 13 em 26.5V, 29 em 24.0V
- ultra conservador: 12 em 25.5V, 13 em 27.0V, 29 em 24.5V

## Compatibilidade com as cargas do seu cenario

Cargas informadas:

- geladeira
- maquina de lavar 1500 a 1900 W
- purificador 110 W
- air fryer 1700 W
- fogao de inducao 2000 W
- 2 notebooks + monitor
- ventilador
- ar condicionado 9000 BTU (~800 W)
- cafeteira 600 W
- TV 75 + TV 35
- lampadas e cameras

Conclusao pratica:

- suficiente com gestao de simultaneidade
- insuficiente para operar varias cargas pesadas ao mesmo tempo sem risco

## Combinacoes de uso

Pode:

- geladeira + TVs + notebooks + lampadas + cameras
- ar condicionado + cargas leves
- cafeteira + cargas leves (curto tempo)

Atencao:

- maquina + cargas leves
- ar condicionado + fogao (curto tempo)
- ar condicionado + air fryer (curto tempo)

Evitar:

- maquina + air fryer
- maquina + fogao
- air fryer + fogao
- fogao + air fryer + ar condicionado

## Estrategia por horario

- 09:00-16:00: cargas pesadas, uma por vez
- 16:00-19:00: reduzir simultaneidade
- 19:00-23:00: cargas leves/moderadas
- madrugada: manter essenciais

## Contingencia (nublado + queda de rede)

1. desligar imediatamente cargas pesadas
2. manter cargas essenciais
3. estabilizar por 10 a 15 minutos
4. religar uma carga por vez

## Checklist final de operacao

- manter no maximo 1 carga pesada por vez
- concentrar carga pesada no horario solar
- em alarme, voltar para essenciais
- usar CSO apenas quando necessario
- retornar para OSO quando normalizar

## Referencias

- anenji-guia-rapido-anj4000-24v.md
- anenji-passo-a-passo-painel-anj4000-24v.md
- anenji-checklist-configuracao-anj4000-24v.md
- anenji-quadro-semaforo-cargas.md
- anenji-plano-contingencia.md
- anenji-opcoes-paginas-11-17-4-2kw.md
