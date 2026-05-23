# Community Service Tracker — Final Project

## Project Overview
Students will complete a Node.js + PostgreSQL web application that tracks community service hours. The app allows users to log service records and generate a total-hours report by student.

---

## Setup Instructions
1. Clone / download the project folder
2. Run `npm install`
3. Copy `.env.example` to `.env` and fill in your PostgreSQL connection string
4. Run `node server.js` (or `npm start`)
5. Open `http://localhost:3000` in your browser

---

## Student Tasks (6 files total)

### ✏️ COMMENT (2 files)
Add comments explaining what the code does — do NOT change any logic.

| File | What to do |
|------|-----------|
| `db/index.js` | Add a comment above each of the 5 marked sections |
| `models/serviceModel.js` | Add a comment above each of the 3 functions describing what it does, its parameters, and return value |

---

### 🐛 FIX BUGS (2 files)
Two bugs per file. Find each bug, fix it, and add a comment explaining what was wrong.

| File | Bug 1 | Bug 2 |
|------|-------|-------|
| `routes/service.js` | POST body uses `numHours` but should be `hours` | Report route uses `router.post` but should be `router.get` |
| `public/script.js` | `student_id` is missing from the fetch body in the submit handler | `loadReport()` fetches `/api/service/hours-summary` but should be `/api/service/report` |

---

### ➕ ADD CODE (2 files)
Add the missing code described in the comment blocks.

| File | What to add |
|------|------------|
| `schema.sql` | A `hours NUMERIC(5,2) NOT NULL` column in the `service_records` table |
| `public/index.html` | A `<label>` + `<input>` for `student_id` in the log-service form |

---

## Answer Key (Teacher Only)

### schema.sql — add after `activity_date` line:
```sql
  hours        NUMERIC(5,2) NOT NULL,
```

### public/index.html — add after the student_name input:
```html
<label for="student_id">Student ID</label>
<input type="text" id="student_id" name="student_id"
       placeholder="e.g. 10432" required />
```

### routes/service.js — Bug 1:
Change `numHours` → `hours` in the destructuring line

### routes/service.js — Bug 2:
Change `router.post('/report', ...)` → `router.get('/report', ...)`

### public/script.js — Bug 1:
Add `student_id` to the fetch body object:
`JSON.stringify({ student_name, student_id, activity_date, hours, recipient })`

### public/script.js — Bug 2:
Change `"/api/service/hours-summary"` → `"/api/service/report"`
