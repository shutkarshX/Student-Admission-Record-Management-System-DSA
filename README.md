# Student Admission & Record Management System

A multi-tier admission management solution featuring a **C-based linked-list engine**, an **interactive React admin dashboard**, and a **Python Flask REST API** with CSV persistence.

---

## 🏗️ Architecture & Modules

```text
DSA/
├── c-terminal-app/
│   └── admission_system.c          # Core C terminal app with linked-list data structures & file I/O
├── react-dashboard/
│   └── AdmissionDashboard.jsx      # Modern React UI with search, department filtering & status tracking
├── flask-api/
│   ├── app.py                      # Flask REST backend with CSV storage
│   └── requirements.txt            # Python dependencies
├── .gitignore
└── README.md
```

---

## 🚀 Components

### 1. C Terminal Engine (`c-terminal-app/`)
* **Data Structure**: Singly Linked List (`struct Student* next`) where each applicant node holds ID, contact details, academic marks, and branch allocation state.
* **Dual Roles**:
  * **Student Mode**: Register application, view merit status, and check allocated branch.
  * **Admin Mode**: View pending applications, approve/reject candidates, assign roll numbers, and persist state to `students.txt`.
* **Compile & Run**:
  ```bash
  cd c-terminal-app
  gcc admission_system.c -o admission_system
  ./admission_system
  ```

---

### 2. React Admin Dashboard (`react-dashboard/`)
* **Tech Stack**: React 18 (Hooks, `useState`, `useMemo`).
* **Features**:
  * Real-time search across candidate names, departments, and emails.
  * Department filter (`Computer Science`, `Engineering`, `Business`, `Medicine`, `Law`, `Sciences`).
  * Status badges (`Pending`, `Admitted`, `Rejected`, `Waitlisted`).
  * Interactive candidate details modal and application editor.

---

### 3. Flask REST Backend (`flask-api/`)
* **Tech Stack**: Python 3, Flask.
* **Storage**: Persistent CSV-based data stores (`students.csv`, `courses.csv`, `admissions.csv`).
* **Endpoints**:
  * Application submissions and status queries.
  * Course catalogs and admission record management.
* **Run**:
  ```bash
  cd flask-api
  pip install -r requirements.txt
  python app.py
  ```

---

## 🛠️ Key Technical Highlights
* **Memory Management**: Manual dynamic allocation and node traversal in C.
* **Data Flow**: Demonstrates system design across low-level procedural C, declarative React UI, and a Python micro-backend.
