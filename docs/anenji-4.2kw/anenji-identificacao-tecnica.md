# Identificacao tecnica - ANENJI ANJ-4000W-24V

## Objetivo

Consolidar os dados de placa/etiqueta e do menu de programas para referencia tecnica e conferencia de limite.

## Inverter mode

- rated power: 4200 VA / 4200 W
- DC input: 24 Vdc, 158 A
- AC output: 230 Vac, 50/60 Hz, 18.3 A, 1 fase

## AC charger mode

- AC input: 230 Vac, 50/60 Hz, 27.7 A, 1 fase
- DC output: 27 Vdc
- max charge current (AC): 80 A (default 30 A)
- max charge current (PV+AC): 100 A

## Solar charger mode

- max PV array power: 4500 W
- min solar voltage: 60 Vdc
- max solar voltage (Voc): 500 Vdc
- max charge current: 100 A

## Interpretao pratica

- o inversor suporta ate 4200 W nominais
- a bateria do sistema continua limitando uso continuo em torno de 3000 W
- operacao segura depende de nao somar cargas pesadas simultaneas

## Programas do menu (fonte ANENJI)

- documento base: 4-2kw.pdf
- paginas: 11 a 17
- arquivo utilizado na sessao: /Users/alyssondaniel/Downloads/4-2kw.pdf

Programas mais relevantes para seu cenario:

- 01: output source priority (usar SBU priority)
- 11: maximum utility charging current (usar 10A ou 20A)
- 16: charger source priority (usar Only Solar no dia a dia)
- 26/27: tensoes de carga (bulk/float)
- 29: low DC cut-off voltage
- 33/39: equalizacao (manter desativada para LiFePO4)
- 45: low DC cut-off SOC

## Referencias

- anenji-manual-final-anj4000-24v.md
- anenji-plano-operacao-cenario-atual.md
- anenji-opcoes-paginas-11-17-4-2kw.md
