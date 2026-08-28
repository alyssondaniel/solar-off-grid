# Configuracao recomendada - Sumry SP-4200

## Objetivo

Este documento registra uma configuracao recomendada para o sistema abaixo:

- Inversor Sumry SP-4200, 24 V, 3800 W, MPPT 55-450 Vdc
- 4 placas solares bifaciais de 610 W, totalizando 2440 Wp
- 1 bateria Felicity Solar LiFePO4 25,6 V 170 Ah, 4,4 kWh

O foco desta configuracao e:

- priorizar o uso do solar
- proteger a bateria LiFePO4
- evitar cortes do BMS por descarga excessiva
- manter uma operacao estavel entre solar, bateria e rede

## Resumo executivo

Esta secao resume os pontos principais para consulta rapida.

### Sistema analisado

- inversor Sumry SP-4200, 24 V, 3800 W
- 4 placas de 610 W, total de 2440 Wp
- 1 bateria Felicity LiFePO4 25,6 V 170 Ah, 4,4 kWh

### Configuracao final recomendada

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

### Limites praticos do sistema

- limite continuo mais confortavel na bateria: ate `2500 W`
- limite continuo aceitavel: ate `3000 W`
- o inversor entrega mais, mas a bateria e o limitador real do sistema
- cargas resistivas pesadas devem ser evitadas na bateria, principalmente a noite

### Arranjo recomendado

- placas em `4S1P`, com verificacao final do `Voc` total abaixo de `450 Vdc`
- carga priorizada pelo solar
- rede como apoio quando a bateria cair para `12 25.5V`

### Regras rapidas de uso

- usar cargas mais pesadas durante o dia, com sol
- evitar varios equipamentos de aquecimento ao mesmo tempo
- nao usar o sistema como se a bateria suportasse `3800 W` continuos
- acompanhar os primeiros dias para validar tensoes, temperatura de cabos e comportamento do BMS

## Resumo tecnico do sistema

### Inversor

Pela etiqueta fotografada do equipamento:

- Modelo: SP-4200
- Potencia nominal: 4200 VA / 3800 W
- Banco de baterias: 24 Vdc
- Carga solar maxima: 110 A
- Potencia FV declarada: 6000 W
- Tensao MPPT: 55-450 Vdc
- Tensao maxima de circuito aberto FV: 450 Vdc
- Saida AC: 230 Vac, 50/60 Hz

### Bateria

Pela etiqueta fotografada da bateria:

- Modelo: FLA24171-EU
- Quimica: LiFePO4
- Tensao nominal: 25,6 V
- Energia nominal: 4,4 kWh
- Faixa de operacao: 22,4-28,8 V
- Corrente maxima continua de carga/descarga: 120 A
- Potencia maxima de carga/descarga: 3000 W

### Campo solar

- 4 modulos bifaciais de 610 W
- Potencia total: 2440 Wp

## Observacao mais importante

O limitador real do sistema e a bateria, nao o inversor.

Embora o inversor suporte 3800 W, a bateria informa limite continuo de 120 A e potencia maxima de 3000 W. Em um sistema de 24 V, isso significa que cargas altas por muito tempo podem forcar a bateria e provocar atuacao do BMS.

Por isso, o uso recomendado e:

- carga continua confortavel: ate 2500 W
- carga continua aceitavel: ate 3000 W
- acima de 3000 W: somente por curtos periodos ou com apoio da rede

## Configuracao recomendada

Se o inversor oferecer o modo de bateria `USE` ou `USER`, este deve ser preferido. So use um modo `Lithium` com comunicacao se houver compatibilidade confirmada entre o protocolo do inversor e o da bateria Felicity.

### Parametros principais

- `01` Output source priority: `SBU`
- `02` Maximum charging current: `80A`
- `03` AC input range: `APL`
- `05` Battery type: `USE`
- `08` Output voltage: `230V`
- `09` Output frequency: `60`
- `11` Maximum utility charging current: usar apenas se necessario
- `12` Back to utility: `25.5V`
- `13` Back to battery: `26.5V`
- `16` Charger source priority: `OSO` ou `CSO`

### Tensoes recomendadas para a bateria

- `26` Bulk / Absorption: `28.4V`
- `27` Float: `27.0V`
- `29` Low DC cut-off: `24.0V`
- `33` Equalization: `EdS` / `OFF`

### Correntes recomendadas

- `02` Maximum total charging current: `80A`
- `11` Maximum utility charging current: usar o menor valor necessario se `16 CSO` estiver ativo

## Justificativa dos ajustes

### Tipo de bateria em modo USER

O modo `USER` permite definir tensoes coerentes com a faixa de operacao da LiFePO4. Isso e mais seguro do que depender de um preset generico.

### Tensao de bulk em 28,4 V

Esse valor carrega a bateria adequadamente sem manter o banco colado no limite superior de 28,8 V.

### Tensao de float em 27,0 V

LiFePO4 nao precisa permanecer em flutuacao alta por longos periodos. Usar um float baixo reduz estresse na bateria.

### Corte em 24,0 V

Esse valor protege melhor a bateria do que descarregar ate o extremo inferior da faixa nominal. Tambem reduz a chance de desligamento abrupto por atuacao do BMS.

### Retorno para rede em 25,2 V

Esse ponto e suficientemente conservador para evitar descarga profunda e chaveamento instavel proximo da subtensao.

### Retorno para bateria em 26,4 V

Esse ajuste reduz o efeito de comutacao frequente entre rede e bateria.

### Corrente maxima de carga em 80 A

O arranjo solar totaliza 2440 Wp. Em termos de carga de bateria no topo da tensao:

2440 W / 28,4 V ~= 86 A

Na pratica, `80 A` e um bom valor de trabalho, com folga e sem exigir o maximo do banco. O inversor suporta mais, mas nao ha vantagem real em ajustar no teto para este conjunto.

## Modo de operacao recomendado

### Perfil principal

Usar:

- Output source priority: `SBU`
- Charger source priority: `16 OSO` ou `16 CSO`

Com esse perfil:

- o solar alimenta as cargas primeiro
- o excedente vai para a bateria
- a bateria sustenta as cargas quando o solar nao for suficiente
- a rede entra quando a bateria cair para o ponto configurado de retorno

Esse e o melhor compromisso entre economia e preservacao da bateria.

### Perfil mais conservador

Caso a prioridade seja preservar ao maximo a bateria, pode-se usar um perfil equivalente a `SUB` ou outro modo em que a rede entre mais cedo. Isso reduz o uso do banco fora do horario solar.

## Ligacao recomendada das placas

A configuracao mais indicada, em principio, e:

- `4S1P`, ou seja, 4 placas em serie

Motivos:

- o MPPT aceita de 55 V a 450 Vdc
- o inversor trabalha bem com strings em tensao mais alta
- 4 modulos em serie normalmente ficam confortavelmente dentro da janela MPPT neste tipo de sistema

## Verificacao obrigatoria antes da ligacao final

Confirmar na etiqueta do modulo:

- `Voc`
- `Vmp`
- `Isc`
- `Imp`

Regra principal:

- a soma dos `Voc` das 4 placas, considerando margem para clima frio, deve permanecer abaixo de `450 Vdc`

Sem a etiqueta completa do modulo, a recomendacao de `4S1P` e a mais provavel, mas precisa dessa conferencia antes da ligacao definitiva.

## Preset final sugerido

Se for preciso definir um unico conjunto de parametros para iniciar a operacao, usar em ordem de programa:

- `01` Output source priority: `SBU`
- `02` Maximum charging current: `80A`
- `03` AC input range: `APL`
- `05` Battery type: `USE`
- `08` Output voltage: `230V`
- `09` Output frequency: `60`
- `11` Maximum utility charging current: `10A` a `80A`, se usado
- `12` Back to utility: `25.5V`
- `13` Back to battery: `26.5V`
- `16` Charger source priority: `OSO` ou `CSO`
- `26` Bulk / Absorption: `28.4V`
- `27` Float: `27.0V`
- `29` Low DC cut-off: `24.0V`
- `33` Equalization: `EdS` / `OFF`

## Sequencia pratica para configurar no inversor

Se a configuracao for feita diretamente no painel do inversor, a ordem abaixo reduz retrabalho e evita conflitos entre parametros.

### Ordem recomendada

1. Ajustar `01` para `SBU`
2. Ajustar `02` para `80A`
3. Ajustar `03` para `APL`
4. Ajustar `05` para `USE`
5. Ajustar `08` para `230V`
6. Ajustar `09` para `60`
7. Ajustar `11` apenas se quiser limitar a carga da rede
8. Ajustar `12` para `25.5V`
9. Ajustar `13` para `26.5V`
10. Ajustar `16` para `OSO` ou `CSO`
11. Ajustar `26` para `28.4V`
12. Ajustar `27` para `27.0V`
13. Ajustar `29` para `24.0V`
14. Confirmar `33` em `EdS`

### Tabela rapida de configuracao

| Item                             | Valor recomendado | Observacao                                    |
| -------------------------------- | ----------------- | --------------------------------------------- |
| Battery type                     | `USE` / `USER`    | Permite tensoes manuais para LiFePO4          |
| Output source priority           | `SBU`             | Solar e bateria primeiro, rede por ultimo     |
| Charger source priority          | `Solar first`     | Privilegia carga pelo FV                      |
| AC input range                   | `APL`             | Mais tolerante a variacoes da rede            |
| Output voltage                   | `230 V`           | Equivalente pratico para rede 220 V           |
| Output frequency                 | `60 Hz`           | Padrao local                                  |
| Maximum charging current         | `80 A`            | Limite coerente com o campo FV e a bateria    |
| Maximum utility charging current | `0 A`             | Uso normal sem carga pela rede                |
| Bulk / Absorption                | `28.4 V`          | Carga alta sem encostar no limite maximo      |
| Float                            | `27.0 V`          | Float baixo para reduzir estresse             |
| Equalization                     | `OFF`             | Nao usar em LiFePO4                           |
| Low DC cut-off                   | `24.0 V`          | Protege o banco e reduz risco de corte do BMS |
| Back to utility                  | `25.2 V`          | Volta para rede antes de descarga profunda    |
| Back to battery                  | `26.4 V`          | Evita chaveamento excessivo                   |

## Checklist apos a configuracao

Depois de salvar os ajustes, fazer esta verificacao com o sistema em operacao.

### Checklist eletrico e funcional

- confirmar se o inversor mostra bateria de 24 V corretamente
- confirmar se a tensao da bateria sobe de forma coerente durante a carga solar
- confirmar se a equalizacao permanece desligada
- confirmar se a rede nao esta carregando a bateria quando `Maximum utility charging current` estiver em `0 A`
- confirmar se o sistema entra na rede quando a bateria chegar perto de `24.2 V`
- confirmar se o sistema volta para bateria quando a tensao subir para perto de `27.0 V`
- confirmar se a corrente de carga nao ultrapassa o valor configurado
- confirmar se nao ha alarmes de sobrecarga, sobretemperatura ou erro de bateria

### Checklist de uso seguro

- evitar cargas noturnas acima de `3000 W`
- evitar ligar cargas resistivas pesadas simultaneamente na bateria
- observar se o BMS da bateria registra cortes ou alarmes
- acompanhar os primeiros dias de operacao para validar o comportamento real do sistema

## Ajustes em caso de comportamento indesejado

Se o sistema estiver chaveando com muita frequencia entre rede e bateria:

- aumentar o `Back to utility` para `24.4 V`
- manter o `Back to battery` em `27.0 V`

Se a bateria estiver chegando muito rapido ao topo e permanecendo alta por muitas horas:

- reduzir o `Bulk / Absorption` para `28.2 V`
- manter o `Float` em `27.0 V`

Se for necessario apoio leve da rede em dias de pouca irradiacao:

- ajustar `Maximum utility charging current` para `20 A`
- manter `Maximum charging current` total em `80 A`

## Ajuste opcional para maior conservacao da bateria

Se a prioridade for aumentar a vida util da bateria, considerar:

- Bulk / Absorption: `28.2 V`
- Float: `27.0 V`
- Back to utility: `24.4 V`

Isso tende a reduzir um pouco a energia extraida do banco, mas melhora a margem de seguranca operacional.

## Cargas recomendadas e nao recomendadas

Mais adequadas para esse sistema:

- iluminacao
- TV
- geladeira
- ventiladores
- eletronicos em geral

Exigem mais cuidado, principalmente fora do horario solar:

- micro-ondas
- air fryer
- ferro eletrico
- bombas
- varias cargas de aquecimento ao mesmo tempo

Nao e uma boa combinacao para esse sistema:

- chuveiro eletrico ligado pela bateria

## Tabela de cargas tipicas e combinacoes praticas

Os valores abaixo sao referencias usuais. O consumo real pode variar conforme modelo, partida do motor e modo de uso.

### Potencias tipicas

| Equipamento          | Potencia tipica                                      |
| -------------------- | ---------------------------------------------------- |
| Lampadas LED da casa | `50 a 150 W` no total                                |
| TV                   | `80 a 150 W`                                         |
| Ventilador           | `60 a 120 W`                                         |
| Geladeira            | `100 a 250 W` em operacao, com pico de partida maior |
| Notebook e roteador  | `40 a 120 W`                                         |
| Micro-ondas          | `1200 a 1600 W`                                      |
| Air fryer            | `1400 a 1800 W`                                      |
| Ferro eletrico       | `1000 a 1500 W`                                      |
| Bomba pequena        | `400 a 1200 W`, dependendo do modelo                 |
| Chuveiro eletrico    | `4500 W` ou mais                                     |

### Combinacoes normalmente tranquilas

| Combinacao                                     | Potencia estimada | Situacao  |
| ---------------------------------------------- | ----------------- | --------- |
| Iluminacao + TV + roteador + ventilador        | `250 a 500 W`     | Tranquila |
| Iluminacao + TV + geladeira + ventilador       | `350 a 700 W`     | Tranquila |
| Iluminacao + notebooks + TV + geladeira        | `400 a 800 W`     | Tranquila |
| Geladeira + ventiladores + eletronicos da casa | `500 a 1000 W`    | Tranquila |

### Combinacoes aceitaveis com atencao

| Combinacao                           | Potencia estimada | Situacao                              |
| ------------------------------------ | ----------------- | ------------------------------------- |
| Geladeira + micro-ondas              | `1400 a 1900 W`   | Aceitavel, melhor com sol             |
| Geladeira + air fryer                | `1500 a 2100 W`   | Aceitavel, melhor com sol             |
| TV + ventiladores + air fryer        | `1600 a 2200 W`   | Aceitavel, usar com atencao           |
| Bomba pequena + cargas leves da casa | `800 a 1800 W`    | Aceitavel, depende do pico de partida |

### Combinacoes que ja entram em zona de risco

| Combinacao                          | Potencia estimada | Situacao                       |
| ----------------------------------- | ----------------- | ------------------------------ |
| Micro-ondas + air fryer + geladeira | `2800 a 3800 W`   | Risco alto na bateria          |
| Ferro + air fryer + cargas leves    | `2600 a 3500 W`   | Risco alto na bateria          |
| Bomba + micro-ondas + geladeira     | `1800 a 3000+ W`  | Picos podem derrubar o sistema |
| Chuveiro + qualquer outra carga     | `Acima do limite` | Nao recomendado                |

### Regra pratica para uso diario

- abaixo de `1000 W`, o sistema trabalha com bastante folga
- entre `1000 W` e `2000 W`, o sistema opera bem, especialmente durante o dia
- entre `2000 W` e `2500 W`, o uso ja pede atencao maior fora do horario solar
- entre `2500 W` e `3000 W`, o sistema entra na faixa limite recomendada da bateria
- acima de `3000 W`, considerar apoio da rede ou evitar a combinacao

### Regra pratica para picos de partida

Mesmo quando a potencia media parece aceitavel, motores e compressores podem causar picos momentaneos. Por isso:

- evitar ligar bomba, geladeira e outras cargas de partida junto com equipamentos resistivos pesados
- se houver desligamento inesperado, avaliar se o problema foi pico e nao apenas consumo medio
- durante a noite, ser mais conservador com qualquer combinacao envolvendo motor e aquecimento

## Autonomia aproximada da bateria

Energia nominal da bateria: `4.352 kWh`

Energia util pratica, considerando margem de protecao e perdas: aproximadamente `3.5 a 3.9 kWh`

Estimativas simples:

- carga de 300 W: cerca de 11 a 13 horas
- carga de 500 W: cerca de 7 a 8 horas
- carga de 1000 W: cerca de 3,5 a 4 horas
- carga de 2000 W: cerca de 1,7 a 2 horas

Esses numeros sao aproximados e variam com temperatura, estado de carga, eficiencia do inversor e regime real de descarga.

## Autonomia aproximada por equipamento

As estimativas abaixo usam como referencia uma energia util pratica de `3.5 a 3.9 kWh`.

| Equipamento ou carga        | Potencia de referencia | Autonomia aproximada                              |
| --------------------------- | ---------------------- | ------------------------------------------------- |
| Iluminacao leve da casa     | `100 W`                | `35 a 39 horas`                                   |
| TV + roteador               | `150 W`                | `23 a 26 horas`                                   |
| Ventilador                  | `80 W`                 | `43 a 49 horas`                                   |
| Geladeira em operacao media | `150 W`                | `23 a 26 horas`                                   |
| Carga leve residencial      | `300 W`                | `11 a 13 horas`                                   |
| Carga moderada residencial  | `500 W`                | `7 a 8 horas`                                     |
| Micro-ondas                 | `1400 W`               | `2.5 a 2.8 horas` de consumo continuo equivalente |
| Air fryer                   | `1500 W`               | `2.3 a 2.6 horas` de consumo continuo equivalente |
| Ferro eletrico              | `1200 W`               | `2.9 a 3.2 horas` de consumo continuo equivalente |
| Carga alta                  | `2000 W`               | `1.7 a 2 horas`                                   |

### Como interpretar essa autonomia

- equipamentos como micro-ondas, air fryer e ferro nao ficam ligados continuamente, entao o uso real costuma ser em minutos, nao em horas
- geladeira e bomba trabalham em ciclos, portanto a autonomia real depende do tempo em que ficam efetivamente ligadas
- quanto maior a potencia instantanea, maior a exigencia sobre a bateria e maior a sensibilidade a picos

## Plano operacional sugerido para dia e noite

Uma operacao disciplinada melhora bastante a vida util da bateria e o aproveitamento do solar.

### Durante o dia

- priorizar uso de cargas pesadas enquanto ha irradiacao solar
- concentrar micro-ondas, air fryer, bomba e outros consumos fortes no periodo de sol
- observar se a bateria atinge a carga sem permanecer excessivamente alta por muitas horas
- aproveitar o horario de maior geracao para recarregar o banco e alimentar a casa

### No final da tarde

- reduzir o uso de cargas de aquecimento e motores desnecessarios
- verificar se a bateria esta entrando na noite com tensao confortavel
- evitar iniciar consumos pesados exatamente quando a geracao solar estiver caindo rapidamente

### Durante a noite

- manter apenas cargas leves e moderadas sempre que possivel
- evitar combinar micro-ondas, air fryer, ferro, bomba e outras cargas de pico
- tratar `2500 W` como limite de atencao e `3000 W` como teto pratico da bateria
- se a casa precisar de mais carga nesse horario, deixar a rede apoiar o sistema

### Em dias nublados ou chuvosos

- ser mais conservador com o banco de baterias
- considerar apoio leve da rede com `Maximum utility charging current` em `20 A`, se necessario
- evitar descarregar profundamente a bateria so para manter cargas pesadas

### Em ausencia prolongada

- manter cargas desnecessarias desligadas
- preservar o perfil de carga conservador
- acompanhar se a rede e o solar estao mantendo o sistema estavel sem alarmes

## Plano de resposta rapida para problemas comuns

Se surgir comportamento anormal, usar esta referencia rapida.

| Sintoma                                   | Possivel causa                                        | Acao inicial sugerida                                 |
| ----------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| Inversor troca muito entre rede e bateria | Tensoes de retorno muito proximas ou consumo instavel | Subir `Back to utility` para `24.4 V`                 |
| Bateria descarrega rapido a noite         | Carga noturna alta demais                             | Reduzir cargas e rever combinacoes noturnas           |
| BMS corta em pico                         | Excesso de potencia instantanea                       | Evitar combinar motores com cargas resistivas         |
| Bateria fica muito alta por muito tempo   | Bulk alto para o perfil de uso                        | Testar `Bulk` em `28.2 V`                             |
| Rede carrega a bateria sem necessidade    | Corrente AC de carga habilitada                       | Confirmar `Maximum utility charging current` em `0 A` |

## Diagrama simplificado de ligacao

O arranjo recomendado para este sistema e o seguinte:

```text
Placa 1 (+) -> (-) Placa 2 (+) -> (-) Placa 3 (+) -> (-) Placa 4

Extremidade positiva da string  -----------------------> Entrada PV+
Extremidade negativa da string  -----------------------> Entrada PV-

Bateria Felicity 25,6 V (+) ---------------------------> BAT+
Bateria Felicity 25,6 V (-) ---------------------------> BAT-

Rede AC 220/230 V -------------------------------------> AC INPUT

Saida do inversor -------------------------------------> Quadro de cargas
```

### Observacoes sobre a ligacao

- as 4 placas devem formar uma unica string em serie, isto e, `4S1P`
- instalar seccionadora e protecao DC no lado fotovoltaico
- instalar disjuntor ou fusivel adequado entre bateria e inversor
- usar cabos de bateria bem dimensionados para alta corrente em 24 V
- respeitar polaridade em todas as conexoes
- nunca ligar ou desligar o campo solar sob manipulacao insegura ou sem isolacao adequada

## Protecoes recomendadas

As protecoes abaixo nao substituem projeto eletrico, mas representam uma base prudente para esse tipo de sistema.

### Lado fotovoltaico

- seccionadora DC entre string e inversor
- DPS DC apropriado para a tensao do string
- conectores MC4 originais ou equivalentes de boa procedencia
- identificacao clara de polaridade e circuito

### Lado da bateria

- fusivel DC ou disjuntor DC entre bateria e inversor
- chave seccionadora DC para manutencao segura
- cabos curtos e bem prensados com terminais adequados
- barramento ou conexao firme, sem aquecimento em bornes

### Lado AC

- disjuntor para entrada AC da rede
- disjuntor para saida AC do inversor para o quadro de cargas
- DPS AC no quadro, quando aplicavel
- aterramento correto do sistema conforme norma local

## Materiais e boas praticas de instalacao

Itens normalmente recomendados para esse conjunto:

- cabo solar adequado para uso externo no string FV
- cabo de bateria de bitola compativel com correntes elevadas em 24 V
- terminais prensados com ferramenta adequada
- disjuntores ou fusiveis DC apropriados para corrente continua
- organizacao fisica dos cabos para evitar esforco mecanico nos bornes
- identificacao dos circuitos de bateria, solar, entrada AC e saida AC

Boas praticas importantes:

- evitar cabo longo demais entre bateria e inversor
- evitar emendas improvisadas no circuito da bateria
- reapertar bornes apos alguns dias de operacao, se o fabricante permitir
- verificar aquecimento anormal em conectores, cabos e protecoes

## Dimensionamento preliminar de correntes, cabos e protecoes

Esta secao serve como referencia inicial. A definicao final deve considerar:

- distancia real dos cabos
- metodo de instalacao
- temperatura ambiente
- queda de tensao admissivel
- norma eletrica local
- especificacao do fabricante dos cabos e protecoes

### Correntes de referencia do sistema

- campo solar: a corrente do string depende da `Imp` e `Isc` reais do modulo
- carga solar para a bateria: ate cerca de `80 A` no ajuste recomendado
- bateria em carga/descarga continua: referencia pratica de ate `120 A`
- bateria no teto do inversor: `3800 W / 24 V ~= 158 A`, valor acima do recomendado para esta bateria
- saida AC em 230 V e 3800 W: `3800 / 230 ~= 16.5 A`

### Tabela preliminar

| Trecho                  | Corrente de referencia                          | Protecao sugerida                                                    | Cabo sugerido                                          |
| ----------------------- | ----------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------ |
| String FV para inversor | Conforme `Imp` e `Isc` do modulo                | Seccionadora DC + DPS DC                                             | Cabo solar PV adequado ao string                       |
| Bateria para inversor   | Ate `120 A` continuo                            | Fusivel DC ou disjuntor DC entre `125 A` e `160 A`, conforme projeto | `35 mm2` minimo em trechos curtos; `50 mm2` preferivel |
| Entrada AC da rede      | Ate cerca de `26.2 A` pela etiqueta do inversor | Disjuntor AC conforme rede e alimentacao                             | Cabo conforme corrente, distancia e norma local        |
| Saida AC para cargas    | Ate cerca de `16.5 A` em plena carga            | Disjuntor AC compativel com o circuito de saida                      | Cabo conforme corrente, distancia e norma local        |

### Notas importantes sobre o lado da bateria

- em sistemas de `24 V`, pequenas quedas de tensao ja tem impacto relevante
- quanto menor o cabo entre bateria e inversor, melhor
- para esse conjunto, `50 mm2` costuma ser uma escolha mais robusta do que `35 mm2`, especialmente se houver picos e distancias maiores
- se o percurso for mais longo, a bitola deve ser revista com calculo de queda de tensao
- o fusivel ou disjuntor DC nao deve ser escolhido apenas pela corrente nominal, mas tambem pela capacidade de interrupcao em corrente continua

### Notas importantes sobre o lado FV

- antes da ligacao definitiva, confirmar `Voc`, `Vmp`, `Isc` e `Imp` do modulo
- a tensao total em circuito aberto do string deve permanecer abaixo de `450 Vdc`
- a seccionadora e o DPS DC precisam ser compativeis com a tensao maxima do string

### Notas importantes sobre o lado AC

- a entrada AC deve respeitar a capacidade do circuito da rede disponivel no local
- a saida AC do inversor deve alimentar um quadro de cargas adequado ao limite real do sistema
- se houver cargas criticas e cargas pesadas, o ideal e separa-las em circuitos distintos

## Checklist de comissionamento

Antes de considerar a instalacao pronta, executar esta sequencia.

### Antes de energizar

- confirmar polaridade da bateria com multimetro
- confirmar polaridade da string solar com multimetro
- confirmar continuidade de aterramento onde aplicavel
- confirmar aperto mecanico dos terminais
- confirmar que as protecoes DC e AC estao corretamente posicionadas
- confirmar que as cargas inicialmente conectadas sao moderadas

### Primeira partida

- energizar primeiro pela bateria
- observar se o inversor inicializa sem alarme
- verificar tensao da bateria no display
- ligar o solar e confirmar entrada FV no monitoramento
- ligar a rede AC e verificar se a leitura de entrada esta correta
- salvar os parametros recomendados

### Testes iniciais

- testar uma carga leve na saida AC
- observar se o fluxo de energia muda corretamente entre solar, bateria e rede
- confirmar que a carga solar respeita o limite configurado
- confirmar ausencia de cheiro de aquecimento ou ruido anormal
- acompanhar um ciclo diurno e uma transicao para o periodo noturno

## Manutencao e acompanhamento

Nas primeiras semanas, vale acompanhar estes pontos:

- tensao minima atingida pela bateria durante a noite
- tensao maxima atingida ao final da carga solar
- frequencia com que o sistema entra na rede
- temperatura percebida em cabos e terminais da bateria
- ocorrencia de alarmes no inversor ou no BMS

Se tudo estiver estavel, a configuracao pode ser mantida como padrao de operacao.

## Sequencia recomendada de energizacao

Para reduzir risco de falha de inicializacao ou leitura incorreta de tensao, a sequencia pratica recomendada e:

1. verificar polaridade da bateria e do string solar
2. ligar primeiro a bateria ao inversor
3. aguardar o inversor inicializar corretamente
4. confirmar tensao do banco no display
5. ligar a entrada solar
6. por ultimo, ligar a rede AC de entrada, se ela for usada
7. conectar as cargas na saida do inversor somente apos a inicializacao normal

Ao desligar o sistema, fazer o inverso:

1. desligar cargas
2. desligar rede AC
3. desligar entrada solar
4. desligar bateria por ultimo

## Tabela de cenarios de uso

Os cenarios abaixo ajudam a decidir como operar o sistema no dia a dia.

| Cenario                                    | Configuracao sugerida                                  | Resultado esperado                             |
| ------------------------------------------ | ------------------------------------------------------ | ---------------------------------------------- |
| Uso diario normal                          | `SBU`, `Solar first`, rede sem carga da bateria        | Maior economia com boa protecao da bateria     |
| Dia nublado ou chuva                       | `SBU`, carga pela rede em `20 A` se necessario         | Mantem autonomia sem deixar a bateria afundar  |
| Prioridade total para vida util da bateria | `SUB` ou retorno mais cedo para rede                   | Menor profundidade de descarga                 |
| Uso noturno com carga elevada              | Manter rede disponivel e evitar uso acima de `3000 W`  | Reduz risco de corte do BMS                    |
| Casa vazia por longos periodos             | Float baixo, cargas minimizadas, monitoramento da rede | Sistema mais estavel e menor estresse no banco |

## Regras praticas de operacao

Para este conjunto, estas regras ajudam bastante:

- durante o dia, concentrar cargas mais pesadas quando houver producao solar
- a noite, evitar combinar varios equipamentos de aquecimento ao mesmo tempo
- se houver micro-ondas, air fryer ou bomba, evitar operar tudo junto pela bateria
- se a bateria estiver chegando no corte com frequencia, subir o `Back to utility`
- se a bateria estiver passando muitas horas no topo, reduzir levemente o `Bulk`

## Sinais de que a configuracao esta boa

Depois de alguns dias de uso, o comportamento esperado e:

- a bateria nao deve cair rapidamente para a faixa de corte em uso leve
- o inversor deve alternar pouco entre rede e bateria
- nao deve haver disparos frequentes do BMS
- a maior parte da carga diurna deve vir do solar
- a bateria deve encerrar o dia com tensao coerente para o perfil de consumo da casa

## Sinais de que a configuracao precisa ajuste

Vale revisar os parametros se aparecer algum destes sinais:

- o inversor troca repetidamente entre bateria e rede
- a bateria chega ao corte mesmo com consumo moderado
- o BMS interrompe descarga em picos noturnos
- a bateria fica muito tempo em tensao alta todos os dias
- a rede esta carregando a bateria sem necessidade

## Pendencias para refinamento futuro

Para validar a configuracao com mais precisao, ainda vale obter:

- foto da tela do menu do inversor com a numeracao dos programas
- etiqueta eletrica completa de uma placa solar
- confirmacao se ha comunicacao CAN ou RS485 ativa entre bateria e inversor

Com esses dados, esta configuracao pode ser refinada item a item conforme o menu exato do equipamento.
