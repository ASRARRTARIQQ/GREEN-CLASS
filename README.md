# GreenClass — Learn at Your Own Pace

A free, nature-inspired study website for CBSE Classes 8–12, built with plain HTML, CSS and JavaScript.
No framework, database, API key or paid service is needed.

> **Honest status:** the website is complete and ready to use, but it ships **without any real study PDFs**
> and with **chapter lists that are not yet verified** against the official 2026–27 CBSE curriculum
> (Class 9 chapter lists are intentionally empty). You add the PDFs, and you verify the syllabus.

## Project structure

```
GreenClass/
├── index.html            the page (16 numbered sections)
├── css/style.css         all styling (19 numbered sections)
├── js/
│   ├── syllabus.js       session, classes, subjects, chapters   (SECTIONS 03-04)
│   ├── pdf-library.js    your PDF list                          (SECTION 05)
│   ├── quiz.js           quiz questions                         (SECTION 11 data)
│   └── script.js         website behaviour (15 numbered sections)
├── pdfs/                 put your PDF files here (see pdfs/README.txt)
├── assets/images, icons  background picture and logo
└── README.md
```

## 1. Create or extract the project folder
Unzip `GreenClass.zip`. You should see the folder above. Keep the folders exactly as they are.

## 2. Open the website on your computer
- **Quick look:** double-click `index.html`. Everything works except the automatic "file not found" check for PDFs.
- **Best way (recommended):** run a tiny local server so PDFs and downloads behave like the real website.
  - Install Python from python.org, open a terminal in the GreenClass folder, run `python -m http.server 8000`
    (or `python3 -m http.server 8000`), then open http://localhost:8000
  - Or install VS Code and its "Live Server" extension, then right-click `index.html` → Open with Live Server.

## 3. Edit the files
Open the folder in a free editor such as VS Code. Every file is divided into numbered sections. Use Search (Ctrl+F) for
`SECTION 07`, for example. Change one thing, save, refresh the browser.
- Colours: `css/style.css` SECTION 01 (and dark theme in SECTION 15)
- Hero text: `index.html` SECTION 04
- Contact email: `index.html` SECTION 14 (replace `your-email@example.com`)
- Background picture: replace `assets/images/forest.svg`, or change the `url(...)` in CSS SECTION 04

## 4. Add classes, subjects and chapters
All in `js/syllabus.js`.
- **New subject:** add a line to `GC_SUBJECTS` (copy an existing line). Use a lowercase id with no spaces.
  Remember to create a folder `pdfs/class-X/<id>`.
- **Rename a subject:** change its `name`.
- **Remove a subject:** delete its line.
- **Chapters:** edit the list for the key `"class:subject"` in `GC_CHAPTERS`, e.g. `"10:science": [ "Life Processes", ... ]`.
- Streams for Classes 11–12 are controlled by the `streams` field of each subject.
- If you rename a chapter, update the same text in `js/pdf-library.js` and `js/quiz.js`, or the PDF will not match.

## 5. Add PDF notes and lecture notes
1. Name the file using lowercase and hyphens, e.g. `life-processes-notes.pdf`.
2. Put it in `pdfs/class-10/science/`.
3. Open `js/pdf-library.js` and add an entry (a template is in the file):
```js
{
  class: 10, subject: "science", chapter: "Life Processes", type: "lecture-notes",
  title: "Life Processes — Lecture Notes",
  file: "pdfs/class-10/science/life-processes-lecture-notes.pdf",
  description: "Lecture notes for the chapter.",
  year: "", status: "available"
},
```
4. Refresh the page. The card appears under Class 10 → Science → Life Processes, in the search results,
   in the Lecture notes section and in the PDF library list.
Types: `short-notes, detailed-notes, lecture-notes, important-questions, solved-examples, worksheet, summary, formula-sheet, mind-map, revision-checklist`.
Chapters with no entry automatically show "Study material coming soon."

## 6. Add PYQ PDFs
Same as above, using one of these types: `pyq-board`, `pyq-school`, `sample-paper`, `pyq-chapter`.
Add `year`, and optionally `questionType`, `marks`, `difficulty`, so the PYQ filters work.
Label things honestly: do not call practice questions "official CBSE papers", and only upload papers you have the right to share.

## 7. Test View and Download
Run the site on a local server (step 2). Open a card with status "available". **View PDF** opens a new tab;
**Download PDF** saves the file; **Back to materials** scrolls back to the materials list.
When the site runs on a server, any listed PDF that cannot be found is shown as "File not found" instead of a dead button.

## 8. Publish the website online
It is a static site, so any static host works. Free options: GitHub Pages, Netlify, Cloudflare Pages.
Upload the whole GreenClass folder (including `pdfs/`). Check each host's file-size limits for large PDFs.
Test View and Download again on the live address.

## 9. Fix broken PDF links
1. Is the file really inside `pdfs/class-X/subject/`?
2. Does `file:` in `pdf-library.js` match the path and name exactly (lowercase, hyphens, `.pdf`)?
3. Some hosts (Linux) treat `Notes.PDF` and `notes.pdf` as different files.
4. Did you refresh the page (Ctrl+F5)?
5. Open the browser console (F12) for warnings that start with "GreenClass:".

## 10. Update the syllabus for a new academic session
1. Download the new curriculum from https://cbseacademic.nic.in (Curriculum section).
2. In `js/syllabus.js` change `GC_SESSION.session`, `lastChecked`, and the `message`.
3. Update chapter lists. Remove deleted chapters; mark chapters that are optional in your `note` text.
4. Add verified lists to `GC_VERIFIED_LISTS` (e.g. `"10:science"`). Set `status: "verified"` only when **every** list is checked.
5. Update chapter names inside `pdf-library.js` and `quiz.js` if they changed.

## Important limits (please read)
- **Syllabus accuracy:** the lists in this package are starting points, not verified. CBSE released new 2026–27 curricula
  (with a revised scheme for Class 9), so check the official site yourself.
- **No automatic folder scanning:** a static website cannot see new files by itself. That is why `pdf-library.js` exists.
- **Admin helper:** the "Administrator helper" in the PDF library section only writes the code line and lets you preview a
  PDF on your own device. It does **not** upload or publish anything. A real upload feature needs a backend or storage service.
- **Student data:** bookmarks, planner, progress and theme use the browser's localStorage. They stay on that device and
  browser, do not sync across devices, and disappear if the student clears browser data. No personal data is collected.
- **Quiz questions** are samples written for GreenClass, never official CBSE questions.
- **Fonts** load from Google Fonts when online; the site falls back to system fonts offline.
