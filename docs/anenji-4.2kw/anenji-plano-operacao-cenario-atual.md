# Plano de operacao - ANENJI ANJ-4000W-24V (cenario atual)

## Base tecnica usada

Dados da etiqueta do inversor ANENJI:

- modelo: ANJ-4000W-24V
- potencia nominal inversor: 4200 VA / 4200 W
- entrada DC: 24 Vdc, 158 A
- saida AC: 230 Vac, 50/60 Hz, 18.3 A
- carga AC maxima: 80 A (default 30 A)
- carga maxima PV+AC: 100 A
- MPPT solar: potencia FV maxima 4500 W
- tensao solar minima: 60 Vdc
- tensao solar maxima (Voc): 500 Vdc

Dados da bateria (mantidos do seu sistema):

- Felicity 25.6 V, 4.4 kWh
- corrente continua maxima: 120 A
- potencia maxima carga/descarga: 3000 W

## Conclusao tecnica principal

Mesmo com inversor de 4200 W, o limite pratico continuo ainda e a bateria (3000 W).

Para operacao segura no dia a dia:

- faixa confortavel: ate 2500 W simultaneos
- faixa de atencao: 2500 a 3200 W (curto periodo)
- evitar acima de 3200 W na bateria

## Compatibilidade com seus equipamentos

Equipamentos informados:

- geladeira (34.6 kWh/mes)
- maquina de lavar (1500 a 1900 W)
- purificador (110 W)
- air fryer (1700 W)
- fogao de inducao (2000 W)
- 2 notebooks + monitor
- ventilador
- ar condicionado 9000 BTU (~800 W)
- cafeteira (600 W)
- TV 75 + TV 35
- lampadas e cameras

### Suficiencia no ANENJI

- sim, para uso com gestao de simultaneidade
- nao, para uso livre de varias cargas pesadas ao mesmo tempo

## Combinacoes praticas

Seguras:

- geladeira + TVs + notebooks + lampadas + cameras
- ar condicionado + cargas leves
- cafeteira + cargas leves (tempo curto)

Atencao:

- maquina + cargas leves
- ar condicionado + fogao de inducao (tempo curto)
- ar condicionado + air fryer (tempo curto)

Evitar:

- maquina + air fryer
- maquina + fogao de inducao
- air fryer + fogao de inducao
- fogao + air fryer + ar condicionado

## Janela de uso recomendada

- 09:00-16:00: executar cargas pesadas (1 por vez)
- 19:00-23:00: manter cargas leves/moderadas
- madrugada: priorizar cargas essenciais

## OSO/CSO

- modo padrao: OSO (evita rede carregando bateria sem necessidade)
- usar CSO apenas em sequencia de dias ruins de sol ou contingencia
- se usar CSO, limitar carga AC (10A ou 20A) para reduzir estresse da bateria

Correspondencia no menu (4-2kw.pdf paginas 11 a 17):

- programa 16: Only Solar (OSO) / Solar and Utility (CSO)
- programa 11: limite de carga AC

## Programas recomendados (resumo)

- 01 SBU priority
- 02 60A
- 08 230V
- 09 60Hz
- 10 manual
- 11 10A ou 20A
- 12 25.5V
- 13 26.5V
- 16 Only Solar (dia a dia)
- 26 28.2V a 28.4V
- 27 27.0V
- 29 24.0V
- 33 disable
- 39 disable
- 45 20%

## Perfis prontos - Felicity FLA24170-EU (24V LiFePO4, 170Ah)

Perfil equilibrado:

- 12 25.0V
- 13 26.5V
- 29 23.5V

Perfil anti-zero (recomendado):

- 12 25.5V
- 13 26.5V
- 29 24.0V

Perfil ultra conservador:

- 12 25.5V
- 13 27.0V
- 29 24.5V

## Regra operacional unica

- no maximo 1 carga pesada por vez
- carga pesada preferencialmente no horario solar
- se houver alarme, voltar para cargas essenciais
