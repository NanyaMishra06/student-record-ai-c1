# AI-Assisted Student Record and Result Management System

**Course Code**: PRC1001  
**Course Name**: Programming in C  
**Academic Program**: B.Tech Computer Science and Engineering (Semester I)  
**Institution**: University of Petroleum and Energy Studies (UPES), Dehradun  
**Student Name**: Nanya Mishra  
**SAP ID**: 590033891  
**Roll No.**: R214226020  
**Batch**: 20  
**Repository**: [NanyaMishra06/student-record-ai-c1](https://github.com/NanyaMishra06/student-record-ai-c1)  

---

## 📖 Table of Contents
1. [Project Overview](#-project-overview)
2. [Key Features](#-key-features)
   - [Part A: Core C Requirements](#part-a--core-c-requirements)
   - [Part B: AI-Assisted Academic Advisor](#part-b--ai-assisted-academic-advisor)
3. [Repository File Structure](#-repository-file-structure)
4. [Data Structures & Design](#-data-structures--design)
5. [Compilation & Execution Instructions](#-compilation--execution-instructions)
6. [Menu Navigation & Usage Guide](#-menu-navigation--usage-guide)
7. [Academic Advisor Logic & Decision Matrix](#-academic-advisor-logic--decision-matrix)
8. [Testing & Verification](#-testing--verification)
9. [GitHub Workflow & Commit History](#-github-workflow--commit-history)
10. [Viva Preparation & Concept Summary](#-viva-preparation--concept-summary)

---

## 📌 Project Overview
The **AI-Assisted Student Record and Result Management System** is a robust console-based, menu-driven software application written in standard C. Developed as a semester project for **PRC1001 (Programming in C)**, it bridges fundamental C constructs—structures, arrays, loops, string operations, sorting algorithms, and modular functions—with modern software engineering workflows including Git version control, GitHub issue tracking, and an AI-assisted heuristic Academic Advisor module.

---

## 🎯 Key Features

### Part A – Core C Requirements
1. **Menu-Driven Interface**: Clean, looped console UI providing seamless user access to 9 distinct functional options and a safe exit.
2. **Preloaded Baseline Records**: Program initializes with 5 verified student profiles covering all 4 academic years (1st, 2nd, 3rd, and 4th years).
3. **Record Storage**: Comprehensive data tracking for each student:
   - `SAP ID` (Unique 9-digit `long int`)
   - `Roll No.` (String alphanumeric identifier)
   - `Name` (Full name string, supporting whitespace)
   - `Phone No.` (Contact string)
   - `Email ID` (Official university email string)
   - `Year` (Integer 1 to 4)
   - `Semester` (Integer 1 to 8)
   - `SGPA Array` (`float[8]` storing Semester Grade Point Averages; `0.0` for upcoming semesters)
   - `CGPA` (Calculated cumulative grade point average)
4. **Student Record Operations**:
   - **Add Student**: Interactive data entry with automated duplication checks against existing SAP IDs and input bounding.
   - **Search Record**: Fast linear search by SAP ID displaying complete student profile and semester breakdown.
   - **Delete Record**: Deletes an existing record by SAP ID and shifts subsequent array elements leftward to maintain continuous memory.
   - **Display All Records**: Formatted, card-style breakdown of all enrolled student records.
5. **Analytics & Sorting**:
   - **CGPA Calculation**: Computes dynamic average based solely on completed semesters (`sgpa > 0.0`), preventing artificial score deflation for junior students.
   - **Cohort Analysis (Year-wise Average CGPA)**: Aggregates performance by academic year (1st through 4th) to analyze batch trends.
   - **Sort by SAP ID**: Bubble sort arranging records in ascending order of SAP ID on a copied array (preserving primary entry order).
   - **Sort by Name**: Alphabetical ascending bubble sort using `strcmp()` on a copied array.

### Part B – AI-Assisted Academic Advisor
- Employs a heuristic decision-making engine in C suggested and refined using AI tools.
- Evaluates student CGPA against 4 defined performance tiers.
- Performs diagnostic analysis by looping across semester SGPAs to identify the specific lowest-scoring semester and generate actionable counsel.
- Offers dual execution: single student lookup or comprehensive whole-class advisory report.

---

## 📂 Repository File Structure

```
student-record-ai-c1/
├── .gitignore             # Ignores executables and temporary build files
├── 590033891.c            # Complete C source file named strictly as SAP_ID.c
├── README.md              # Detailed project overview and technical documentation
├── AI_USAGE_LOG.md        # Comprehensive AI assistance and verification log
└── tests/
    ├── sample_input.txt   # Automated batch menu test input sequence
    └── sample_output.txt  # Verified program execution console output log
```

---

## 🏗 Data Structures & Design

```c
#define MAX_STUDENTS 100
#define TOTAL_SEMESTERS 8

struct Student {
    long int sap_id;             /* Unique student identifier */
    char roll_no[20];            /* Alphanumeric roll number */
    char name[50];               /* Full student name */
    char phone[15];              /* Contact phone number */
    char email[50];              /* Email address */
    int year;                    /* Current academic year (1-4) */
    int semester;                /* Current semester (1-8) */
    float sgpa[TOTAL_SEMESTERS]; /* SGPA history for up to 8 terms */
    float cgpa;                  /* Cumulative Grade Point Average */
};

/* Database array */
struct Student students[MAX_STUDENTS];
int student_count = 0;
```

---

## ⚙️ Compilation & Execution Instructions

### Prerequisites
- GCC Compiler (MinGW / TDM-GCC / GCC on Linux / Clang on macOS)

### 1. Compile the Program
Open a terminal in the project directory:
```bash
gcc -Wall -Wextra 590033891.c -o 590033891.exe
```

### 2. Run Interactively
```bash
# On Windows
.\590033891.exe

# On Linux/macOS
./590033891.exe
```

### 3. Run Automated Test Suite
Feed `tests/sample_input.txt` to verify all menu flows:
```bash
# On Windows PowerShell
Get-Content tests\sample_input.txt | .\590033891.exe

# On Linux/macOS / Git Bash
./590033891.exe < tests/sample_input.txt
```

---

## 🧭 Menu Navigation & Usage Guide

```
------------------------- MAIN MENU -------------------------
1. Add Student Details
2. Search and Display a Student Record
3. Calculate CGPA of Each Student
4. Calculate Average CGPA of Students by Year
5. Display Records of All Students
6. Delete an Individual Student Record
7. Display All Records in Increasing Order of SAP ID
8. Display All Records in Increasing Order of Name
9. AI-Assisted Academic Advisor
0. Exit
-------------------------------------------------------------
```

---

## 🤖 Academic Advisor Logic & Decision Matrix

The academic advisor evaluates student CGPA against 4 AI-suggested performance tiers:

| Tier / Category | CGPA Range | AI Recommendation & Action Plan |
| :--- | :--- | :--- |
| **Excellent Performance** | $\text{CGPA} \ge 8.5$ | Excellent performance – maintain your current study pattern and explore competitive coding, internships, or mini-projects. |
| **Good Performance** | $7.0 \le \text{CGPA} < 8.5$ | Good performance – stay consistent with lecture notes and revise core subjects to push your CGPA above 8.5. |
| **Needs Improvement** | $5.5 \le \text{CGPA} < 7.0$ | Needs improvement – focus more on subjects with lower SGPA and solve extra practice problems before mid-sem/end-sem exams. |
| **Requires Immediate Attention** | $\text{CGPA} < 5.5$ | Requires immediate attention – meet your faculty advisor, attend remedial doubt sessions, and clear core fundamentals. |

---

## 🧪 Testing & Verification

The baseline database contains 5 representative student records:

| SAP ID | Roll No. | Student Name | Year | Sem | SGPA History (Completed) | CGPA | Advisor Category |
| :---: | :---: | :--- | :---: | :---: | :--- | :---: | :--- |
| `590033891` | R214226020 | Nanya Mishra | 1 | 1 | S1: 9.25 | **9.25** | Excellent Performance |
| `50010202` | R214225002 | Aarav Sharma | 2 | 3 | S1: 7.80, S2: 8.10, S3: 8.25 | **8.05** | Good Performance |
| `50010208` | R214224008 | Riya Patel | 3 | 5 | S1: 6.40, S2: 6.10, S3: 5.80, S4: 6.30, S5: 6.15 | **6.15** | Needs Improvement |
| `50010201` | R214225001 | Kabir Mehra | 2 | 4 | S1: 5.20, S2: 4.80, S3: 5.00, S4: 4.90 | **4.97** | Requires Immediate Attention |
| `50010204` | R214223004 | Ananya Joshi | 4 | 7 | S1: 8.60, S2: 8.80, S3: 9.10, S4: 8.70, S5: 8.90, S6: 9.20, S7: 9.00 | **8.90** | Excellent Performance |

---

## 🐙 GitHub Workflow & Commit History

In compliance with the assignment instructions, version control was maintained through progressive, meaningful commits:

1. `Initial C program: define student structure and project skeleton (590033891.c)`: Foundation data structures, memory limits, and sample loader.
2. `Implement student record functions: add, search, delete, and display records`: Core CRUD operations with bounds checking and memory shifting.
3. `Implement CGPA calculation and sorting algorithms by SAP ID and Name (Closes #1)`: Analytical CGPA calculations, cohort breakdown, and Bubble Sort algorithms on copied structures.
4. `AI-assisted advisor + documentation: heuristic advisor engine, test suite, and AI usage log`: Rule-based academic advisor module, markdown documentation, AI usage log, and test suite.

---

## 🎓 Viva Preparation & Concept Summary

Key questions and answers for viva assessment:
- **Q: How does CGPA calculation handle students who haven't completed 8 semesters?**  
  *A*: The loop only counts semesters where `sgpa[i] > 0.0f`. Sum is divided strictly by completed semesters (`completed_sems`), avoiding dividing by 8.
- **Q: How does sorting avoid corrupting the original student list?**  
  *A*: The sorting functions copy `students[]` into a local `temp_list[]` array before sorting and printing, ensuring the primary list order remains unchanged.
- **Q: How does the delete operation work in memory?**  
  *A*: When a target SAP ID is found at index $i$, a loop shifts all elements from index $i+1$ to $n-1$ one position to the left, and decrements `student_count`.
- **Q: How did AI assist you in this project?**  
  *A*: AI served as an ideation assistant to suggest the 4 CGPA advisory tiers, boundary test cases for incomplete semesters, and safe string input patterns in C.
