GREENCLASS — PDF FOLDER GUIDE
=============================

Put your PDF files in this folder, inside the right class and subject folder.

FOLDER PATTERN
  pdfs/class-<number>/<subject-id>/<file-name>.pdf

Subject ids (folder names) used by the website:
  Classes 8-10 : science, mathematics, english, hindi, social-science, sanskrit, information-technology
  Classes 11-12: physics, chemistry, mathematics, biology, english, computer-science,
                 informatics-practices, accountancy, business-studies, economics,
                 history, geography, political-science, sociology, psychology
  (entrepreneurship is also defined in js/syllabus.js; create pdfs/class-11/entrepreneurship if you use it)

FILE NAMING RULES
  - Use only lowercase letters, numbers and hyphens. No spaces, no capital letters.
  - Pattern: <chapter-name>-<type-suffix>.pdf
  - Wrong: "Life Processes Notes (final).PDF"   Right: life-processes-notes.pdf

TYPE SUFFIXES
  short-notes, notes (detailed notes), lecture-notes, important-questions, solved-examples,
  worksheet, summary, formulas, mind-map, checklist,
  board-paper, school-exam, sample-paper, pyq

EXAMPLES
  pdfs/class-10/science/life-processes-notes.pdf
  pdfs/class-10/science/life-processes-lecture-notes.pdf
  pdfs/class-10/science/life-processes-pyq.pdf
  pdfs/class-10/mathematics/real-numbers-notes.pdf
  pdfs/class-12/physics/electrostatics-notes.pdf
  Whole-paper example: pdfs/class-10/science/board-paper-2024.pdf

AFTER YOU ADD A FILE
  1. Open js/pdf-library.js
  2. Add (or edit) one entry whose "file" path matches the file exactly
  3. Set status to "available"
  4. Refresh the website

All folders are empty on purpose. This project contains NO real PDFs.
Never put a file here that you do not have the right to share.
