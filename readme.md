Here’s the **updated `README.md`** with your specific **Known Issue** about **tabs and placing cards** during import 👇

---

````markdown
# 🧰 Metabase Export & Import Utility

A Python-based utility for exporting and importing configuration data from a community edition instance of [Metabase](https://www.metabase.com).  
This tool allows you to back up and restore key Metabase assets, including **fields**, **cards**, and **dashboards** — ideal for environment migrations or instance replication.

---

## 🚀 Features

- 📤 Export fields, cards, and dashboards from an existing Metabase instance.  
- 📥 Import configurations into a new or existing Metabase deployment.  
- 🗂️ Supports multiple databases and environments.  
- 🧱 Simple CLI commands for quick backup and restore.  

---

## 📦 Requirements

- Python 3.8+
- `requests` library  
  Install dependencies with:
  ```bash
  pip install -r requirements.txt
````

*(or manually install `requests` if no requirements file is present)*

---

## 🛠️ Usage

### 1. Export Metabase Data

```bash
python3 metabase_export.py http://localhost:3000/api/ <username> <password> <database_name> <export_folder>
```

This command will generate three files for each element, using the database name as a prefix:

* `<database_name>_fields_exported.csv`
* `<database_name>_cards_exported.json`
* `<database_name>_dashboard_exported.json`

✅ **Tip:** Make sure the user has admin or read access to the required resources.

---

### 2. Import Metabase Data

```bash
python3 metabase_import.py http://localhost:3000/api/ <username> <password> <database_name> <import_folder>
```

This will import fields, cards, and dashboards into the target Metabase instance from the exported files.

---

## 📝 File Naming Convention

| Element    | Exported File Name                        | Import File Name                           |
| ---------- | ----------------------------------------- | ------------------------------------------ |
| Fields     | `<database_name>_fields_exported.csv`     | `<database_name>_fields_forimport.csv`     |
| Cards      | `<database_name>_cards_exported.json`     | `<database_name>_cards_forimport.json`     |
| Dashboards | `<database_name>_dashboard_exported.json` | `<database_name>_dashboard_forimport.json` |

> Before importing, ensure the file names match the expected import format.

---

## 🧭 Notes & Tips

* Ensure the target Metabase instance has the same database schema as the source.
* If dashboards belong to collections, make sure collections exist in the target instance before importing.
* Metrics are deprecated in newer Metabase versions — you can safely skip metrics import if not applicable.
* If `collection_id` is `null`, remove the field or set it to a valid collection to avoid 400 errors during import.

---

## 🧪 Example

Export from source:

```bash
python3 metabase_export.py https://source-metabase.com/api/ admin@example.com Secret123 mydb export
```

Import into target:

```bash
python3 metabase_import.py http://192.168.2.106:3000/api/ user@example.com Secret123 mydb export
```

---

## ⚠️ Known Issues

* 🧭 **Tabs Handling:**
  Creating dashboard tabs and placing their respective cards in the correct tab is **not yet supported**.
  All cards are placed under the main dashboard section during import. If your dashboards use tabs extensively, you may need to **manually recreate tabs** after import.

---

## 🤝 Contributing

Pull requests are welcome!
If you find bugs or want to suggest improvements, please [open an issue](../../issues).

---

## 💡 Acknowledgements

* [Metabase](https://www.metabase.com) — Open-source analytics platform.
* Community contributors who helped improve the API export/import workflow.

```

