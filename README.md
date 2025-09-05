# Topic 5: Capstone - Journal API

Welcome to your Python capstone project! You'll be working with a **FastAPI + PostgreSQL** application that helps people track their daily learning journey. This will prepare you for deploying to the cloud in the next phase.

By the end of this capstone, your API should be working locally and ready for cloud deployment.

## Table of Contents

- [🚀 Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [1. Fork and Clone the Repository](#1-fork-and-clone-the-repository)
  - [2. Configure Your Environment (.env)](#2-configure-your-environment-env)
  - [3. Set Up Your Development Environment](#3-set-up-your-development-environment)
  - [4. Verify the PostgreSQL Database Is Running](#4-verify-the-postgresql-database-is-running)
  - [5. Run the API](#5-run-the-api)
  - [6. Test Everything Works! 🎉](#6-test-everything-works-)
- [�️ Explore Your Database (Optional)](#️-explore-your-database-optional)
  - [1. Install PostgreSQL Extension](#1-install-postgresql-extension)
  - [2. Connect to Your Database](#2-connect-to-your-database)
  - [3. Explore Your Data](#3-explore-your-data)
- [Project Structure](#project-structure)
- [Your Learning Goals](#your-learning-goals)
- [🎯 Development Tasks (Your Work!)](#-development-tasks-your-work)
  - [1. API Implementation (Required)](#1-api-implementation-required)
  - [2. Logging Setup (Required)](#2-logging-setup-required)
  - [3. Data Model Improvements (Optional)](#3-data-model-improvements-optional)
  - [4. Cloud CLI Setup (Required for Deployment)](#4-cloud-cli-setup-required-for-deployment)
- [📊 Data Schema](#-data-schema)
- [🔌 API Endpoints](#-api-endpoints)
- [✅ How to Complete This Project](#-how-to-complete-this-project)
- [🔧 Troubleshooting](#-troubleshooting)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

## 🚀 Getting Started

### Prerequisites

- Git installed on your machine
- Docker Desktop installed and running
- VS Code with the Dev Containers extension

### 1. Fork and Clone the Repository

1. **Fork this repository** to your GitHub account by clicking the "Fork" button
1. **Clone your fork** to your local machine:

   ```bash
   git clone https://github.com/YOUR_USERNAME/journal-starter.git
   ```

1. Move into the project directory:

   ```bash
   cd journal-starter
   ```

1. **Open in VS Code**:

   ```bash
   code .
   ```

### 2. Configure Your Environment (.env)

Environment variables live in a `.env` file (which is **git-ignored** so you don't accidentally commit secrets). This repo ships with a template named `.env-sample`.

1. Copy the sample file to create your real `.env`:

   ```bash
   cp .env-sample .env
   ```

### 3. Set Up Your Development Environment

1. **Install the Dev Containers extension** in VS Code (if not already installed)
2. **Reopen in container**: When VS Code detects the `.devcontainer` folder, click "Reopen in Container"
   - Or use Command Palette (`Cmd/Ctrl + Shift + P`): `Dev Containers: Reopen in Container`
3. **Wait for setup**: The API container will automatically install Python, dependencies, and configure your environment.
   The PostgreSQL Database container will also automatically be created.

### 4. Verify the PostgreSQL Database Is Running

In a terminal outside of VS Code, run:

```bash
   docker ps
```

You should see the postgres service running.

### 5. Run the API

Make sure you are in the root of your project in the terminal:

```bash
   ./start.sh
```

### 6. Test Everything Works! 🎉

1. **Visit the API docs**: http://localhost:8000/docs
1. **Create your first entry** In the Docs UI Use the POST `/entries` endpoint to create a new journal entry.
1. **View your entries** using the GET `/entries` endpoint to see what you've created!

**🎯 Once you can create and see entries, you're ready to start implementing the missing endpoints!**

## 🗄️ Explore Your Database (Optional)

Want to see your data directly in the database? You can connect to PostgreSQL using VS Code's PostgreSQL extension:

### 1. Install PostgreSQL Extension

1. **Install the PostgreSQL extension** in VS Code (search for "PostgreSQL" by Chris Kolkman)
2. **Restart VS Code** after installation

### 2. Connect to Your Database

1. **Open the PostgreSQL extension** (click the PostgreSQL icon in the sidebar)
2. **Click "Add Connection"** or the "+" button
3. **Enter these connection details**:
   - **Host name**: `postgres`
   - **User name**: `postgres`
   - **Password**: `postgres`
   - **Port**: `5432`
   - **Conection Type**: `Standard/No SSL`
   - **Database**: `career_journal`
   - **Display name**: `Journal Starter DB` (or any name you prefer)

### 3. Explore Your Data

1. **Expand your connection** in the PostgreSQL panel
2. **Left-click on "Journal Starter DB" to expand**
3. **Right-click on "career_journal"**
4. **Select "New Query"**
5. **Type this query** to see all your entries:

   ```sql
   SELECT * FROM entries;
   ```

6. **Run the query** to see all your journal data! (Ctrl/Cmd + Enter OR use the PostgreSQL command pallete: Run Query)

You can now explore the database structure, see exactly how your data is stored, and run custom queries to understand PostgreSQL better.

## Project Structure

This project uses a clean FastAPI architecture with PostgreSQL:

```txt
api/
├── main.py                    # FastAPI app entry point
├── requirements.txt           # Python dependencies  
├── models/
│   └── entry.py              # Pydantic data models
├── repositories/
│   ├── interface_repository.py    # Database interface
│   └── postgres_repository.py     # PostgreSQL implementation
├── routers/
│   └── journal_router.py     # API endpoints (YOUR MAIN WORK HERE)
└── services/
    └── entry_service.py      # Business logic layer
```

## Your Learning Goals

Complete a Journal API that allows users to:

- ✅ **Store journal entries** (already implemented)
- ✅ **Retrieve all journal entries** (already implemented)
- ❌ **Retrieve single journal entry** (you need to implement)  
- ❌ **Delete specific journal entries** (you need to implement)
- ✅ **Update journal entries** (already implemented)
- ✅ **Delete all entries** (already implemented)
- ❌ **Setup logging** (you need to implement)

## 🎯 Development Tasks (Your Work!)

### 1. API Implementation (Required)

**File: `api/routers/journal_router.py`**

Implement these missing endpoints:

- [ ] **GET /entries/{entry_id}** - Get single entry by ID  
- [ ] **DELETE /entries/{entry_id}** - Delete specific entry

Each endpoint has detailed TODO comments with step-by-step guidance!

### 2. Logging Setup (Required)

**File: `api/main.py`**

- [ ] Configure basic logging using `logging.basicConfig()`
- [ ] Set logging level to INFO
- [ ] Add console handler
- [ ] Test with a startup log message

### 3. Data Model Improvements (Optional)

**File: `api/models/entry.py`**

- [ ] Add custom field validators (e.g., minimum length)
- [ ] Add data sanitization methods
- [ ] Add schema version tracking

### 4. Cloud CLI Setup (Required for Deployment)

**File: `.devcontainer/devcontainer.json`**

- [ ] Choose and uncomment ONE cloud CLI tool:
  - Azure CLI: `"ghcr.io/devcontainers/features/azure-cli:1": {}`
  - AWS CLI: `"ghcr.io/devcontainers/features/aws-cli:1": {}`  
  - Google Cloud CLI: `"ghcr.io/devcontainers/features/gcloud:1": {}`

## 📊 Data Schema

Each journal entry follows this structure:

| Field       | Type      | Description                                | Validation                   |
|-------------|-----------|--------------------------------------------|------------------------------|
| id          | string    | Unique identifier (UUID)                   | Auto-generated               |
| work        | string    | What did you work on today?                | Required, max 256 characters |
| struggle    | string    | What's one thing you struggled with today? | Required, max 256 characters |
| intention   | string    | What will you study/work on tomorrow?      | Required, max 256 characters |
| created_at  | datetime  | When entry was created                     | Auto-generated UTC           |
| updated_at  | datetime  | When entry was last updated                | Auto-updated UTC             |

## 🔌 API Endpoints

| Method | Endpoint           | Status | Description                    |
|--------|--------------------|--------|--------------------------------|
| POST   | /entries           | ✅ Done | Create new journal entry       |
| GET    | /entries           | ✅ Done | List all journal entries       |
| GET    | /entries/{id}      | ❌ TODO | Get single entry by ID         |
| PATCH  | /entries/{id}      | ✅ Done | Update existing entry          |
| DELETE | /entries/{id}      | ❌ TODO | Delete specific entry          |
| DELETE | /entries           | ✅ Done | Delete all entries             |

## ✅ How to Complete This Project

1. **Start by running the existing API** - make sure it works
2. **Study the working endpoints** - understand the patterns
3. **Implement missing endpoints one by one** - follow the TODO comments
4. **Test each endpoint** - use the /docs page to test
5. **Add logging** - see your API in action
6. **Choose a cloud CLI** - prepare for deployment

## 🔧 Troubleshooting

**If the API won't start:**

- Make sure the PostgreSQL container is running: `docker ps`
- Check the container logs: `docker logs your-postgres-container-name`
- Restart the database: `docker restart your-postgres-container-name`

**If you can't connect to the database:**

- Verify the `.env` file exists and has the correct DATABASE_URL
- Make sure Docker Desktop is running
- Try restarting the dev container: `Dev Containers: Rebuild Container`

**If the dev container won't open:**

- Ensure Docker Desktop is running
- Install the "Dev Containers" extension in VS Code
- Try: `Dev Containers: Rebuild and Reopen in Container`

## 🤝 Contributing

We welcome contributions to improve this capstone project! Open an issue and we can plan from there.

### Reporting Issues

Found a bug or have a suggestion? Please [open an issue](https://github.com/learntocloud/journal-starter/issues) with:

- **Clear description** of the problem or suggestion
- **Steps to reproduce** (for bugs)
- **Expected vs actual behavior**
- **Environment details** (OS, Docker version, etc.)

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### What This Means

- ✅ **Commercial use** - You can use this code in commercial projects
- ✅ **Modification** - You can modify and distribute the code
- ✅ **Distribution** - You can distribute the original or modified code
- ✅ **Private use** - You can use this code for personal projects
- ❌ **Liability** - The authors are not liable for any damages
- ❌ **Warranty** - This code comes with no warranty

### Attribution

If you use this project as a foundation for your own work, we'd appreciate a link back to this repository, but it's not required.

---

**Happy coding! 🚀** Built with ❤️ for learning cloud development.
