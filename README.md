# DTedit2

**Editable DataTables for Shiny apps** — create, edit, and delete rows in DT tables from your R/Shiny UI.

Read in Portuguese: [README.pt-BR.md](README.pt-BR.md)

---

[![License: LGPL](https://img.shields.io/badge/License-LGPL-blue.svg)](https://www.gnu.org/licenses/lgpl-3.0)
[![R](https://img.shields.io/badge/R-%3E%3D%203.3.2-276DC3?logo=R)](https://www.r-project.org/)
[![Version](https://img.shields.io/badge/version-0.1.28-blue)](https://github.com/dmslabsbr/dtedit2)
[![Lines of code](https://img.shields.io/tokei/lines/github/dmslabsbr/dtedit2)](https://github.com/dmslabsbr/dtedit2)
[![Last commit](https://img.shields.io/github/last-commit/dmslabsbr/dtedit2)](https://github.com/dmslabsbr/dtedit2)

---

## Credits

This project is a **fork** with extensions and fixes.

| Role | Author | Repository / Contact |
|------|--------|----------------------|
| **Original author** | Jason Bryer, Ph.D. | [jbryer/DTedit](https://github.com/jbryer/DTedit) — jason@bryer.org |
| **External code base** | DavidPatShuiFong | [DavidPatShuiFong/DTedit](https://github.com/DavidPatShuiFong/DTedit) |
| **Fork maintainer** | dmslabsbr (Daniel) | [dmslabsbr/dtedit2](https://github.com/dmslabsbr/dtedit2) — suporte@neoage.com.br |

---

## Description

**DTedit2** extends the [DT](https://rstudio.github.io/DT/) DataTable so users can **add**, **edit**, and **delete** rows directly in the table. Column types (numeric, factor, date, etc.) are mapped to appropriate Shiny inputs. You plug in your own callbacks to persist data (e.g. database or in-memory).

---

## Install

From R:

```r
devtools::install_github('dmslabsbr/dtedit2')
```

Specific branch (e.g. tag):

```r
devtools::install_github('dmslabsbr/dtedit2', ref = 'v0.22f')
```

---

## Quick start

Run the demo app:

```r
DTedit::dtedit_demo()
```

Minimal template: [inst/template/app.R](inst/template/app.R).

---

## Usage in three steps

1. **Define callbacks** for insert, update, and delete (e.g. updating a data frame or database).
2. **Create the `dtedit` object** in your `server` with `thedata`, `edit.cols`, `view.cols`, and your callbacks.
3. **Render in the UI** with `uiOutput('your_dtedit_name')`.

Example (excerpt):

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

This fork adds options such as `view.label.cols`, `edit.require.cols`, `edit.require.label`, `date.format`, and customizable titles/labels for add/edit/delete. See `?dtedit` for the full list.

---

## Screenshot

![DTedit screenshot](inst/screens/dtedit_books_edit.png)

---

## Support

- [Buy me a pizza](https://www.buymeacoffee.com/dmslabs) · [PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=9S3JYKPHR3XQ6)

---

## License

LGPL. See [DESCRIPTION](DESCRIPTION) and repository for details.
