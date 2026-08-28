# Passo a passo no painel - Sumry SP-4200

## Objetivo

Este roteiro foi feito para configurar o inversor diretamente no painel, seguindo a ordem dos programas e usando os codigos mostrados no display.

## Como entrar no menu

1. Ligue o inversor com a bateria conectada.
2. No painel, pressione e segure `ENTER` por cerca de 3 segundos.
3. O inversor entra no modo de configuracao.
4. Use `UP` e `DOWN` para navegar entre os programas.
5. Use `ENTER` para entrar no programa selecionado.
6. Use `UP` e `DOWN` para mudar o valor ou codigo.
7. Use `ENTER` para confirmar o valor.
8. Use `ESC` para sair do ajuste ou do menu.

## Sequencia recomendada de configuracao

### Programa 01

- Navegue ate `01`
- Pressione `ENTER`
- Selecione `SBU`
- Pressione `ENTER` para salvar

### Programa 02

- Navegue ate `02`
- Pressione `ENTER`
- Selecione `80A`
- Pressione `ENTER` para salvar

### Programa 03

- Navegue ate `03`
- Pressione `ENTER`
- Selecione `APL`
- Pressione `ENTER` para salvar

### Programa 05

- Navegue ate `05`
- Pressione `ENTER`
- Selecione `USE`
- Pressione `ENTER` para salvar

### Programa 08

- Navegue ate `08`
- Pressione `ENTER`
- Selecione `230V`
- Pressione `ENTER` para salvar

### Programa 09

- Navegue ate `09`
- Pressione `ENTER`
- Selecione `60`
- Pressione `ENTER` para salvar

### Programa 11

- Navegue ate `11`
- So altere se quiser limitar carga da rede
- Se for usar apoio leve da rede, comece em `10A` ou `20A`
- Pressione `ENTER` para salvar, se alterar

### Programa 12

- Navegue ate `12`
- Pressione `ENTER`
- Selecione `25.5V`
- Pressione `ENTER` para salvar

### Programa 13

- Navegue ate `13`
- Pressione `ENTER`
- Selecione `26.5V`
- Pressione `ENTER` para salvar

### Programa 16

- Navegue ate `16`
- Pressione `ENTER`
- Escolha uma destas opcoes:

`OSO`
Usar se quiser que apenas o solar carregue a bateria.

`CSO`
Usar se quiser solar primeiro e rede carregando a bateria somente quando nao houver solar.

- Pressione `ENTER` para salvar

### Programa 26

- Navegue ate `26`
- Pressione `ENTER`
- Ajuste para `28.4V`
- Pressione `ENTER` para salvar

### Programa 27

- Navegue ate `27`
- Pressione `ENTER`
- Ajuste para `27.0V`
- Pressione `ENTER` para salvar

### Programa 29

- Navegue ate `29`
- Pressione `ENTER`
- Ajuste para `24.0V`
- Pressione `ENTER` para salvar

### Programa 33

- Navegue ate `33`
- Pressione `ENTER`
- Selecione `EdS`
- Pressione `ENTER` para salvar

## Sequencia final resumida

- `01` -> `SBU`
- `02` -> `80A`
- `03` -> `APL`
- `05` -> `USE`
- `08` -> `230V`
- `09` -> `60`
- `11` -> opcional, `10A` ou `20A` se quiser limitar carga da rede
- `12` -> `25.5V`
- `13` -> `26.5V`
- `16` -> `OSO` ou `CSO`
- `26` -> `28.4V`
- `27` -> `27.0V`
- `29` -> `24.0V`
- `33` -> `EdS`

## Depois de configurar

1. Saia do menu com `ESC`.
2. Verifique se os parametros ficaram gravados.
3. Confirme que o solar esta carregando normalmente.
4. Confirme que a rede nao esta carregando a bateria sem necessidade.
5. Observe se a troca para rede acontece perto de `12 25.5V`.
6. Observe se a volta para bateria acontece perto de `13 26.5V`.

## Se algo sair do esperado

- Se a rede estiver carregando a bateria sem querer, volte ao `16` e selecione `OSO`.
- Se estiver chaveando muito entre rede e bateria, aumente o `12` para `25.5V`.
- Se a bateria ficar muito tempo em tensao alta, reduza o `26` para `28.2V`.
- Se houver corte do BMS, reduza cargas simultaneas e evite picos.

## Referencias

- `checklist-configuracao-sumry-sp4200.md`
- `guia-rapido-sumry-sp4200.md`
- `manual-final-sumry-sp4200.md`
