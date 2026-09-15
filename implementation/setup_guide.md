# Addis Alem Hospital SBFR ODK - Setup Guide

## Complete Installation and Configuration Instructions

---

## 1. System Requirements

### Minimum Hardware Requirements
- **CPU**: 2.0 GHz dual-core processor or better
- **RAM**: 4 GB minimum (8 GB recommended)
- **Storage**: 50 GB free space minimum
- **Network**: Stable internet connection (minimum 2 Mbps)

### Software Requirements
- **Operating System**: Windows 10+, macOS 10.14+, or Ubuntu 18.04+
- **Python**: 3.7 or higher
- **Git**: Latest version
- **Database**: SQLite3 (included) or PostgreSQL 12+
- **Browser**: Chrome, Firefox, Safari, or Edge (latest version)

---

## 2. Repository Setup

### Step 1: Clone Repository

```bash
# Open terminal/command prompt
cd [preferred-location]

# Clone the ODK repository
git clone https://github.com/alebetadie-hue/addis-alem-hospital-sbfr-odk.git

# Navigate to repository
cd addis-alem-hospital-sbfr-odk
```

### Step 2: Verify Repository Structure

```bash
# List directory structure
tree -L 2
# or on Windows: dir /s
```

Expected output:
```
addis-alem-hospital-sbfr-odk/
├── README.md
├── GETTING_STARTED.md
├── QR_CODE.md
├── workflows/
├── data-collection/
├── implementation/
├── training/
├── quality-assurance/
├── docs/
└── ...
```

---

## 3. Python Environment Setup

### Step 1: Install Python

**On Windows**:
1. Download Python 3.9+ from https://www.python.org/downloads/
2. Run installer
3. Check "Add Python to PATH"
4. Click "Install Now"

**On macOS**:
```bash
# Using Homebrew
brew install python3
```

**On Linux (Ubuntu/Debian)**:
```bash
sudo apt-get update
sudo apt-get install python3 python3-pip
```

### Step 2: Create Virtual Environment

```bash
# Navigate to repository
cd addis-alem-hospital-sbfr-odk

# Create virtual environment
python3 -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
# Upgrade pip
pip install --upgrade pip

# Install required packages
pip install -r requirements.txt
```

**If requirements.txt doesn't exist, create it**:

```bash
# Create requirements.txt
cat > requirements.txt << EOF
pandas==1.3.0
openpyxl==3.0.7
jsonschema==3.2.0
click==8.0.1
tabulate==0.8.9
EOF

# Install
pip install -r requirements.txt
```

---

## 4. Database Setup

### Using SQLite (Default)

```bash
# Create database directory
mkdir -p data/database

# Create SQLite database
sqlite3 data/database/sbfr.db

# At the SQLite prompt, create basic tables
# (Can also use provided SQL script)
.exit
```

### Using PostgreSQL (Optional)

```bash
# Install PostgreSQL (if not already installed)
# Windows: Download from https://www.postgresql.org/download/windows/
# macOS: brew install postgresql
# Linux: sudo apt-get install postgresql postgresql-contrib

# Create database
createdb sbfr_database

# Create user (if needed)
psql -c "CREATE USER sbfr_user WITH PASSWORD 'secure_password';"
psql -c "GRANT ALL PRIVILEGES ON DATABASE sbfr_database TO sbfr_user;"
```

---

## 5. Configuration Files

### Create Configuration File

```bash
# Create config directory
mkdir -p config

# Create config file
cat > config/settings.py << EOF
# Database Configuration
DATABASE_TYPE = 'sqlite'  # or 'postgresql'
DATABASE_PATH = 'data/database/sbfr.db'

# For PostgreSQL:
# DATABASE_HOST = 'localhost'
# DATABASE_PORT = 5432
# DATABASE_NAME = 'sbfr_database'
# DATABASE_USER = 'sbfr_user'
# DATABASE_PASSWORD = 'secure_password'

# Data Directories
DATA_INPUT_DIR = 'data/input/'
DATA_OUTPUT_DIR = 'data/output/'
ARCHIVE_DIR = 'data/archive/'

# Validation Settings
STRICT_VALIDATION = True
ALLOW_CORRECTIONS = True

# Logging
LOG_LEVEL = 'INFO'
LOG_FILE = 'logs/sbfr.log'
EOF
```

### Create Data Directories

```bash
# Create necessary directories
mkdir -p data/input
mkdir -p data/output
mkdir -p data/archive
mkdir -p data/backups
mkdir -p logs
```

---

## 6. Test Installation

### Run Validation Test

```bash
# Test Python installation
python --version

# Test required packages
python -c "import pandas; import openpyxl; import jsonschema; print('All packages installed successfully!')"

# Test validation script
python implementation/scripts/data_validation.py --help
```

### Expected Output

```
Usage: data_validation.py [OPTIONS]

Options:
  --file FILE              Path to data file for validation
  --directory DIR          Path to directory with multiple files
  --schema FILE            Path to JSON schema file
  --report FILE            Output report file path
  --help                   Show this message and exit.
```

---

## 7. User Access Setup

### Create User Accounts (Optional)

```bash
# Create users file
cat > config/users.csv << EOF
username,password_hash,role,department,status
col_001,hash_value_here,data_collector,SBFR,active
col_002,hash_value_here,data_collector,SBFR,active
supervisor_001,hash_value_here,supervisor,SBFR,active
manager_001,hash_value_here,manager,SBFR,active
EOF
```

---

## 8. File Permissions

### Set Appropriate Permissions

```bash
# On Linux/macOS
chmod 755 implementation/scripts/*.py
chmod 755 data/
chmod 755 config/

# Restrict sensitive files
chmod 600 config/settings.py
chmod 600 config/users.csv
```

---

## 9. Backup Setup

### Create Backup Script

```bash
# Create backup script
cat > backup.sh << 'EOF'
#!/bin/bash
BACKUP_DIR="data/backups"
DATE=$(date +"%Y%m%d_%H%M%S")
tar -czf $BACKUP_DIR/backup_$DATE.tar.gz data/ config/
echo "Backup created: $BACKUP_DIR/backup_$DATE.tar.gz"
EOF

# Make script executable
chmod +x backup.sh

# Test backup
./backup.sh
```

---

## 10. Final Verification

### Complete Setup Checklist

- [ ] Repository cloned successfully
- [ ] Python 3.7+ installed
- [ ] Virtual environment created and activated
- [ ] Dependencies installed (requirements.txt)
- [ ] Database created and configured
- [ ] Configuration files created
- [ ] Data directories created
- [ ] Scripts are executable
- [ ] Test validation runs successfully
- [ ] Backup system functional

---

## 11. Troubleshooting

### Common Issues

**Issue**: Python not found
- **Solution**: Add Python to PATH or use full path to python executable

**Issue**: Module not found error
- **Solution**: Ensure virtual environment is activated and requirements installed

**Issue**: Permission denied on scripts
- **Solution**: Run `chmod +x implementation/scripts/*.py` on Linux/macOS

**Issue**: Database connection error
- **Solution**: Verify database is running and connection settings are correct

---

## 12. Next Steps

1. Review `GETTING_STARTED.md` for quick start guide
2. Read `workflows/daily_operations.md` for daily procedures
3. Review `data-collection/forms/` for available forms
4. Run training session with team members
5. Begin data collection with test data
6. Monitor logs in `logs/sbfr.log`

---

**Setup Completed**: Your ODK is ready for use!

**Last Updated**: September 15, 2026
