# Plano de operacao - SUMRY SP-4200 (cenario atual)

## Base tecnica

- inversor Sumry SP-4200: 3800W
- banco 24V com bateria LiFePO4 4.4kWh
- arranjo solar 4x610W (2440Wp)

## Limite real de operacao

- faixa confortavel: ate 2500W
- faixa de atencao: 2500W a 3000W
- acima de 3000W: evitar na bateria

## Programas recomendados (resumo)

- 01 SBU
- 02 80A
- 03 APL
- 05 USE
- 08 230V
- 09 60Hz
- 11 10A ou 20A quando usar CSO
- 12 25.5V (anti-zero)
- 13 26.5V
- 16 OSO (padrao) / CSO (contingencia)
- 26 28.4V
- 27 27.0V
- 29 24.0V
- 33 EdS

## Perfis prontos - Felicity FLA24170-EU (24V LiFePO4, 170Ah)

Perfil equilibrado (recomendado):

- 12 25.0V
- 13 26.5V
- 29 23.5V

Perfil anti-zero (recomendado para seu caso):

- 12 25.5V
- 13 26.5V
- 29 24.0V

Perfil ultra conservador (maxima protecao):

- 12 25.5V
- 13 27.0V
- 29 24.5V

## Combinacoes praticas

Pode:

- geladeira + TVs + notebooks + lampadas + cameras
- ar condicionado + cargas leves

Atencao:

- maquina + cargas leves
- ar + air fryer por periodo curto

Evitar:

- maquina + air fryer
- maquina + fogao
- air fryer + fogao

## Regra operacional unica

- no maximo 1 carga pesada por vez
- carga pesada preferencialmente com sol
- em alarme, voltar para essenciais

## Referencias

- manual-final-sumry-sp4200.md
- guia-rapido-sumry-sp4200.md
- passo-a-passo-painel-sumry-sp4200.md
- checklist-configuracao-sumry-sp4200.md
