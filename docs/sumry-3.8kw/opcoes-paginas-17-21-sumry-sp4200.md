# Opcoes das paginas 17 a 21 do manual

## Observacao importante

As paginas 17 a 21 nao mostram 39 opcoes distintas.

Elas mostram programas que vao ate o numero `39`, mas as opcoes visiveis nesse trecho totalizam `29` itens:

- `00`
- `01`
- `02`
- `03`
- `04`
- `05`
- `06`
- `07`
- `08`
- `09`
- `11`
- `12`
- `13`
- `16`
- `18`
- `19`
- `20`
- `22`
- `23`
- `25`
- `26`
- `27`
- `29`
- `33`
- `34`
- `35`
- `36`
- `37`
- `39`

## Legenda de decisao

- `configurar`: ajustar manualmente para o seu sistema
- `manter default`: deixar no valor padrao do manual
- `ignorar`: nao precisa mexer para o seu caso

Observacao de degrau real no painel:

- os programas 12 e 13 aceitam ajuste em passos de `0.5V`
- por isso, usar `12 25.5V` e `13 26.5V` como perfil anti-zero

## Tabela completa

| Option | Funcao                                    | Codigo padrao visivel | Acao             | Valor recomendado     | Observacao                                                                 |
| ------ | ----------------------------------------- | --------------------- | ---------------- | --------------------- | -------------------------------------------------------------------------- |
| `00`   | Exit setting mode                         | `ESC`                 | `ignorar`        | `ESC`                 | Apenas sai do menu                                                         |
| `01`   | Output source priority                    | `SUB`                 | `configurar`     | `SBU`                 | Prioriza solar, depois bateria, depois rede                                |
| `02`   | Maximum charging current                  | `80A` default         | `configurar`     | `80A`                 | Bom limite total para seu conjunto                                         |
| `03`   | AC input voltage range                    | `APL` default         | `manter default` | `APL`                 | Melhor para rede com oscilacao                                             |
| `04`   | Power saving mode                         | `SdS` default         | `manter default` | `SdS`                 | Evita desligamento por carga baixa                                         |
| `05`   | Battery type                              | `AGn` default         | `configurar`     | `USE`                 | Necessario para ajustar tensoes manualmente                                |
| `06`   | Auto restart when overload occurs         | `Lrd` default         | `manter default` | `Lrd`                 | Pode ficar no padrao se nao houver preferencia contraria                   |
| `07`   | Auto restart when over temperature occurs | `ttd` default         | `manter default` | `ttd`                 | Pode ficar no padrao                                                       |
| `08`   | Output voltage                            | `230V` default        | `manter default` | `230V`                | Ja coincide com a recomendacao                                             |
| `09`   | Output frequency                          | `50` default          | `configurar`     | `60`                  | Adequar ao padrao local                                                    |
| `11`   | Maximum utility charging current          | `60A` default         | `ignorar`        | nao usar com `16 OSO` | So configurar se escolher `16 CSO`                                         |
| `12`   | Back to utility in SBU                    | `23.0V` default       | `configurar`     | `25.5V`               | Evita descarga profunda no uso noturno                                     |
| `13`   | Back to battery in SBU                    | `27.0V` default       | `configurar`     | `26.5V`               | Reduz chaveamento e retorno precoce                                        |
| `16`   | Charger source priority                   | `SNU` default         | `configurar`     | `OSO` ou `CSO`        | `OSO` para apenas solar; `CSO` para solar primeiro                         |
| `18`   | Alarm control                             | `bON` default         | `manter default` | `bON`                 | Mantem alertas ativos                                                      |
| `19`   | Auto return to default display screen     | `ESP` default         | `manter default` | `ESP`                 | Nao interfere negativamente                                                |
| `20`   | Backlight control                         | `LON` default         | `manter default` | `LON`                 | Apenas preferencia visual                                                  |
| `22`   | Beeps while primary source is interrupted | `AON` default         | `manter default` | `AON`                 | Mantem aviso sonoro de troca de fonte                                      |
| `23`   | Overload bypass                           | `bYd` default         | `manter default` | `bYd`                 | Dia a dia em bypass OFF; usar bypass ON so em contingencia de continuidade |
| `25`   | Record fault code                         | `FdS` default         | `manter default` | `FdS`                 | Pode ficar no padrao                                                       |
| `26`   | Bulk charging voltage                     | `28.2V` default       | `configurar`     | `28.4V`               | Ajuste fino para o seu banco LiFePO4                                       |
| `27`   | Floating charging voltage                 | `27.0V` default       | `manter default` | `27.0V`               | O padrao ja atende bem                                                     |
| `29`   | Low DC cut-off voltage                    | `21.0V` default       | `configurar`     | `24.0V`               | Protege melhor a bateria no perfil anti-zero                               |
| `33`   | Battery equalization                      | `EdS` default         | `manter default` | `EdS`                 | Equalizacao deve ficar desligada                                           |
| `34`   | Battery equalization voltage              | `29.2V` default       | `ignorar`        | nao usar              | Sem efeito pratico se `33` estiver em `EdS`                                |
| `35`   | Battery equalized time                    | `60` default          | `ignorar`        | nao usar              | Sem efeito pratico se `33` estiver em `EdS`                                |
| `36`   | Battery equalized timeout                 | `120` default         | `ignorar`        | nao usar              | Sem efeito pratico se `33` estiver em `EdS`                                |
| `37`   | Equalization interval                     | `30d` default         | `ignorar`        | nao usar              | Sem efeito pratico se `33` estiver em `EdS`                                |
| `39`   | Equalization activated immediately        | `AdS` default         | `ignorar`        | nao usar              | Nao deve ser usado em LiFePO4                                              |

## Resumo pratico

### Configurar

- `01` -> `SBU`
- `02` -> `80A`
- `05` -> `USE`
- `09` -> `60`
- `12` -> `25.5V`
- `13` -> `26.5V`
- `16` -> `OSO` ou `CSO`
- `26` -> `28.4V`
- `29` -> `24.0V`

### Manter default

- `03` -> `APL`
- `04` -> `SdS`
- `06` -> `Lrd`
- `07` -> `ttd`
- `08` -> `230V`
- `18` -> `bON`
- `19` -> `ESP`
- `20` -> `LON`
- `22` -> `AON`
- `23` -> `bYd`
- `25` -> `FdS`
- `27` -> `27.0V`
- `33` -> `EdS`

### Ignorar

- `00`
- `11` quando `16 OSO` estiver ativo
- `34`
- `35`
- `36`
- `37`
- `39`

## Observacao final

Se voce usar `16 CSO` em vez de `16 OSO`, o programa `11` deixa de ser `ignorar` e passa a ser `configurar` com o menor valor util, como `10A` ou `20A`.

Se a prioridade absoluta for continuidade da carga em evento critico, o bypass pode ser habilitado temporariamente; no dia a dia, manter bypass desativado para preservar previsibilidade da operacao.
