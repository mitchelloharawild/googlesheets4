# googlesheets4 (development version)

### Write Sheets

These functions are ready for use but are still under development. You can expect refinements to their interface and capabilities:

  * `sheets_create()` is a new function to create a new Sheet and, optionally,
    write one or more data frames into it (#61).
  * `sheets_write()` (also available as `write_sheet()`) is a new function to
    write a data frame into a new or existing (work)sheet, inside a new or
    existing (spread)Sheet.
  * `sheets_append()` adds rows to the data in an existing sheet.

More Sheet-editing functionality is coming!

### Other new functions and arguments

There is a new family of `sheets_sheet_*()` functions that operate on the (work)sheets inside an existing (spread)Sheet:
  
  * `sheets_sheet_data()` returns a tibble of metadata with one row per sheet.
  * `sheets_sheet_names()` returns sheet names.
  * `sheets_sheet_add()` adds one or more sheets.
  * `sheets_sheet_delete()` deletes one or more sheets.

`sheets_cells()` gains two new arguments that make it possible to get more data on more cells. By default, we get only the fields needed to parse cells that contain values. But `sheets_cells(cell_data = "full", discard_empty = FALSE)` is now available if you want full cell data, including formatting, even for cells that have no value (#4).

### Renamed functions and classes

* `sheets_sheets()` is now `sheets_sheet_names()`, in order to fit into a coherent family of `sheets_sheet_*()` functions that deal with (work)sheets. `sheets_sheets()` still exists but will be removed rather quickly since googlesheets4 is so new.

* The S3 class `sheets_Spreadsheet` is renamed to `googlesheets4_spreadsheet`, a consequence of rationalizing all internal and external classes. `googlesheets4_spreadsheet` is the class that holds metadata for a Sheet and it is connected to the API's [`Spreadsheet`](https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets#resource:-spreadsheet) schema. The return value of `sheets_get()` has this class.

### Bug fixes

* `read_sheet()` passes its `na` argument down to the helpers that parse cells, so that `na` actually has the documented effect (#73).

# googlesheets4 0.1.0

* Added a `NEWS.md` file to track changes to the package.
