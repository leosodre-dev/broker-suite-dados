# Base de dados do Broker Suite

Este repositório guarda a base pública que o app **Broker Suite** baixa ao abrir.
Tudo fica no arquivo `base.json`. Só coloque aqui **informações públicas**
(alíquotas, índices, taxas). Nunca coloque dados de clientes.

## Como editar

1. Abra o arquivo `base.json` aqui no GitHub e clique no lápis (Edit).
2. Faça a alteração.
3. Atualize o campo `"atualizadoEm"` com a data de hoje (ex.: `"2026-11-05"`).
4. Clique em **Commit changes**.
5. Os apps recebem a mudança em até 12 horas (ou ao abrir, se a memória expirou).

**Atenção à formatação:** use **ponto** como separador decimal (`0.29`, não `0,29`),
mantenha as aspas e as vírgulas entre os itens. Se o arquivo ficar inválido,
os apps simplesmente continuam usando a última versão boa.

## Seções

### `ivar`
IVAR mensal (FGV), em % ao mês. Para lançar um mês novo, adicione uma linha:
`"2026-09": 0.35,`

### `itbi`
Uma regra por município. Campos:
- `municipio`, `uf`: igual ao nome do IBGE (ex.: `"Vitória da Conquista"`, `"BA"`)
- `aliquotaPadrao`: em % (ex.: `3.0`)
- `fonte`, `conferidoEm`: de onde veio a regra e quando foi conferida
- `preliminar`: `true` mostra o aviso "confirme com a prefeitura"
- `observacao`: texto opcional
- `sfh`: redução sobre a parte financiada (opcional): `aliquota`,
  `limiteFinanciado`, `limiteImovel`, `descricao`
- `opcoes`: alíquotas alternativas (imóvel popular etc.): `rotulo`, `aliquota`,
  `descricao`, `marcadaPorPadrao`

### `bancos`
Taxa anunciada, seguros e tarifa de referência por banco
(`caixa`, `bb`, `itau`, `santander`, `bradesco`):
- `taxa`: % ao ano (ex.: `11.19`), ou `null`
- `nominal`: `true` para taxa nominal, `false` para efetiva
- `mip`, `dfi`: % ao mês (ex.: `0.025`), ou `null`
- `tarifa`: R$ por mês (ex.: `25.00`), ou `null`

O que cada usuário cadastrar no próprio celular tem prioridade sobre esta base.
