# CV Maker reference

## Summary

This page lists the facts about CV Maker: the sections, fields, menu items, file limits, AI settings and error messages. Use it to confirm what a control does or what a limit is. To learn a task, use the [tutorial](tutorial-first-cv.md). To complete one task, use the [how-to guides](how-to.md). To understand the design, read [About CV Maker](concept.md).

## Sections

The **Sections** panel controls which parts of the CV appear. Tick a checkbox to show a section. Drag its handle to change its position.


| Section                          | On by default | Entries                                             |
| -------------------------------- | ------------- | --------------------------------------------------- |
| Profile                          | Yes           | One text block                                      |
| Experience                       | Yes           | Job title, company, dates, bullets                  |
| Projects                         | Yes           | Project entries                                     |
| Education                        | Yes           | School or university, degree, field of study, dates |
| Skills                           | Yes           | Categories with comma-separated items               |
| Languages                        | No            | \[verify the fields\]                               |
| Certifications &amp; Awards      | No            | \[verify the fields\]                               |
| Volunteer &amp; Extracurriculars | No            | \[verify the fields\]                               |
| Custom Section                   | No            | \[verify the fields\]                               |


Personal Info is not in the Sections panel. It appears at the top of the CV. \[verify\]

## Personal Info fields

- **Full Name**
- **Job Title**
- **Phone**
- **Email**
- **Location**: city and country only
- **Links**: add with **+ LinkedIn**, **+ GitHub**, **+ Portfolio** or **+ Other**

## Entry fields

**Education**

- School / University
- Degree
- Field of Study
- Start Date and End Date
- **Currently ongoing**: removes the end date for a degree you still study

**Experience**

- Job title, company and dates
- Bullets, added with **+ Add bullet**

**Skills**

- **Category**: a label, such as *Tools*
- **Items (comma-separated)**: for example, *Python, JavaScript, SQL*
- **+ Add skill category** adds another category

## Entry controls

Each entry has these controls:

- **Move up** and **Move down** change its position within the section.
- **Remove entry** deletes it.

## Templates

- **Classic:** a centred name and contact line. Applicant tracking systems read this layout most easily.
- **With photo:** a photo beside the name and contact details.

## Photos


| Rule                | Value                                                                 |
| ------------------- | --------------------------------------------------------------------- |
| Accepted file types | JPG, PNG, WebP, GIF                                                   |
| Maximum file size   | 15 MB                                                                 |
| Crop                | Square, from the centre                                               |
| Storage             | Your browser only. The app never sends the photo to the AI assistant. |


## CV language

The **CV language** control sets the language of the CV headings. **Same as the app** uses the interface language.

For Polish text, **Gender forms in Polish text** sets the verb forms. The options are **Detect from my text**, masculine and feminine. \[verify the labels\]

## Header and menu


| Control             | Action                               |
| ------------------- | ------------------------------------ |
| **AI**              | Opens the AI assistant               |
| **Undo** / **Redo** | Reverses or repeats a change         |
| **Save PDF**        | Opens the print dialog to save a PDF |
| Sun or moon button  | Switches between light and dark mode |
| **⋯ menu**          | Opens the menu below                 |


**⋯ menu** items:

- **Save backup**: downloads a `.json` file
- **Restore backup**: replaces the CV with a backup file
- **Export as Word (.docx)**: downloads a Word file
- **Save as default CV**: saves the current CV as the default
- **Load default CV**: replaces the CV with the default
- **AI settings &amp; API key**: sets the provider and key
- **Reset all data**: deletes all CV data, the default CV and the AI key from this browser

\[verify the menu labels\]

## Keyboard shortcuts

- **Ctrl+Z** (Windows) or **Cmd+Z** (Mac): Undo
- **Ctrl+Shift+Z** or **Cmd+Shift+Z**: Redo

The shortcuts work only when the editor has focus. \[verify\]

## Files


| File                 | Use                      | Limit                                    |
| -------------------- | ------------------------ | ---------------------------------------- |
| `.json` backup       | Restores a CV in the app | Must come from this app                  |
| PDF                  | AI reference material    | 10 MB. The app reads the first 30 pages. |
| Word (`.docx`)       | AI reference material    | 10 MB                                    |
| Text, Markdown, HTML | AI reference material    | 10 MB                                    |


The app cannot import a PDF or Word file as a CV. Only the `.json` backup restores a CV.

## AI providers


| Provider           | Key source                          |
| ------------------ | ----------------------------------- |
| OpenAI             | platform.openai.com/api-keys        |
| Anthropic (Claude) | console.anthropic.com/settings/keys |
| Google Gemini      | aistudio.google.com/apikey          |


- The app stores the key in your browser.
- Requests go from your browser directly to the provider you chose.
- Each provider has its own key.

## AI protections

The AI assistant cannot change these fields:

- Contact details
- Employers and schools
- Dates of existing entries

The job title must match the job text word for word. The app flags a number, employer or school that does not appear in your CV or your messages.

## Error messages


| Message                                                                 | Meaning                                                     | Action                                   |
| ----------------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------------- |
| *Invalid file: please upload a CV Maker .json backup file*              | The file is not a backup from this app                      | Choose the backup file you saved         |
| *Please choose a JPG, PNG, WebP or GIF picture*                         | The photo type is not supported                             | Choose a supported file type             |
| *That picture is too large*                                             | The photo is over 15 MB                                     | Choose a smaller picture                 |
| *That file couldn't be read as a picture*                               | The file is damaged or is not a picture                     | Choose another file                      |
| *Could not save the default CV: the browser storage is full or blocked* | The browser cannot store the default CV                     | Free up browser storage, or use a backup |
| Authentication error (AI)                                               | The key is wrong or not valid for the provider              | Copy the key again                       |
| Quota error (AI)                                                        | The provider account has no credit or has reached its limit | Check the provider's billing page        |
| Network error (AI)                                                      | The request did not reach the provider                      | Check your connection                    |


## Glossary

- **Backup:** a `.json` file that holds a CV. Restore it to bring the CV back.
- **Default CV:** a saved copy of a CV that you load to start a new one.
- **Entry:** one item in a section, such as one job or one degree.
- **Section:** a part of the CV, such as Experience or Education.
- **Quick prompt:** a preset request for the AI assistant, such as shortening bullets.
- **Suggestion:** a change the AI assistant proposes. You apply or leave out each one.

## FAQ

**Does CV Maker store my CV on a server?**
No. The app stores your CV in your browser. Export a backup to keep a copy.

**Can I use the app without AI?**
Yes. The AI assistant is optional and needs your own key.

**Can I import a PDF CV?**
No. Use the `.json` backup for a CV. Attach a PDF to the AI assistant as reference material.

**Does the AI see my photo?**
No. The photo stays in your browser.

## Related links

- [Tutorial: build your first CV](tutorial-first-cv.md)
- [How-to guides](how-to.md)
- [About CV Maker](concept.md)

