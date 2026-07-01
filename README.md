# openmrs-350-patients-dataset



```bash
sudo docker compose up -d
```

**What this does:** Starts all the services including databases and web interfaces.

**✅ Success indicator:** You'll see messages saying services are ready. The process is complete when you stop seeing new log messages.

---

## What's Now Available?

After running the setup, you'll have access to:

- **CloudBeaver** (Database viewer): http://localhost:8979
- **MySQL Database**: Contains OpenMRS DB with the 350 openmrs dataset of patient data

---

### Viewing the 350 patient dataset with CloudBeaver

CloudBeaver is a web-based tool that lets you explore your databases without needing to install additional software.

#### First Time Setup (Only do this once)

1. **Open CloudBeaver**: Go to http://localhost:8978 in your web browser

2. **Create Your Admin Account** (First time only):
    - You'll see a Setup Wizard
    - Choose any username (suggestion: `admin_user`)
    - Choose any password (suggestion: `Admin@123` - remember this!)
    - Click through to complete the setup
    - Log in with these credentials

#### Connect to Your Database
**Connect to MySQL database:**

1. Click **"New Connection"** again
2. Select **"MySQL"** from the list
3. Fill in these exact details:
    - **Host**: `synthetic-data`
    - **Port**: `3306`
    - **Database**: *(leave empty)*
    - **Username**: `root`
    - **Password**: `openmrs`
4. Click **"Create"**

**Important:** Once connected, you'll see openmrs schema

---
