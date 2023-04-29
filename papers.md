---
title: "Papers"
summary: "About this page."
date: 2016-04-13
layout: default
---

Here I list all the publications (including peer-reviewed papers and preprints) with short introductions to them. 

## Published paper
library(bib2df)
library(stevemisc)
library(stringi)

# load a bib file to data frame
bib_df <- bib2df(file="purblications.bib")

# clean entries
bib_df$TITLE <- stri_replace_all_regex(bib_df$TITLE, "[\\{\\}]", "")
bib_df$JOURNAL <- stri_replace_all_regex(bib_df$JOURNAL, "[\\{\\}]", "")
bib_df$BOOKTITLE <- stri_replace_all_regex(bib_df$BOOKTITLE, "[\\{\\}]", "")

# convert a single row back to .bib entry
bib_entry <- paste0(capture.output(df2bib(bib_df[1,])), collapse="")
bib_entry

# print out the citation
stevemisc::print_refs(bib_entry,
                      csl = "apa.csl",
                      spit_out = TRUE,
                      delete_after = FALSE)