# GreenClass — Testing checklist and troubleshooting

Test on a local server (`python -m http.server 8000`) in a current Chrome, Edge, Firefox or Safari.

## Checklist
- [ ] Page loads with no red errors in the console (F12).
- [ ] Every menu link scrolls to its section; the mobile menu (☰) opens and closes.
- [ ] Theme toggle switches light/dark and remembers the choice after refresh.
- [ ] Five circular class cards show; clicking one shows only that class's subjects.
- [ ] Classes 11 and 12 show a stream picker (Science, Commerce, Humanities) and the subject list changes.
- [ ] Clicking a subject shows its chapters; Class 9 and unlisted subjects show "Chapter list not added yet".
- [ ] Opening a chapter shows 10 material cards, each "Coming soon" until you add a PDF.
- [ ] Search "life" finds the Life Processes chapter; a nonsense word shows the friendly empty state.
- [ ] Class → Subject → Chapter → Type filters narrow down results together with the search box.
- [ ] After adding a real PDF and setting `status: "available"`, View PDF opens a tab, Download PDF saves a file, Back to materials scrolls up.
- [ ] A registry entry with a wrong path shows "File not found" (on a server) instead of a broken button.
- [ ] PYQ filters (class, subject, category, year, difficulty, question type) work; with no papers an empty state shows.
- [ ] Quiz: choose Class 10 → Science → Start; four options, instant feedback with explanation, progress bar, final score, Retry.
- [ ] Planner: add/tick/delete a task; add a reminder; mark a chapter studied (a +3 day reminder appears); progress bars change.
- [ ] Bookmark (☆) a card; it shows in Bookmarks; opening a PDF adds it to Recently opened.
- [ ] Keyboard only: Tab reaches every control with a visible orange focus ring; Enter/Space activate buttons.
- [ ] Resize to phone width: nothing scrolls sideways; text stays readable on the background.

Honest note: the code was syntax-checked and its data cross-checked (chapter names, element IDs) before delivery,
but it has not been run through a full browser test. Please run this checklist once and report anything that fails.

## Troubleshooting
| Problem | Likely cause | Fix |
|---|---|---|
| Blank class area / "Something went wrong" | A typo in a file you edited (missing comma, quote or bracket) | Open the console (F12), read the line number, fix the comma/quote |
| Edited a PDF entry, nothing changed | Cached page | Hard refresh (Ctrl+F5) |
| PDF card says "coming soon" | `status` is not exactly `"available"` or `file` is empty | Fix the entry |
| "File not found" on a card | Path or file name does not match | Compare `file:` with the real name, lowercase and hyphens |
| PDF card does not appear in a chapter | `chapter` text differs from `syllabus.js` | Copy the chapter name exactly |
| Download opens the PDF instead of saving | Some browsers ignore `download` for cross-origin files | Keep PDFs on the same site; right-click → Save link as |
| Everything works but no "File not found" checks | You opened `index.html` directly | Use a local server |
| Fonts look different offline | Google Fonts not reachable | Expected; a fallback font is used |
| Bookmarks vanished | Browser data cleared or a different browser/device | localStorage is per browser and device |
