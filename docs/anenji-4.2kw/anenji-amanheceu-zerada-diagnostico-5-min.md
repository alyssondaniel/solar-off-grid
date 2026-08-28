# Diagnostico 5 min - ANENJI amanheceu zerada

## Objetivo

Roteiro rapido para quando a bateria amanhece muito baixa ou vazia, mesmo com expectativa de comutacao para rede.

## Sintoma-alvo

- bateria amanheceu em tensao muito baixa
- inversor nao comutou no ponto esperado
- cargas essenciais desligaram na madrugada

## Passo 1 - confirmar status agora (1 min)

Verificar no display e anotar:

- tensao atual da bateria
- fonte ativa (bateria ou rede)
- alarmes ativos
- falhas registradas (se houver)

## Passo 2 - validar parametros criticos (1 min)

Conferir no menu:

- programa 12 em 25.5V
- programa 13 em 26.5V
- programa 29 em 24.0V
- programa 16 em Only Solar (ou Solar and Utility, contingencia)
- programa 11 em 10A ou 20A quando usar contingencia

Se qualquer valor estiver diferente, corrigir e salvar.

## Passo 3 - confirmar rede disponivel (1 min)

- rede AC presente e estavel
- disjuntor AC de entrada ligado
- sem alarme de entrada AC fora de faixa

Se nao houver rede valida, a comutacao nao vai acontecer no horario noturno.

## Passo 4 - reduzir risco imediato (1 min)

Para a noite seguinte:

- desligar cargas pesadas apos 19:00
- manter so essenciais na madrugada
- evitar duas cargas pesadas simultaneas

Se precisar suporte temporario, usar 16 em Solar and Utility com 11 em 10A ou 20A.

## Passo 5 - teste noturno guiado (1 min)

Fazer 3 verificacoes:

- 22h: tensao e fonte ativa
- 02h: tensao e fonte ativa
- 06h: tensao e fonte ativa

Esperado no perfil anti-zero:

- comutacao para rede perto de 25.5V
- retorno para bateria perto de 26.5V
- sem permanecer em zona critica de 24.0V

## Se falhar novamente

- subir programa 12 para 25.5V
- manter programa 29 em 24.0V ou 24.5V
- manter 16 em Solar and Utility por 24h a 48h
- revisar cabos, bornes e queda de tensao

## Referencias

- anenji-manual-final-anj4000-24v.md
- anenji-checklist-configuracao-anj4000-24v.md
- anenji-plano-contingencia.md
