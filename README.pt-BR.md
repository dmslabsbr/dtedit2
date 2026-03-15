# DTedit2

**DataTables editáveis para apps Shiny** — criar, editar e excluir linhas em tabelas DT direto na interface R/Shiny.

Leia em inglês: [README.md](README.md)

---

[![Licença: LGPL](https://img.shields.io/badge/Licen%C3%A7a-LGPL-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0)
[![R](https://img.shields.io/badge/R-%3E%3D%203.3.2-276DC3?logo=R)](https://www.r-project.org/)
[![Versão](https://img.shields.io/badge/vers%C3%A3o-0.1.28-blue)](https://github.com/dmslabsbr/dtedit2)
[![Linhas de código](https://img.shields.io/tokei/lines/github/dmslabsbr/dtedit2)](https://github.com/dmslabsbr/dtedit2)
[![Último commit](https://img.shields.io/github/last-commit/dmslabsbr/dtedit2)](https://github.com/dmslabsbr/dtedit2)

---

## Créditos

Este projeto é um **fork** com extensões e correções.

| Papel | Autor | Repositório / Contato |
|-------|--------|------------------------|
| **Autor original** | Jason Bryer, Ph.D. | [jbryer/DTedit](https://github.com/jbryer/DTedit) — jason@bryer.org |
| **Base de código externa** | DavidPatShuiFong | [DavidPatShuiFong/DTedit](https://github.com/DavidPatShuiFong/DTedit) |
| **Mantenedor do fork** | dmslabsbr (Daniel) | [dmslabsbr/dtedit2](https://github.com/dmslabsbr/dtedit2) — suporte@neoage.com.br |

---

## Descrição

O **DTedit2** estende o [DT](https://rstudio.github.io/DT/) DataTable para que o usuário possa **adicionar**, **editar** e **excluir** linhas diretamente na tabela. Tipos de coluna (numérico, fator, data, etc.) são mapeados para os inputs Shiny adequados. Você conecta seus próprios callbacks para persistir os dados (por exemplo em banco de dados ou em memória).

---

## Instalação

No R:

```r
devtools::install_github('dmslabsbr/dtedit2')
```

Branch ou tag específica (ex.: tag):

```r
devtools::install_github('dmslabsbr/dtedit2', ref = 'v0.22f')
```

---

## Início rápido

Executar o app de demonstração:

```r
DTedit::dtedit_demo()
```

Modelo mínimo: [inst/template/app.R](inst/template/app.R).

---

## Uso em três passos

1. **Definir callbacks** de inserção, atualização e exclusão (ex.: atualizar um data frame ou banco).
2. **Criar o objeto `dtedit`** no `server` com `thedata`, `edit.cols`, `view.cols` e seus callbacks.
3. **Exibir na UI** com `uiOutput('nome_do_seu_dtedit')`.

Exemplo (trecho):

```r
DTedit::dtedit(input, output,
  name = 'mycontacts',
  thedata = mydata,
  edit.cols = c('name', 'email', 'useR', 'notes'),
  edit.label.cols = c('Name', 'Email Address', 'Are they an R user?', 'Additional notes'),
  view.cols = c('name', 'email', 'useR'),
  callback.update = my.update.callback,
  callback.insert = my.insert.callback,
  callback.delete = my.delete.callback)
```

Este fork adiciona opções como `view.label.cols`, `edit.require.cols`, `edit.require.label`, `date.format` e títulos/etiquetas customizáveis para adicionar/editar/excluir. Consulte `?dtedit` para a lista completa.

---

## Captura de tela

![Captura de tela do DTedit](inst/screens/dtedit_books_edit.png)

---

## Suporte

- [Buy me a pizza](https://www.buymeacoffee.com/dmslabs) · [PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=9S3JYKPHR3XQ6)

---

## Licença

LGPL. Consulte [DESCRIPTION](DESCRIPTION) e o repositório para detalhes.
