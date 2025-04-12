---
published: false
---

## Updating the list

1. Request from the Department of Neighborhoods the most-recent copy of their list of active civic associations.
2. It's probably an `.xlsx` file, so you'll need to convert it to a CSV. Along the way, do the following:
    - remove question marks and spaces from column headings
    - change the email column heading to `email`
    - change "Meeting Day/Time" to "Meeting"
    - add new columns "Facebook" and "notes"
    - normalize "Website" data:
        - Only have a single URL
        - Facebook URLs go to the "Facebook" column
        - non-URL content moves to "Email" or "notes" columns as appropriate, or is deleted.
3. Export the spreadsheet as a `.csv` with quoted, escaped cells, and comma separator, saved to `_data/civics.csv`