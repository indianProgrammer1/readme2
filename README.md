# 🧠 ExecutionCoach

## 📄 Project Overview
**ExecutionCoach** is a console-based C++ application (no UI) designed to analyze trading data from a CSV file using predefined rules (`rules.conf`) and store the analysis results in a PostgreSQL database.

---

## ⚙️ System Requirements
- **C++ Version:** C++17 or higher  
- **Database:** PostgreSQL (recommended version 14 or above)  
- **Library:** libpqxx (C++ interface for PostgreSQL)  
- **Operating System:** Windows  
- **Compiler Options:**  
  - Windows → `g++` (MinGW) or Microsoft Visual Studio (MSVC)  

---

## 🚀 Installation & Setup

### 🧩 Step 1 — Install PostgreSQL
1. Download PostgreSQL for Windows:  
   👉 [https://www.postgresql.org/download/windows/](https://www.postgresql.org/download/windows/)
2. During installation:  
   - Remember your **username** (default: `postgres`)  
   - Remember your **password**  
   - Select **pgAdmin** when asked to install it.  
3. After installation, verify PostgreSQL is running by:  
   - Opening **pgAdmin**, or  
   - Running this command in Command Prompt:  
     ```
     psql -U postgres -l
     ```

---

### 📦 Step 2 — Install libpqxx (PostgreSQL C++ Library)
1. Open **Command Prompt** and run the following commands:  
   ```
   git clone https://github.com/microsoft/vcpkg.git
   cd vcpkg
   bootstrap-vcpkg.bat
   ```
   This installs the **vcpkg** package manager.  

2. Now install **libpqxx** and its dependencies:  
   ```
   vcpkg install libpqxx:x64-windows
   ```

---

### ⚙️ Step 3 — Verify DLL Placement
Make sure your folder looks like this:

```
C:\ExecutionCoach\
├── ExecutionCoach.exe
├── pqxx.dll
├── libpq.dll
├── libssl-3-x64.dll
├── libcrypto-3-x64.dll
├── rules.conf
├── schema.sql
└── trades.csv
```

All the required DLLs should be in the same folder as `ExecutionCoach.exe`.

---

### 🏗️ Step 4 — Build the Project
If you have `g++` installed, you can compile directly from CMD:
```
g++ -std=c++17 -I"path\to\libpqxx\include" -L"path\to\libpqxx\lib" *.cpp -lpqxx -lpq -o ExecutionCoach.exe
```

Alternatively, you can build using Visual Studio (configure include/linker paths for libpqxx).

---

## ▶️ Step 5 — Run the Application
Open **Command Prompt**, navigate to the folder where `ExecutionCoach.exe` is located, and run:

```
ExecutionCoach.exe "C:\path\to\trades.csv" "C:\path\to\rules.conf" "host=localhost port=5432 dbname=postgres user=postgres password=YOUR_PASSWORD"
```

📝 **Example:**  
```
ExecutionCoach.exe "Sample_Trades_CSV__preview_.csv" "rules.conf" "host=localhost port=5432 dbname=postgres user=postgres password=5432"
```

---

## ✅ Output Example
When executed correctly, the console will display:
```
Connected to: postgres

=== Execution Summary ===
Processed trades: 120
Parser errors:    0
DB write errors:  0

Decisions:
OK          : 80
WARN        : 25
ADJUST_QTY  : 10
BLOCK       : 5
Queue drops : 0
==========================
```

   





