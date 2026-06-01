# 🎓 Student Result Management System

A desktop application for managing student academic records — built with Python, MySQL, and Tkinter. Automates grade computation using stored procedures and enforces data integrity through database triggers.

## 🔥 Features

- **Marks Entry** — enter and update subject-wise marks per student per semester
- **Automated Grade Calculation** — MySQL stored procedures compute grades and GPA automatically
- **GPA Tracking** — cumulative GPA across semesters with trend view
- **Semester-wise Reports** — generate printable result reports per student or per class
- **Data Integrity** — MySQL triggers enforce valid mark ranges and prevent duplicate entries
- **Search & Filter** — search students by roll number, name, or department

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | Python 3.11 |
| GUI | Tkinter |
| Database | MySQL 8.x |
| DB Connectivity | mysql-connector-python |
| Logic | Stored Procedures, Triggers |

## 🗄️ Database Design

```sql
students        (roll_no, name, department, batch_year)
subjects        (sub_code, sub_name, credits, semester)
marks           (roll_no, sub_code, marks_obtained, exam_date)
grades          (roll_no, semester, gpa, total_credits)
```

## 🚀 Getting Started

```bash
git clone https://github.com/bravesp2726/student-result-management.git
cd student-result-management
pip install -r requirements.txt
python main.py
```

## ✅ Testing

All CRUD operations validated with manual and automated PyTest scripts covering valid/invalid marks entry, GPA computation, and trigger enforcement on boundary values.

## 📄 License

MIT
