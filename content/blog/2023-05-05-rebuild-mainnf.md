---
title: 'Rebuild Main.nf'
date: 2023-05-05T13:40:19Z
draft: false
meta_img: "images/image.png"
tags:
  - "one tag"
  - "another tag"
description: "Description for the page"
---

### Todos for Today

- Class
  - if there are any paper edits
- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Ade
  - Finish SRS implement:
     - Filter NC and Mock Samples
     - Update downstream processes for SRS NC MOCK
     - Implement the other ones
  - Taguchi optmization for richness?
  - Make these subworkflows as opposed to one long workflow?
  - Unit tests based on the example data
  - Positive Control Analysis
  - Examine How SRS changes result vs rarefying
  - Run a proper analysis to send to Ade
  - Mock Community Investigation
  - How does the other Ben's Analysis line up with mine/ampliseq?
    - filtering step for the abundance?
    - Filtering unknown taxa?
- gg-catalog
  - Generate a gene network 
    - how do you do this?
      - possibly this: https://bmcbioinformatics.biomedcentral.com/articles/10.1186/s12859-020-3371-7
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### Ade 

#### Downstream processes:

cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 4e0038876815fb717361918409a3ddec2fd627e
slurm sub: 21994911

```bash
Command exit status:
  1

Command output:
  (empty)

Command error:
  • `0` -> `0...52`
  • `0` -> `0...53`
  • `0` -> `0...54`
  • `0` -> `0...55`
  • `0` -> `0...56`
  Rows: 1741 Columns: 56
  ── Column specification ────────────────────────────────────────────────────────
  Delimiter: "\t"
  chr  (1): 7b9c8d4a1896d84d92ab4820edd025a6
  dbl (55): 36, 60, 395, 372, 277, 0...7, 536, 43, 38, 749, 519, 558, 1070, 22...
  
  ℹ Use `spec()` to retrieve the full column specification for this data.
  ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
  Error in `select()`:
  ! Can't subset columns that don't exist.
  ✖ Column `X.OTU.ID` doesn't exist.
  Backtrace:
       ▆
    1. ├─table %>% select(-c("X.OTU.ID"))
    2. ├─dplyr::select(., -c("X.OTU.ID"))
    3. └─dplyr:::select.data.frame(., -c("X.OTU.ID"))
    4.   ├─dplyr:::tidyselect_fix_call(...)
    5.   │ └─base::withCallingHandlers(...)
    6.   └─tidyselect::eval_select(expr(c(...)), .data)
    7.     └─tidyselect:::eval_select_impl(...)
    8.       ├─tidyselect:::with_subscript_errors(...)
    9.       │ ├─base::tryCatch(...)
   10.       │ │ └─base tryCatchList(expr, classes, parentenv, handlers)
   11.       │ │   └─base tryCatchOne(expr, names, parentenv, handlers[[1L]])
   12.       │ │     └─base doTryCatch(return(expr), name, parentenv, handler)
   13.       │ └─tidyselect:::with_entraced_errors(expr)
   14.       │   └─rlang::try_fetch(...)
   15.       │     └─base::withCallingHandlers(...)
   16.       └─tidyselect:::vars_select_eval(...)
   17.         └─tidyselect:::walk_data_tree(expr, data_mask, context_mask, error_call)
   18.           └─tidyselect:::eval_c(expr, data_mask, context_mask)
   19.             └─tidyselect:::reduce_sels(node, data_mask, context_mask, init = init)
   20.               └─tidyselect:::walk_data_tree(new, data_mask, context_mask)
   21.                 └─tidyselect:::eval_c(expr, data_mask, context_mask)
   22.                   └─tidyselect:::reduce_sels(node, data_mask, context_mask, init = init)
   23.                     └─tidyselect:::walk_data_tree(new, data_mask, context_mask)
   24.                       └─tidyselect:::as_indices_sel_impl(...)
   25.                         └─tidyselect:::as_indices_impl(x, vars, call = call, strict = strict)
   26.                           └─tidyselect:::chr_as_locations(x, vars, call = call)
   27.                             └─vctrs::vec_as_location(x, n = length(vars), names = vars)
   28.                               └─vctrs `<fn>`()
   29.                                 └─vctrs:::stop_subscript_oob(...)
   30.                                   └─vctrs:::stop_subscript(...)
   31.                                     └─rlang::abort(...)
  Execution halted

Work dir:
  /scratch/bjl34716/ade/cycle-4/work/62/e7d00602edff9cab379936cb6b09c1
```
```


cycle 4 rev: 8a2cfcaa78eb9c5d75a7ac2d5a2355c661125ae2
visualize ampliseq rev: 
slurm sub: 

```bash
```

