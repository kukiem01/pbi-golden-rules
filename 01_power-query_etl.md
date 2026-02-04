# 01) Power Query (ETL) - Structure, Naming, Loading

## Goal
- Maintainable, readable, performant transformations
- Clear lineage and predictable structure

## Important (PBIX reality)
- For tables loaded to the model:
  - Power Query query name == Model table name
- Therefore:
  - Use **technical naming** only for **non-loaded** queries
  - Use **user/model-facing naming** for **loaded** tables

## Query Groups (folders)
- **00_Raw_Source**
  - Raw connections / entry points
  - Minimal transforms
- **10_Staging**
  - Intermediate transforms (cleaning/shaping/joining)
  - Reusable logic referenced by final queries
- **20_Model**
  - Final analytical tables loaded into the model
- **30_Support_UI**
  - Disconnected/support tables (slicers, parameters, lists)
- **99_Documentation** (optional)
  - Documentation-only queries (DOC_*)

## Naming rules
### Non-loaded queries (Enable Load = OFF)
- `Raw_<Thing>` — external source entry
- `Stg_<Thing>_<Step>` — intermediate shaping
- `DOC_<NN>_<Topic>` — documentation

### Loaded model tables (Enable Load = ON)
- Title Case with spaces
- No technical prefixes (Raw_/Stg_) visible in the Fields pane

## Loading rules
- Enable Load = **OFF** for:
  - `Raw_*`
  - `Stg_*`
  - `DOC_*`
  - helper queries not intended as model tables
- Enable Load = **ON** only for:
  - final analytical tables (facts/dimensions)
  - required support tables used by slicers/parameters/visual logic

## External UI/support sources (e.g., Excel on SharePoint)
Recommended flow:
- `Raw_*` (00_Raw_Source, load off)  
  → Reference  
- `Stg_*` (10_Staging, load off) *(optional)*  
  → Reference  
- final table (30_Support_UI, load on if needed)

## Inline support tables (Table.FromRows / compressed payload)
- Put directly in 30_Support_UI if it is a standalone disconnected table
- Split `Stg_` + final only when:
  - inline payload is large, or
  - you want to separate raw inline data from transformations

## ETL step hygiene (always)
- Filter early (reduce rows/columns ASAP)
- Preserve query folding where possible (push transforms to source)
- Expensive steps late (sort, group, pivot, heavy merges)
- Prefer Reference over Duplicate for re-use
- Apply stable, explicit data types (avoid implicit type guessing)
