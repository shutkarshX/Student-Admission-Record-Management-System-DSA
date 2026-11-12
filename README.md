# Student Admission & Record Management System

[![C](https://img.shields.io/badge/Language-C99-A8B9CC.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![GCC](https://img.shields.io/badge/Compiler-GCC-blue.svg)](https://gcc.gnu.org/)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0%2B-green.svg)](https://flask.palletsprojects.com/)
[![React](https://img.shields.io/badge/React-18-61DAFB.svg)](https://react.dev/)
[![Data Structures](https://img.shields.io/badge/Data%20Structure-Singly%20Linked%20List-orange.svg)]()

A comprehensive multi-tier academic solution developed for the **Data Structures & Algorithms (DSA)** curriculum. It implements a student admission lifecycle through a native **C Singly Linked List engine**, backed by a **Python Flask REST API** and an interactive **React admin dashboard**.

---

## 🏛️ System Architecture

```mermaid
graph TD
    subgraph ClientTiers["User Interfaces"]
        CLI["C Terminal Interface<br/>(Student & Admin CLI)"]
        WebUI["React Admin Dashboard<br/>(AdmissionDashboard.jsx)"]
    end

    subgraph LogicTiers["Processing Engines"]
        EngineC["C Linked List Engine<br/>(Dynamic Memory Allocation)"]
        FlaskAPI["Python Flask REST API<br/>(Endpoints & Validation)"]
    end

    subgraph StorageTiers["Persistence Layer"]
        FileC[("students.txt<br/>(Flat File Record Store)")]
        FilePy[("CSV Store<br/>(students / courses / admissions)")]
    end

    CLI --> EngineC -->|"File I/O (Save / Load)"| FileC
    WebUI -->|"HTTP JSON Requests"| FlaskAPI -->|"CSV Reader / Writer"| FilePy
```

---

## 🔗 Data Structure: Singly Linked List Design

The core C engine models student applicants using dynamic heap allocation (`malloc` / `free`) connected through self-referential pointer structures:

```mermaid
classDiagram
    class StudentNode {
        +int id
        +char name[50]
        +char phone[15]
        +char email[50]
        +float marks
        +char desiredBranch[30]
        +int rollNo
        +char assignedBranch[30]
        +char status[15]
        +StudentNode* next
    }
```

```mermaid
flowchart LR
    Head["head*"] --> Node1["[ID: 1] Alice<br/>Status: Approved<br/>Roll: 202601"]
    Node1 --> Node2["[ID: 2] Bob<br/>Status: Pending<br/>Roll: Unassigned"]
    Node2 --> Node3["[ID: 3] Charlie<br/>Status: Rejected<br/>Roll: N/A"]
    Node3 --> NullPtr["NULL"]
```

---

## ⏱️ Algorithmic Complexity

| Operation | Function | Time Complexity | Space Complexity | Description |
| :--- | :--- | :---: | :---: | :--- |
| **Applicant Registration** | `insertEnd()` | $\mathcal{O}(n)$ | $\mathcal{O}(1)$ | Appends a new candidate node to the tail of the list |
| **Search by ID / Roll** | `searchStudent()` | $\mathcal{O}(n)$ | $\mathcal{O}(1)$ | Linear traversal through pointers |
| **Admin Decision** | `approveStudent()` | $\mathcal{O}(n)$ | $\mathcal{O}(1)$ | Finds applicant and assigns roll & branch |
| **File Persistence** | `saveToFile()` | $\mathcal{O}(n)$ | $\mathcal{O}(1)$ | Serializes linked list sequentially to disk |
| **File Deserialization** | `loadFromFile()` | $\mathcal{O}(n)$ | $\mathcal{O}(n)$ | Reconstructs in-memory list on application startup |

---

## 🚀 Running the Components

### 1. C Terminal Engine (`c-terminal-app/`)

Prerequisites: GCC compiler (`MinGW` on Windows or `gcc` on Linux/macOS).

```bash
cd c-terminal-app

# Compile
gcc admission_system.c -o admission_system

# Run
./admission_system
```

**Features:**
* **Student Mode**: Apply for admission, provide contact details, submit academic marks, and check real-time admission status.
* **Admin Mode**: Review queue of pending applications, grant approvals, assign official roll numbers, or reject candidates. All state automatically persists to `students.txt`.

---

### 2. Python Flask REST API (`flask-api/`)

Prerequisites: Python 3.10+

```bash
cd flask-api

# Install dependencies
pip install -r requirements.txt

# Run the API server
python app.py
```
*The server listens on `http://127.0.0.1:5000` with endpoints for students, courses, and admission processing backed by CSV storage.*

---

### 3. React Admin Dashboard (`react-dashboard/`)

The modern frontend dashboard component in `AdmissionDashboard.jsx` provides:
* Live search by student name and ID.
* Multi-parameter department filtering (Computer Science, Electronics, Mechanical, Civil).
* Status distribution metrics (Approved, Pending, Rejected).
* Responsive table view with badge indicators.

---

## 📂 Repository Structure

```text
DSA/
├── c-terminal-app/
│   ├── admission_system.c          # Core C terminal app with linked-list data structures & file I/O
│   └── students.txt                # Persistent record store
├── flask-api/
│   ├── app.py                      # Flask REST backend with CSV storage
│   └── requirements.txt            # Python dependencies
├── react-dashboard/
│   └── AdmissionDashboard.jsx      # Modern React dashboard component
├── .gitignore
└── README.md
```

---

## 📜 Academic Curriculum Mapping
* **Subject:** Data Structures & Algorithms (DSA).
* **Topics Covered:** Dynamic Memory Allocation (`malloc`, `free`), Singly Linked Lists, Pointer Manipulation, File I/O Streams, Linear Search, Separation of Concerns in Software Engineering.
