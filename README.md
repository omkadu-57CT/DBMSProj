# Student Management System (MySQL + Python)

## Structure
| File | Purpose |
|------|---------|
| `schema.sql` | Database, tables, indexes, function, triggers, procedure, views |
| `sample_data.sql` | Demo departments, students, courses, marks, attendance |
| `queries.sql` | 10 useful reports (rankings, pass %, attendance, etc.) |
| `app.py` | Command-line app (CRUD, enrollment, marks, report card) |

## Setup
1. Requires MySQL 8.0+ and Python 3.8+.
2. Load the database:
   ```
   mysql -u root -p < schema.sql
   mysql -u root -p < sample_data.sql
   ```
3. Install the driver: `pip install mysql-connector-python`
4. Run the app:
   ```
   export DB_USER=root DB_PASSWORD=yourpassword
   python app.py
   ```
   (On Windows: `set DB_USER=root` and `set DB_PASSWORD=yourpassword`.)

## Database design
- departments 1—N students, departments 1—N courses
- students N—N courses through `enrollments` (holds semester, marks, grade)
- `attendance` records per student, course and date
- Grade is derived from marks by `fn_grade()` through triggers
- `vw_student_gpa` computes credit-weighted GPA on a 10-point scale

## Ideas to extend
Add a teachers table, user login with roles, fee management, a web front end (Flask or Django), or export of report cards to PDF.

## Web frontend (Flask)
```
cd web
pip install -r requirements.txt
export DB_USER=root DB_PASSWORD=yourpassword
python app.py        # open http://localhost:5000
```
Pages: dashboard (with department bars), student list with search, add/edit/delete and CSV export, student profile (report card, inline marks, enrollment, attendance), courses (add courses and departments), bulk attendance marking, and a GPA leaderboard. Dark mode follows your system setting.
# DBMSProj
# DBMSProj
