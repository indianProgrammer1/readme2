

## Project Overview
**ExecutionCoach** is a console-based C++ application (no UI) designed to 
analyze trading data from a CSV file based 
on predefined rules (`rules.conf`) and store the results in a PostgreSQL database.

---

## ⚙️ System Requirements

- **C++17** or higher  
- **PostgreSQL** installed (recommended version 14 or above)  
- **libpqxx** library for database communication  
- **Operating System:** Windows   
- **Compiler:**  
  - Windows → `g++` (MinGW) or `MSVC`  
 

---

## 🏗️ Build and Run Instructions## ⚙️ Step 1 — Install PostgreSQL

1. Download PostgreSQL from:  
   👉 https://www.postgresql.org/download/windows/
2. Run the installer and make sure to:
   - Remember your **username** (default: `postgres`)
   - Remember your **password**
   - Install **pgAdmin** when prompted
3. After installation, verify PostgreSQL is running by opening **pgAdmin** or running:
 
---
## ⚙️ Step 2 — Install libpqxx (PostgreSQL C++ Library)


Open Command Prompt and run:
`git clone https://github.com/microsoft/vcpkg.git
`cd vcpkg
`bootstrap-vcpkg.bat`

This installs the vcpkg package manager.

Install libpqxx and dependencies:
`vcpkg install libpqxx:x64-windows
---
## ⚙️ Step 3 
Open CMD and go to the folder containing your files:
Example:
`ExecutionCoach.exe 
`"pathTo/trades.csv" 
`"pathTo/rules.conf" 
 `"host=localhost port=5432 dbname=postgres user=postgres password=YOUR_PASSWORD"
 

   
   


