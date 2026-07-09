# SGA BI Dashboards

This repository contains the Power BI reporting layer for the SGA project. It consumes the curated
data produced by [sga-api-pipeline](../sga-api-pipeline), which extracts, transforms, and loads data
from an external API into a PostgreSQL Data Warehouse.

The project is versioned using the **Power BI Project (.pbip)** format, so the report layout and the
semantic model (tables, relationships, DAX measures) are stored as text files (PBIR/TMDL) and can be
reviewed like regular code changes.

---

## Table of Contents

- [Architecture & Folder Structure](#architecture--folder-structure)
- [Data Source](#data-source)
- [Prerequisites](#prerequisites)
- [Working with the Project](#working-with-the-project)
- [License](#license)
- [Contact](#contact)

---

## Architecture & Folder Structure

```
sga-bi-dashboards/
├── SGA Analytics.pbip            # Entry point, opens both parts below in Power BI Desktop
├── SGA Analytics.Report/         # Report layout (visuals, pages, bookmarks) as JSON (PBIR)
└── SGA Analytics.SemanticModel/  # Tables, relationships, DAX measures as text (TMDL)
```

The `.pbix` binary is not versioned. Once a `.pbix` is converted and saved as a Power BI Project,
the `.pbip` folders above become the source of truth in this repository.

## Data Source

Data is read from the PostgreSQL Data Warehouse populated by `sga-api-pipeline`. This report does not
duplicate any extraction or transformation logic — business rules live in the pipeline; this repository
is only responsible for the semantic model (relationships, measures) and visualization layer.

## Prerequisites

- Power BI Desktop (latest version)
- The **"Power BI Project (.pbip) save option"** preview feature enabled
  (`File > Options and settings > Options > Preview features`)
- Access credentials to the PostgreSQL Data Warehouse (see `sga-api-pipeline` for connection details)

## Working with the Project

1. Open `SGA Analytics.pbip` in Power BI Desktop.
2. Power BI Desktop will build a local, gitignored cache (`.pbi/`) — this is expected and never committed.
3. Make changes to the report or the semantic model, then save (`Ctrl+S`).
4. Review the diff in the `.Report` and `.SemanticModel` folders like any other text change, then commit.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Contact

Antonio Fernandes
