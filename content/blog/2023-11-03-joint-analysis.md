---
title: 'Joint Analysis'
date: 2023-11-03T13:28:17Z
draft: false
meta_img: "images/image.png"
tags:
  - "regmi-rfid"
description: "Description for the page"
---

### RFID

The ESSD was causing problems again so I pulled updates to the internal hdd, and re-run the driver script so that I have my intermediates and figures. 

rev:  01867f9973f8e6df6abfaa792d55b9c586273ee5 
 
```bash
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (2): from_zone, to_zone
dbl (3): t1, t2, tagname

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 2314 Columns: 5
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (2): from_zone, to_zone
dbl (3): t1, t2, tagname

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 4878 Columns: 5
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (2): from_zone, to_zone
dbl (3): t1, t2, tagname

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 4356 Columns: 5
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (2): from_zone, to_zone
dbl (3): t1, t2, tagname

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Rows: 1608 Columns: 5
── Column specification ────────────────────────────────────────────────────────
Delimiter: ","
chr (2): from_zone, to_zone
dbl (3): t1, t2, tagname

ℹ Use `spec()` to retrieve the full column specification for this data.
ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
Error: Can't subset columns that don't exist.
✖ Column `tagname` doesn't exist.
Backtrace:
     █
  1. ├─tidyr::nest(rm_11_overall_df, data = -tagname)
  2. └─tidyr:::nest.tbl_df(rm_11_overall_df, data = -tagname)
  3.   └─purrr::map(cols, ~names(tidyselect::eval_select(.x, .data)))
  4.     └─tidyr:::.f(.x[[i]], ...)
  5.       └─tidyselect::eval_select(.x, .data)
  6.         └─tidyselect:::eval_select_impl(...)
  7.           ├─tidyselect:::with_subscript_errors(...)
  8.           │ ├─base::tryCatch(...)
  9.           │ │ └─base:::tryCatchList(expr, classes, parentenv, handlers)
 10.           │ │   └─base:::tryCatchOne(expr, names, parentenv, handlers[[1L]])
 11.           │ │     └─base:::doTryCatch(return(expr), name, parentenv, handler)
 12.           │ └─tidyselect:::instrument_base_errors(expr)
 13.           │   └─base::withCallingHandlers(...)
 14.           └─tidyselect:::vars_select_eval(...)
 15.             └─tidyselect:::walk_data_tree(expr, data_mask, context_mask)
 16.               └─tidyselect:::eval_minus(expr, data_mask, context_mask)
 17.                 └─tidyselect:::eval_bang(expr, data_mask, context_mask)
 18.                   └─tidyselect:::walk_data_tree(expr[[2]], data_mask, context_mask)
 19.                     └─tidyselect:::as_indices_sel_impl(...)
 20.                       └─tidyselect:::as_indices_impl(x, vars, strict = strict)
 21.                         └─tidyselect:::chr_as_locations(x, vars)
 22.                           └─vctrs::vec_as_location(x, n = length(vars), names = vars)
 23.                             └─(function () ...
 24.                               └─vctrs:::stop_subscript_oob(...)
 25.                                 └─vctrs:::stop_subscript(...)
 ```
 
```bash
Error: Can't subset columns that don't exist.
✖ Column `tagname` doesn't exist.
Backtrace:
     █
  1. ├─tidyr::nest(rm_2_overall_df, data = -tagname)
  2. └─tidyr:::nest.tbl_df(rm_2_overall_df, data = -tagname)
  3.   └─purrr::map(cols, ~names(tidyselect::eval_select(.x, .data)))
  4.     └─tidyr:::.f(.x[[i]], ...)
  5.       └─tidyselect::eval_select(.x, .data)
  6.         └─tidyselect:::eval_select_impl(...)
  7.           ├─tidyselect:::with_subscript_errors(...)
  8.           │ ├─base::tryCatch(...)
  9.           │ │ └─base:::tryCatchList(expr, classes, parentenv, handlers)
 10.           │ │   └─base:::tryCatchOne(expr, names, parentenv, handlers[[1L]])
 11.           │ │     └─base:::doTryCatch(return(expr), name, parentenv, handler)
 12.           │ └─tidyselect:::instrument_base_errors(expr)
 13.           │   └─base::withCallingHandlers(...)
 14.           └─tidyselect:::vars_select_eval(...)
 15.             └─tidyselect:::walk_data_tree(expr, data_mask, context_mask)
 16.               └─tidyselect:::eval_minus(expr, data_mask, context_mask)
 17.                 └─tidyselect:::eval_bang(expr, data_mask, context_mask)
 18.                   └─tidyselect:::walk_data_tree(expr[[2]], data_mask, context_mask)
 19.                     └─tidyselect:::as_indices_sel_impl(...)
 20.                       └─tidyselect:::as_indices_impl(x, vars, strict = strict)
 21.                         └─tidyselect:::chr_as_locations(x, vars)
 22.                           └─vctrs::vec_as_location(x, n = length(vars), names = vars)
 23.                             └─(function () ...
 24.                               └─vctrs:::stop_subscript_oob(...)
 25.                                 └─vctrs:::stop_subscript(...)
Execution halted
Script finished

```

Why aren't intermediates written to disk?

code is acting wierd so we reverted to commit cd10867d594c9fc0daa991ec291954ecdd067bae

```bash
it passes
```

If that works without a hitch then we can update cutoffs and if it still works then merge to main

rev: dafa30f236f13deba6f0a95c2f6f5d8ff71fc75e

```bash
driver.sh OK
test.sh OK
```

The only thing is a weird artificat if there is a 1 for the first day, I changed line 200 to be 0,1,2,3 as opposed to 0,1,2,3

I was able to fix the code up and have started the analysis to compare high and low activity nesting zones which we can pick up on Monday
