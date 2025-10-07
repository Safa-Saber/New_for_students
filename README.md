# New_for_students

# Hi, I'm Safa!

## About Me
- Learning Git and GitHub
- New to coding
- Student

## My Projects
- My first repository
- Learning everyday!

### Quick Reference

| What You Want | How to Write It | Result |
|--------------|-----------------|--------|
| Big title | `# Title` | # Title |
| Subtitle | `## Subtitle` | ## Subtitle |
| Bold | `**bold**` | **bold** |
| Italic | `*italic*` | *italic* |
| Code | `` `code` `` | `code` |
| Link | `[text](url)` | [text](url) |
| Bullet | `- item` | - item |
| Number | `1. item` | 1. item |

---

**Remember**: Git is like saving your game - do it often!

*Keep practicing these commands and they'll become second nature!*

<<<<<<< HEAD

*This is going to be added after the end!*
=======
## The end!
>>>>>>> 6d0cac9d5921d6f1b2892a6c11ea05c032eb6aca

# the change

## the change

### the final on the my mac

### Now online 

# Okay now here

# I am making some new changes


*This is our final day!*



![The new picture I added](https://github.com/Safa-Saber/New_for_students/blob/main/OPEN%20DAYS.png)

``` python
# Start with just reading data
import mysql.connector
import pandas as pd
from datetime import datetime

# ============= SECTION 1: DATABASE CONNECTION =============
# This connects to your MySQL database
conn = mysql.connector.connect(
    host="localhost", 
    user="root",
    password="u5FwHND3Kz@dkUs", 
    database="School_team"
)

# Load data into pandas DataFrame
df = pd.read_sql("SELECT * FROM students", conn)
conn.close()  # Always close connection to free resources

# ============= SECTION 2: DATA EXPLORATION =============
# First, let's see what we're working with
print("Data preview:")
print(df.head())
print("\nColumn names:", df.columns.tolist())

# ============= SECTION 3: BASIC STATISTICS =============
# Calculate the basic numbers we need for the report
total_students = len(df)
avg_grade = df['grade'].mean()
avg_attendance = df['attendance_percent'].mean()
highest_grade = df['grade'].max()
lowest_grade = df['grade'].min()

# ============= SECTION 4: FIND TOP PERFORMERS =============
# Sort students by grade and get the top 3
top_3_students = df.nlargest(3, 'grade')[['name', 'grade']]

# ============= SECTION 5: FIND STUDENTS WHO NEED HELP =============
# Find students with grades below 80
students_need_help = df[df['grade'] < 80][['name', 'grade']]

# ============= SECTION 6: ATTENDANCE ANALYSIS =============
# Find students with poor attendance (less than 85%)
poor_attendance = df[df['attendance_percent'] < 85][['name', 'attendance_percent']]

# ============= SECTION 7: SUBJECT PERFORMANCE =============
# Group by subject and calculate statistics
subject_stats = df.groupby('subject')['grade'].agg(['mean', 'min', 'max', 'count']).round(2)

# ============= SECTION 8: BUILD THE REPORT =============
# Get current date for the report
report_date = datetime.now().strftime("%Y-%m-%d")
report_time = datetime.now().strftime("%H:%M")

# Create the report as a formatted string
report = f"""
========================================
    STUDENT PERFORMANCE REPORT
    Date: {report_date}
    Time: {report_time}
========================================

OVERALL STATISTICS:
-------------------
Total Students: {total_students}
Average Grade: {avg_grade:.2f}
Average Attendance: {avg_attendance:.1f}%
Highest Grade: {highest_grade}
Lowest Grade: {lowest_grade}
Grade Range: {highest_grade - lowest_grade}

TOP 3 PERFORMERS:
-----------------
{top_3_students.to_string(index=False)}

STUDENTS NEEDING SUPPORT (Grade < 80):
---------------------------------------
{students_need_help.to_string(index=False) if len(students_need_help) > 0 else "None - All students are performing well!"}

ATTENDANCE CONCERNS (Below 85%):
---------------------------------
{poor_attendance.to_string(index=False) if len(poor_attendance) > 0 else "None - All students have good attendance!"}

PERFORMANCE BY SUBJECT:
-----------------------
{subject_stats.to_string()}

========================================
         END OF REPORT
========================================
"""

# ============= SECTION 9: DISPLAY THE REPORT =============
print(report)

# ============= SECTION 10: SAVE REPORT TO FILE =============
# Create a filename with the date
filename = f"student_report_{report_date}.txt"

# Write the report to a file
with open(filename, 'w') as file:
    file.write(report)

print(f"\n Report saved to: {filename}")
```
