# Checklist de configuracao - Sumry SP-4200

## Antes de entrar no menu

- [ ] Confirmar que a bateria esta ligada corretamente no inversor
- [ ] Confirmar polaridade correta do banco de 24 V
- [ ] Confirmar que as 4 placas estao em `4S1P`
- [ ] Confirmar que o `Voc` total do string esta abaixo de `450 Vdc`
- [ ] Confirmar que o inversor iniciou sem alarme

## Sequencia de configuracao no painel

- [ ] `01` -> `SBU`
- [ ] `02` -> `80A`
- [ ] `03` -> `APL`
- [ ] `05` -> `USE`
- [ ] `08` -> `230V`
- [ ] `09` -> `60`
- [ ] `11` -> definir somente se quiser limitar carga pela rede
- [ ] `12` -> `25.5V` (perfil anti-zero)
- [ ] `13` -> `26.5V`
- [ ] `16` -> `OSO` ou `CSO`
- [ ] `26` -> `28.4V`
- [ ] `27` -> `27.0V`
- [ ] `29` -> `24.0V`
- [ ] `33` -> `EdS`

## Escolha do programa 16

- [ ] Usar `16 OSO` se quiser impedir carga da bateria pela rede
- [ ] Usar `16 CSO` se quiser solar primeiro e rede carregando so quando nao houver solar

## Escolha do programa 11

- [ ] Deixar sem uso se `16 OSO` estiver ativo
- [ ] Se `16 CSO` estiver ativo, escolher o menor valor necessario
- [ ] Comecar por `11 10A` ou `11 20A` se quiser apoio leve da rede

## Verificacao apos salvar

- [ ] Confirmar no display que os programas ficaram gravados
- [ ] Confirmar que a equalizacao esta desligada
- [ ] Confirmar que a tensao da bateria sobe normalmente com o solar
- [ ] Confirmar que a rede nao esta carregando a bateria sem necessidade
- [ ] Confirmar que a troca para rede acontece perto de `12 25.5V`
- [ ] Confirmar que a volta para bateria acontece perto de `13 26.5V`

## Regras de operacao

- [ ] Evitar cargas continuas acima de `2500 W` na bateria
- [ ] Tratar `3000 W` como teto pratico da bateria
- [ ] Evitar combinar micro-ondas, air fryer, ferro e bomba na bateria
- [ ] Concentrar cargas pesadas durante o dia, com sol

## Ajustes rapidos se houver problema

- [ ] Se houver chaveamento excessivo, subir `12` para `25.5V`
- [ ] Se a bateria ficar alta por muito tempo, reduzir `26` para `28.2V`
- [ ] Se houver corte do BMS, reduzir cargas simultaneas e picos
- [ ] Se a rede estiver carregando sem querer, usar `16 OSO`

## Perfil alternativo (equilibrado)

- [ ] `12` -> `25.0V`
- [ ] `13` -> `26.5V`
- [ ] `29` -> `23.5V`

## Teste noturno de validacao

- [ ] Verificar status as `22h`: tensao e fonte ativa
- [ ] Verificar status as `02h`: tensao e fonte ativa
- [ ] Verificar status as `06h`: tensao e fonte ativa

## Referencias

- `manual-final-sumry-sp4200.md`
- `guia-rapido-sumry-sp4200.md`
- `configuracao-inversor-sumry-sp4200.md`
