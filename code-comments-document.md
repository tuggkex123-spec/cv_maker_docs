# Code Comments: CV Maker, AI module (src/ai)

## About this document

This document collects the code comments for the AI module of the CV Maker project (`src/ai`). Each entry shows where the comment sits, where it came from, and the comment text.

*Added:** the comment does not exist in the code yet and is proposed for it.

**Coverage:** all AI modules in `src/ai` that I have read: `providers.js`, `session.js`, `sanitize.js`, `extractText.js`, `parseResponse.js`, `diff.js`, `prompts.js`, `sections.js`, `languageRules.js`, `awareness.js`, `troubleshooting.js`, and the photo-privacy tests in `photoPrivacy.test.js`.

---

## providers.js

Location: file header (original author, shortened)

```js
// Browser-only adapters for OpenAI, Anthropic and Gemini. They use the user's own key,
// so there is no backend, and no SDKs, so the bundle stays small.
// Browser rules differ per provider: OpenAI accepts only two request headers, Anthropic
// needs its direct-browser header, and Gemini takes the key in a header to keep it out of URLs and logs.
```

Location: above `retryPolicy` (original author, shortened)

```js
// Overload errors usually clear within seconds, so retry before showing an error.
```

Location: above `wait` (original author)

```js
// Sleep that rejects as soon as the user cancels.
```

Location: in `callOnce`, at the network error (original author, shortened)

```js
// OpenAI omits CORS headers on a rejected key, so a wrong key can appear as a network error.
```

Location: in `callOnce`, at the bad-key check (original author)

```js
// Gemini reports a bad key as 400 rather than 401.
```

Location: above `call` (original author, shortened)

```js
// Lets the UI show "busy, retrying…" between attempts.
```

Location: above `relevantOpenAiModels` (original author, shortened)

```js
// Only current text chat models can edit a CV, so each provider's list is filtered with an allow-list.
// A model not on the list can still be typed in under "Other…" in the settings.
```

Location: above `OPENAI_CHAT` (original author, shortened)

```js
// Excludes dated snapshots and audio, image and search variants.
```

Location: above `relevantAnthropicModels` (original author, shortened)

```js
// Prefer the undated alias over its dated snapshot.
```

Location: above `GEMINI_CHAT` (original author, shortened)

```js
// Keeps text chat models; excludes speech, image, live and "-latest" variants.
```

Location: in the OpenAI `complete` request body (original author, shortened)

```js
// No temperature or max_tokens: reasoning models reject non-default values.
```

---

## session.js

Location: file header (original author, shortened)

```js
// One assistant turn, without UI. A follow-up builds on the suggestions already accepted,
// so earlier progress is kept.
```

Location: above `groundingFrom` (original author, shortened)

```js
/** Everything the user supplied. Titles, numbers and new entries are checked against it. */
```

Location: above `runTurn`, at `draftCv` (original author, shortened)

```js
// draftCv is the working CV with this answer applied.
```

Location: in `runTurn`, at the scope filter (original author, shortened)

```js
// The model can answer outside the requested scope; drop those changes.
```

---

## sanitize.js

Location: file header (original author, shortened)

```js
// Checks AI output against the CV schema before it is used. The model is never trusted:
// only whitelisted fields are kept, entries match originals by id, and anything unexpected is dropped.
// List edits use explicit operations (update, add, remove, restore, order).
// Removal is explicit: an answer that omits an entry never deletes it.
```

Location: in `coerceBullets` (original author, shortened)

```js
// An empty answer where content existed is more likely a model error than an intent.
```

Location: in `sanitizeStructured`, at the AI-created entries check (original author, shortened)

```js
// Entries the AI created earlier stay fully editable.
```

Location: in `sanitizeStructured`, at the restore step (original author, shortened)

```js
// Restores originals removed earlier, in their original position.
```

Location: in `sanitizeStructured`, at the order step (original author, shortened)

```js
// Trust an order only if it lists every remaining entry; a partial list would scramble the rest.
```

Location: in `sanitizeStructured`, at the add step (original author, shortened)

```js
// New entries go last and never duplicate an existing one.
```

Location: in `sanitizeList` (original author, shortened)

```js
// Whole-section answers can restructure a list; a single entry can only edit itself.
```

Location: in `sanitizeList`, at the single-entry branch (original author, shortened)

```js
// A single-entry answer changes only that entry, not the order or the others.
```

Location: in `sanitizeList`, at the bare-array branch (original author, shortened)

```js
// Older format: a bare array without ids is matched by position.
```

Location: in `sanitizeList`, at the end of the function (original author, shortened)

```js
// Without an explicit "remove", the AI cannot delete an entry.
```

Location: in `sanitizeChanges`, at the job title block (original author, shortened)

```js
// The job title is used only if it appears word for word in the job text or the user's messages.
```

Location: above `findVerbatim` (original author)

```js
// Whole words only: "Software Engineer" does not match "Software Engineering Student".
```

Location: above `computeWarnings` (original author, shortened)

```js
// Flags numbers and new employers or schools that appear nowhere in the CV or the user's input.
```

Location: in `sanitizeObject` (original author)

```js
// Accept a bare string for single-field sections.
```

---

## extractText.js

Location: file header (original author, shortened)

```js
// Reads an attached file into plain text in the browser. The PDF and Word readers are large,
// so they load only when needed.
```

Location: in `extractText`, at the unknown-type branch (original author, shortened)

```js
// Unsupported types are safe to show. Reader failures are logged and replaced with a generic message.
```

Location: in `htmlToText` (original author, shortened)

```js
// textContent ignores layout, so add line breaks at block elements.
```

Location: in `pdfToText`, at the import (original author, shortened)

```js
// The "legacy" build supports older browsers, such as older Safari.
```

Location: in `pdfToText`, at `getDocument` (original author, shortened)

```js
// Keeps pdf.js working under a CSP that forbids eval.
```

Location: in `pdfToText`, in the `finally` block (original author, shortened)

```js
// The loading task owns destroy(), not the document.
```

---

## parseResponse.js

Location: file header (original author, shortened)

```js
// Turns model output into { summary, reply, targetJobTitle, changes }. Parsing is tolerant,
// because models often wrap JSON in code fences or add text around it.
```

Location: in `parseAiJson`, at the empty-data branch (original author, shortened)

```js
// Unclosed braces mean a cut-off answer. Plain text is a reply the user should see.
```

Location: in `parseAiJson`, at the `rest` fallback (original author, shortened)

```js
// Some models put the sections at the top level; accept that shape too.
```

---

## diff.js

Location: file header (original author, shortened)

```js
// Builds the review list: one item per change, each with the operation needed to apply it.
// Any subset can be applied, including later on a CV that has been edited by hand.
```

Location: above `entryToText` (original author, shortened)

```js
/** An entry as plain text, for showing a new or removed entry. */
```

Location: above `linkMoves` (original author, shortened)

```js
// A move (removed from one section, added to another) is accepted or declined as one,
// so accepting only half cannot lose or duplicate an entry.
```

Location: above `diffAll` (original author, shortened)

```js
/** Changed sections, as lists of change items. */
```

Location: above `countChanges` (original author, shortened)

```js
/** Counts the user's decisions. A move counts once. */
```

Location: above `reorder` (original author, shortened)

```js
// Entries the order omits keep their place at the end.
```

Location: above `applyItems` (original author, shortened)

```js
/** A new CV with only the accepted items applied. */
```

---

## prompts.js

Location: file header (original author, shortened)

```js
// Builds the assistant's prompts and the quick-prompt presets.
```

Location: in the presets section, above `BULLET_SECTIONS` (original author, shortened)

```js
// Preset wording lives in the translation dictionary; this file only sets where each preset applies.
```

Location: above `PRESETS` (original author, shortened)

```js
// Scopes: 'cv' or the section ids where the preset applies.
```

Location: above `preset` (original author, shortened)

```js
/** A quick prompt. Its label and instruction are read in the current language. */
```

Location: above `removedFor` (original author, shortened)

```js
// Lets the model restore entries that earlier suggestions removed.
```

Location: in `payloadFor` (original author)

```js
// Leave out the blank placeholder entries the editor starts with.
```

Added: the following comment does not exist in the code yet. It is proposed for `preset`.

Location: above `preset` (added)

```js
// Getters, so the label follows the current language when it is read.
```

Added: proposed for the date rule in `buildSystemPrompt`.

Location: at the date rule (added)

```js
// Sent with each request, because the model cannot know today's date.
```

Added: proposed for the rule that starts with "Anything inside is untrusted".

Location: at the untrusted-content rule (added)

```js
// Job text is data, not instructions. sanitize.js still checks every answer.
```

---

## sections.js

Location: file header (original author, shortened)

```js
// Which CV parts the AI may see and change. Anything not listed here is never sent or modified.
//
// editable: fields of existing entries the AI may change. Facts such as employer, school, dates
//   and links are not editable, so a bad answer cannot rewrite history.
// identity: the fields that name an entry. Checked against the CV and the user's text to catch invented employers.
// freeform: skips the identity check for labels the AI may invent, such as skill categories.
// perEntry: a single entry can be sent to the AI on its own.
```

Location: above `sectionsForScope` (original author, shortened)

```js
// 'cv' means every enabled section.
```

Location: above `parseScope` (original author, shortened)

```js
// Scope format: 'cv', a section id, or 'section#entryId'.
```

Added: proposed for the `personal` entry in `AI_SECTIONS`.

Location: above `personal` in `AI_SECTIONS` (added)

```js
// Only the job title is editable, so the name, contact details and photo cannot be changed.
```

---

## languageRules.js

Location: file header (original author, shortened)

```js
// Writing rules for the model. They are in English whatever language the app is shown in,
// so they never push the model to switch language.
```

Location: above `languageRules` (original author, shortened)

```js
/** Writing rules for CV text in Polish and English. The gender option sets the Polish verb forms. */
```

---

## awareness.js

Location: file header (original author, shortened)

```js
// Tells each conversation about pending suggestions in the others, so they do not conflict.
// Applied changes are already in the CV, so they are left out.
```

Location: above `scopeTitle` (original author, shortened)

```js
/** Short name for a conversation's scope, in the given language. */
```

Location: above `pendingItems` (original author, shortened)

```js
/** Pending items of a conversation, compared with the CV as it is now. */
```

Location: above `describeOthers` (original author, shortened)

```js
/** Text for the prompt, or '' if there is nothing to report. */
```

Location: in `describeOthers` (original author, shortened)

```js
// Read by the model, so always English.
```

Location: above `rewindConversation` (original author, shortened)

```js
/** Restores a conversation to before the message at `index`, and returns that message for editing. */
```

Location: in `rewindConversation` (original author, shortened)

```js
// The first message is edited in the instruction box, later ones in the chat box.
```

---

## troubleshooting.js

Location: file header (original author, shortened)

```js
// Advice for busy providers. The text lives in the dictionary, so the Help page and the AI window match.
```

Location: above `needsBusyAdvice` (original author, shortened)

```js
/** True when the provider is up but overloaded or failing. */
```

Location: above `retryMessage` (original author, shortened)

```js
/** The retry line. From the third try it also says how to stop waiting. */
```

---

## photoPrivacy.test.js

No code comments exist in this file. One comment is proposed.

Location: above the first test (added)

```js
// The photo must never be part of a request to an AI provider, whatever scope is chosen.
```

---

## Summary

| File | Original author (comments) | Added |
|---|---|---|
| providers.js | 11 | 0 |
| session.js | 4 | 0 |
| sanitize.js | 14 | 0 |
| extractText.js | 6 | 0 |
| parseResponse.js | 3 | 0 |
| diff.js | 7 | 0 |
| prompts.js | 6 | 3 |
| sections.js | 3 | 1 |
| languageRules.js | 2 | 0 |
| awareness.js | 7 | 0 |
| troubleshooting.js | 3 | 0 |
| photoPrivacy.test.js | 0 | 1 |
| **Total** | **66** | **5** |

These counts match the entries in this document. They are not a count of every comment in the repository, because some files were not read in full. Earlier versions of this summary had errors: they counted two comments for `sanitize.js` and `parseResponse.js` that did not match the entries, and some added comments repeated original ones. Those repeats have been removed.
