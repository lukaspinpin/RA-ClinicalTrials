---
title: "Clinical Trials Using Response Adaptive Designs"
output: html_document
---

```{r setup, include=FALSE}
# Install reactable if not already installed
if (!requireNamespace("reactable", quietly = TRUE)) {
  install.packages("reactable")
}

library(reactable)

# Load the data
trials <- data.frame(
  `#` = c(1, 2, 3, 4, 5, 6, 7, 8),
  `Trial Name/ID` = c("ABT-089", "Adverse Karyotype Acute Myeloid Leukemia", "ADORE", 
                      "ARREST / NCT03880565", "ASTIN", "ATTACC / NCT04372589", 
                      "AWARD-5 / NCT00734474", "BATTLE / NCT00409968, etc."),
  `Status` = c("completed", "completed", "completed", "completed", "completed", "completed", 
               "completed", "completed"),
  `Phase` = c("II", "", "III", "II", "II", "II/III", "III", "II"),
  `General RA Method` = c("BRAR", "BRAR", "BRAR", "BRAR", "BRAR", "BRAR", "BRAR", ""),
  `Sample Size (final/planned)` = c("337", "34", "1100", "30/176", "966", "1200/3000", 
                                    "1202/1566", "255"),
  `Number of Arms` = c(7, 3, 2, 2, 16, 2, 9, 4),
  `Outcome` = c("Ordinal", "Binary", "Binary", "Survival", "Ordinal", 
                "Ordinal Categorical", "Ordinal", "Binary")
)

# Create the table with reactable
reactable(
  trials,
  columns = list(
    `#` = colDef(name = "No.", align = "center"),
    `Trial Name/ID` = colDef(name = "Trial Name/ID"),
    `Status` = colDef(name = "Status"),
    `Phase` = colDef(name = "Phase"),
    `General RA Method` = colDef(name = "RA Method"),
    `Sample Size (final/planned)` = colDef(name = "Sample Size"),
    `Number of Arms` = colDef(name = "No. of Arms"),
    `Outcome` = colDef(name = "Outcome")
  ),
  sortable = TRUE, # Enable sorting for all columns
  bordered = TRUE, # Add table borders
  highlight = TRUE, # Highlight rows on hover
  striped = TRUE, # Add alternating row colors
  pagination = TRUE, # Enable pagination
  defaultPageSize = 10, # Set default number of rows per page
  theme = reactableTheme(
    rowHighlightStyle = list(backgroundColor = "#f7f7f7"), # Highlight color
    borderColor = "#dcdcdc", # Table border color
    headerStyle = list(backgroundColor = "#f2f2f2", fontWeight = "bold") # Header style
  )
)
