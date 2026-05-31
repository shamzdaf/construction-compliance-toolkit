# Construction Compliance Toolkit

**A Python-based toolkit for highway construction coordination, compliance verification, and quality control.**

This repository is inspired by the **Construction Engineer** role at **Indiana Department of Transportation (INDOT) - Vincennes, IN**, where the focus is on:

- **Daily highway construction operations** (contractors, consultants, quantities).
- **Compliance verification** with INDOT standard specifications and FHWA requirements.
- **Pre-construction conferences**, change orders, and materials verification.
- **Quality control reviews** to ensure adherence to approved plans and safety standards.

---

##  **Purpose**

This toolkit aims to:  
✅ **Automate compliance checks** for design reviews, pay items, and documentation.  
✅ **Streamline pre-construction and change order workflows**.  
✅ **Verify materials and quantities** against INDOT/FHWA standards.  
✅ **Generate reports** for audits, safety, and quality control.

---

##  **Features**


| **Module**                | **Description**                                                                       | **Key Functions**                                           |
| ------------------------- | ------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| `compliance_verifier`     | Verifies construction activities against INDOT/FHWA standards and approved plans.     | `check_compliance()`, `validate_design()`                   |
| `change_order_manager`    | Manages change orders, including reviews, approvals, and documentation.               | `review_change_order()`, `update_contract()`                |
| `materials_verifier`      | Validates materials and quantities against project specifications.                    | `verify_materials()`, `check_quantities()`                  |
| `quality_control`         | Conducts quality control reviews and generates compliance reports.                    | `inspect_quality()`, `generate_qc_report()`                 |
| `documentation_generator` | Automates documentation for daily operations, pre-construction, and safety standards. | `generate_daily_report()`, `compile_precon_meeting_notes()` |


---

## 📂 **Repository Structure**

```
indot-construction-compliance-toolkit/
├── scripts/
│   ├── compliance_verifier.py      # Compliance verification tools
│   ├── change_order_manager.py     # Change order management
│   ├── materials_verifier.py        # Materials and quantities validation
│   ├── quality_control.py           # Quality control reviews
│   └── documentation_generator.py   # Automated documentation
├── README.md                       # Project documentation
└── LICENSE                          # MIT License
```

---

##  **Installation**

### **Prerequisites**

- Python 3.8+
- Required libraries: `pandas`, `numpy`, `openpyxl` (for Excel support)

### **Setup**

1. Clone the repository:
  ```bash
   git clone https://github.com/shamzdaf/construction-compliance-toolkit.git
   cd construction-compliance-toolkit
  ```
2. Install dependencies:
  ```bash
   pip install -r requirements.txt
  ```

---

##  **Quick Start**

### **1. Compliance Verification**

Verify construction activities against INDOT/FHWA standards:

```python
from scripts.compliance_verifier import ComplianceVerifier

verifier = ComplianceVerifier("data/project_specs.json")

# Check compliance for a specific pay item
compliance_status = verifier.check_compliance(
    pay_item="Asphalt Paving",
    quantity=1500,
    unit="tons"
)
print(f"Compliance status: {compliance_status}")

# Validate a design review
design_status = verifier.validate_design(
    design_plan="Highway_24_Widening.pdf",
    specifications="INDOT_2026"
)
print(f"Design validation: {design_status}")
```

### **2. Change Order Management**

Review and manage change orders:

```python
from scripts.change_order_manager import ChangeOrderManager

manager = ChangeOrderManager("data/change_orders.csv")

# Review a new change order
review_status = manager.review_change_order(
    order_id="CO-2026-001",
    description="Additional asphalt layer",
    cost_impact=50000
)
print(f"Change order review: {review_status}")

# Update contract with approved change order
manager.update_contract(
    contract_id="INDOT-2026-VIN-001",
    change_order_id="CO-2026-001"
)
```

### **3. Materials Verification**

Validate materials and quantities:

```python
from scripts.materials_verifier import MaterialsVerifier

verifier = MaterialsVerifier("data/materials_data.csv")

# Verify materials for a project
material_status = verifier.verify_materials(
    project_id="INDOT-2026-VIN-001",
    material="Steel Rebar",
    quantity=2000,
    unit="kg"
)
print(f"Material verification: {material_status}")

# Check quantities against approved plans
quantity_status = verifier.check_quantities(
    project_id="INDOT-2026-VIN-001",
    item="Concrete",
    approved_quantity=3000,
    actual_quantity=3200
)
print(f"Quantity check: {quantity_status}")
```

### **4. Quality Control**

Conduct QC reviews and generate reports:

```python
from scripts.quality_control import QualityControl

qc = QualityControl("data/quality_control_logs.json")

# Inspect quality for a specific activity
inspection_result = qc.inspect_quality(
    activity="Asphalt Compaction",
    parameters={"density": 95, "temperature": 160}
)
print(f"QC inspection result: {inspection_result}")

# Generate a QC report
report = qc.generate_qc_report(
    project_id="INDOT-2026-VIN-001",
    activity="Bridge Deck Pouring",
    findings=["Density within spec", "Temperature optimal"],
    recommendations=["Proceed with next phase"]
)
print(report)
```

### **5. Documentation Generator**

Automate daily reports and pre-construction documentation:

```python
from scripts.documentation_generator import DocumentationGenerator

generator = DocumentationGenerator()

# Generate a daily construction report
daily_report = generator.generate_daily_report(
    date="2026-05-31",
    contractors=["ABC Contractors", "XYZ Consultants"],
    activities=["Asphalt Paving", "Drainage Installation"],
    quantities={"Asphalt": 1500, "Drainage Pipes": 500},
    issues=["Minor delay due to weather"]
)
print(daily_report)

# Compile pre-construction meeting notes
precon_notes = generator.compile_precon_meeting_notes(
    project_id="INDOT-2026-VIN-001",
    attendees=["INDOT Rep", "Contractor A", "Consultant B"],
    agenda=["Project Overview", "Safety Protocols", "Timeline"],
    action_items=["Submit revised design by 2026-06-15"]
)
print(precon_notes)
```

---

##  **Example Data**

### `**data/project_specs.json**`

```json
{
  "INDOT_2026": {
    "standards": {
      "Asphalt Paving": {
        "min_density": 95,
        "max_temperature": 170,
        "unit": "tons"
      },
      "Concrete": {
        "min_strength": 3000,
        "unit": "psi"
      }
    },
    "safety": {
      "PPE_required": ["Hard Hat", "Safety Vest", "Steel-Toe Boots"],
      "inspection_frequency": "daily"
    }
  }
}
```

### `**data/change_orders.csv**`

```csv
order_id,project_id,description,cost_impact,status,date_submitted
CO-2026-001,INDOT-2026-VIN-001,Additional asphalt layer,50000,Approved,2026-05-01
CO-2026-002,INDOT-2026-VIN-002,Revised drainage design,25000,Pending,2026-05-15
```

### `**data/materials_data.csv**`

```csv
project_id,material,approved_quantity,unit,supplier
INDOT-2026-VIN-001,Steel Rebar,2000,kg,ABC Supplies
INDOT-2026-VIN-001,Concrete,3000,tons,XYZ Materials
```

---

##  **Use Cases**


| **Scenario**                       | **Tool**                     | **Output**                    |
| ---------------------------------- | ---------------------------- | ----------------------------- |
| Verify asphalt paving compliance   | `compliance_verifier.py`     | Compliance status (Boolean)   |
| Review a change order              | `change_order_manager.py`    | Approval status (JSON)        |
| Validate steel rebar quantities    | `materials_verifier.py`      | Verification result (Boolean) |
| Inspect asphalt compaction quality | `quality_control.py`         | QC report (Markdown)          |
| Generate daily construction report | `documentation_generator.py` | Daily report (Markdown/PDF)   |


---

##  **Customization**

### **Extend the Toolkit**

- **Add INDOT-specific standards**: Update `project_specs.json` with local requirements.
- **Integrate with INDOT systems**: Use APIs to fetch live project data.
- **Add GIS support**: Use `geopandas` to validate construction against geographic plans.
- **Automate FHWA reporting**: Generate FHWA-compliant reports in PDF/Excel.

### **Visualization (Optional)**

Add a **Streamlit dashboard** to visualize:

- Compliance status across projects.
- Change order trends.
- Materials usage vs. approved quantities.

Example:

```python
# Install Streamlit: pip install streamlit
import streamlit as st
import pandas as pd

st.title("INDOT Construction Dashboard")
df = pd.read_csv("data/change_orders.csv")
st.bar_chart(df, x="project_id", y="cost_impact", color="status")
```

---

##  **License**

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.
