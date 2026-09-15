# Getting Started - Addis Alem Hospital SBFR ODK

## Welcome! 👋

This guide will help you get up and running with the Operational Digital Kit (ODK) for the Addis Alem Hospital SBFR Team.

---

## 📋 Prerequisites

- **Access**: GitHub account with repository access
- **Tools**: 
  - Git (for cloning repository)
  - Python 3.7+ (for data processing scripts)
  - Excel or LibreOffice (for spreadsheet templates)
  - Text editor (for JSON forms and documentation)

---

## 🔧 Step 1: Repository Setup

### Clone the Repository
```bash
git clone https://github.com/alebetadie-hue/addis-alem-hospital-sbfr-odk.git
cd addis-alem-hospital-sbfr-odk
```

### Install Python Dependencies (Optional)
```bash
pip install -r requirements.txt
```

---

## 📂 Step 2: Explore the Structure

### Key Directories:

1. **`/workflows/`** - Team processes and procedures
   - Daily operations
   - Data collection workflow
   - Reporting processes
   - Staff onboarding

2. **`/data-collection/`** - Forms and data schemas
   - Pre-built forms (JSON format)
   - Data schemas for validation
   - Excel/CSV templates

3. **`/implementation/`** - Setup and tools
   - Installation guides
   - User manuals
   - Python scripts for automation
   - Excel-based validation tools

4. **`/training/`** - Learning materials
   - Quick reference guides
   - FAQ documentation
   - Troubleshooting tips

5. **`/quality-assurance/`** - QA and compliance
   - Checklists and audits
   - Compliance guidelines

---

## 📊 Step 3: Access Data Collection Forms

### Finding Forms
All data collection forms are located in `/data-collection/forms/`

Available forms:
- `patient_intake_form.json` - For patient registration
- `service_delivery_form.json` - For service tracking
- `financial_tracking_form.json` - For financial data

### Using Forms
1. Open the JSON form file
2. Review the fields and requirements
3. Use the corresponding Excel template for data entry
4. Run validation scripts to check data quality

---

## 🔄 Step 4: Follow Team Workflows

### Daily Operations Workflow
1. Review `/workflows/daily_operations.md` for daily checklist
2. Access data collection forms
3. Enter data using provided templates
4. Run validation checks
5. Submit to supervisor for review

### Data Collection Workflow
Refer to `/workflows/data_collection_workflow.md` for:
- Step-by-step data collection procedures
- Quality assurance checks
- Error handling and escalation

---

## 📈 Step 5: Run Implementation Tools

### Data Validation
```bash
python implementation/scripts/data_validation.py --file your_data.csv
```

### Generate Reports
```bash
python implementation/scripts/generate_reports.py --month 2026-09 --output reports/
```

### Import Data
```bash
python implementation/scripts/data_import.py --source external_data.xlsx --format xlsx
```

---

## 📖 Step 6: Access Training Materials

### Quick Reference
- **Quick Reference Guide**: `/training/quick_reference_guides.md`
- **FAQ**: `/training/faq.md`
- **Troubleshooting**: `/training/troubleshooting_tips.md`

### Video Guides
Placeholder for video tutorials in `/training/video_guides/`
- Getting Started Video
- Data Entry Tutorial
- Report Generation Guide
- Troubleshooting Video

---

## ✅ Step 7: Quality Assurance Checklist

Before submitting any data:
1. Review `/quality-assurance/checklist.md`
2. Verify all required fields are complete
3. Check data against validation rules
4. Ensure compliance with guidelines
5. Sign off on audit log

---

## 🆘 Troubleshooting

### Common Issues:

**Issue**: Can't access forms
- **Solution**: Check `/data-collection/forms/` directory and ensure file permissions

**Issue**: Python scripts not running
- **Solution**: Install dependencies: `pip install -r requirements.txt`

**Issue**: Data validation errors
- **Solution**: Review `/training/troubleshooting_tips.md` or check data dictionary at `/docs/data_dictionary.md`

For more help, visit `/training/faq.md` or contact the SBFR team lead.

---

## 📞 Getting Help

- **Documentation**: Read relevant markdown files in each directory
- **Issues**: Create a GitHub issue if you encounter problems
- **Team**: Contact your SBFR team supervisor
- **Updates**: Check the repository regularly for new resources

---

## 🎓 Training Path (Recommended Order)

1. **Week 1**: 
   - Read this Getting Started guide
   - Review daily operations workflow
   - Explore data collection forms

2. **Week 2**:
   - Complete training materials in `/training/`
   - Practice with sample data
   - Run validation scripts

3. **Week 3**:
   - Execute full data collection workflow
   - Generate sample reports
   - Complete QA checklist

4. **Week 4+**:
   - Full operational use
   - Continuous improvement and feedback

---

## 🚀 Quick Links

| Resource | Location |
|----------|----------|
| Daily Workflow | `/workflows/daily_operations.md` |
| Data Forms | `/data-collection/forms/` |
| Setup Guide | `/implementation/setup_guide.md` |
| User Manual | `/implementation/user_manual.md` |
| FAQ | `/training/faq.md` |
| QA Checklist | `/quality-assurance/checklist.md` |
| Data Dictionary | `/docs/data_dictionary.md` |

---

## 📞 Support Contact

**SBFR Team Lead**: [Insert contact information]
**Repository Admin**: alebetadie-hue

---

**Ready to get started?** Begin with the Daily Operations Workflow (`/workflows/daily_operations.md`)!

---

**Last Updated**: September 15, 2026
