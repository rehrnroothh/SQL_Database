# SoundGood School Database

This repository contains a simple SQL database schema and seed data for a school project based on a music school called SoundGood.

## Contents

- `SoundGood.sql` — database schema (tables, relationships, constraints).
- `all_inserts.sql` — sample data and helper trigger for reciprocal siblings.
- `er_diagram (1).asta` — ER diagram source file.
- `license.xml` — project license metadata.

## Getting Started

The SQL files are plain SQL and should work in a PostgreSQL environment (due to `GENERATED ALWAYS AS IDENTITY` and `plpgsql`).

### 1) Create the schema

```sql
\i SoundGood.sql
```

### 2) Load sample data

```sql
\i all_inserts.sql
```

## Schema Overview

The schema models students, instructors, instruments, lessons, and scheduling:

- **Students** with contact persons and optional siblings.
- **Instruments** and the many-to-many relationships between students and instruments.
- **Instructors** and the instruments they can teach.
- **Lessons** (individual, group, ensemble) linked to time slots and pricing.
- **Rental instruments** linked to students.

Key tables:

- `student`, `contact_person`, `student_sibling`
- `instrument`, `student_instrument`
- `instructor`, `instructor_instrument`, `time_slot`
- `lesson`, `individual_lesson`, `group_lesson`, `ensemble`
- `pricing_scheme`, `rental_instrument`

## Notes

- The `student_sibling` table includes a trigger that ensures reciprocal sibling relationships are inserted automatically.
- Dates are stored as strings (e.g., `YYYYMMDD`) in this project’s schema.

## License

See `license.xml` for licensing details.
