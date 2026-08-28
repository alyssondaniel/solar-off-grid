# Diagnostico 5 min - SUMRY amanheceu zerada

## Objetivo

Roteiro rapido para quando a bateria amanhece muito baixa ou vazia, mesmo com expectativa de bypass para rede.

## Sintoma-alvo

- bateria amanheceu em tensao muito baixa
- inversor nao fez comutacao para rede no ponto esperado
- cargas essenciais desligaram na madrugada

## Passo 1 - confirmar status agora (1 min)

Verificar no display e anotar:

- tensao atual da bateria
- fonte ativa (bateria ou rede)
- alarmes ativos
- historico de falha (se disponivel)

## Passo 2 - validar parametros criticos (1 min)

Conferir no menu:

- programa 12 em 25.5V
- programa 13 em 26.5V
- programa 29 em 24.0V
- programa 16 em OSO (ou CSO, se contingencia)
- programa 03 em APL

Se qualquer valor estiver diferente, corrigir e salvar.

## Passo 3 - confirmar bypass possivel (1 min)

- rede AC presente e estavel
- disjuntor de entrada AC ligado
- sem alarme de entrada fora de faixa
- programa 03 em APL para maior tolerancia da rede

Se a rede nao estiver aceitando, resolver entrada AC antes de novo teste noturno.

## Passo 4 - reduzir risco imediato (1 min)

Para a noite seguinte:

- desligar cargas pesadas apos 19:00
- manter so essenciais na madrugada
- evitar duas cargas pesadas simultaneas

Se o consumo noturno estiver alto, usar 16 em CSO temporariamente.

## Passo 5 - teste noturno guiado (1 min)

Fazer 3 verificacoes:

- 22h: tensao e fonte ativa
- 02h: tensao e fonte ativa
- 06h: tensao e fonte ativa

Esperado no perfil anti-zero:

- comutacao para rede perto de 25.5V
- retorno para bateria perto de 26.5V
- sem chegar na faixa critica de 24.0V por muito tempo

## Se falhar novamente

- subir programa 12 para 25.5V (ultra conservador)
- manter programa 29 em 24.0V ou 24.5V
- manter 16 em CSO por 24h a 48h
- revisar cabos, bornes e queda de tensao noturna

## Referencias

- manual-final-sumry-sp4200.md
- checklist-configuracao-sumry-sp4200.md
- sumry-plano-contingencia.md
