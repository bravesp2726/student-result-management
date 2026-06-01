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
-- Key tables
students        (roll_no, name, department, batch_year)
subjects        (sub_code, sub_name, credits, semester)
marks           (roll_no, sub_code, marks_obtained, exam_date)
grades          (roll_no, semester, gpa, total_credits)

-- Stored procedure: auto-calculate grade on marks insert
DELIMITER //
CREATE PROCEDURE calculate_grade(IN p_roll_no VARCHAR(20), IN p_semester INT)
BEGIN
    -- Computes weighted GPA and updates grades table
END //
DELIMITER ;

-- Trigger: validate marks before insert
CREATE TRIGGER validate_marks
BEFORE INSERT ON marks
FOR EACH ROW
BEGIN
    IF NEW.marks_obtained < 0 OR NEW.marks_obtained > 100 THEN
        SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = 'Marks must be between 0 and 100';
    END IF;
END;
```

## 📐 Project Structure

```
student-result-management/
├── ui/
│   ├── main_window.py     # Main Tkinter window
│   ├── marks_entry.py     # Marks entry form
│   ├── report_view.py     # Result report screen
│   └── search_panel.py    # Student search
├── db/
│   ├── connection.py      # MySQL connection manager
│   ├── schema.sql         # Full schema with procedures + triggers
│   └── queries.py         # All SQL queries
├── tests/
│   └── test_crud.py       # Manual + automated test cases
└── main.py
```

## 🚀 Getting Started

```bash
git clone https://github.com/bravesp2726/student-result-management.git
cd student-result-management

pip install -r requirements.txt

# Set up MySQL
mysql -u root -p < db/schema.sql

# Update DB credentials in db/connection.py

# Run the app
python main.py
```

## ✅ Testing

All CRUD operations validated with both manual test cases and automated PyTest scripts covering:
- Valid and invalid marks entry
- Grade calculation accuracy
- GPA computation across multiple semesters
- Trigger enforcement on boundary values (0, 100, -1, 101)

## 📄 License

MIT
