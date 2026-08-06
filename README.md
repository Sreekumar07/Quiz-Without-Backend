
A online quiz platform built with **HTML, CSS, and vanilla JavaScript**.  
It(can) run entirely on **GitHub Pages or other Frontend Hosting Platforms** – no backend, no database, no server‑side code.  
Update a single `json` file to launch a new quiz every day.

---

## Live Demo

The sample quiz demo is available at:  [Click Here](https://harishdevlab.github.io/Quiz-Without-Backend/)
---

## Features

### Dynamic & Automatic
- **No front‑end changes needed** – just update `data/quiz.json`.
- Supports **1 to 1000+ questions** without any code modifications.
- Automatically detects a new quiz via `quizId` and clears all previous progress.
- Fresh session created automatically for each new quiz.

### Accurate Timer & Persistence
- Timer starts **only when you click “Start Quiz”**.
- **Survives browser close, refresh, or device restart** – timer continues from where it stopped.
- Auto‑submits when time runs out.

### Auto‑Save Progress
- Every selected answer is instantly saved to `localStorage`.
- Restores **current question, answers, remaining time, palette state, and progress** after a refresh.
- Never lose your work, even if you accidentally close the browser.

### Question Palette & Navigation
- Interactive palette with colour codes:
  - **Gray** – Not visited  
  - **Yellow** – Visited  
  - **Green** – Answered  
  - **Highlighted border** – Current question
- Smooth navigation: **Previous / Next**, **jump via palette**, and **keyboard shortcuts** (arrow keys, A/B/C/D for options).
- Real‑time progress bar showing answered count and percentage.

### Review & Submit
- Review screen shows all questions, their status (Answered / Not Answered), and remaining time.
- Jump directly to any question from the review table.
- Manual submission with a final confirmation to prevent accidental clicks.


### Advanced Formatting (Markdown)
- Question text supports a rich subset of Markdown:
  - **Bold**, *italic*, `inline code`, headings, lists, links, images.
  - **Tables**.
  - **Code blocks** with syntax highlighting.
- See the [sample quiz JSON](https://github.com/HarishDevLab/Quiz-Without-Backend/blob/main/data/quiz.json) for examples.

### Zero Dependencies(for now, may be included in future)
- No frameworks, no libraries, no build tools.
- Pure HTML5, CSS3, ES6+ JavaScript.

## `quiz.json` Format (Complete Reference)

```json
{
  "schemaVersion": "1.0",
  "quizId": "unique-quiz-id-2026-08",
  "title": "Quiz",
  "description": "A short description shown on the instruction page.",
  "duration": 15,
  "startTime": "2026-08-05T00:00:00.000Z",
  "endTime": "2027-12-31T23:59:59.000Z",
  "passingMarks": 40,
  "shuffleQuestions": true,
  "shuffleOptions": true,
  "showCorrectAnswers": false,
  "negativeMarking": 0.25,
  "questions": [
    {
      "id": "q1",
      "question": "What is 2 + 2?",
      "image": "",
      "options": ["3", "4", "5", "6"],
      "correct": 1
    }
  ]
}

```

### Field Descriptions

| Field | Type | Description |
| :--- | :--- | :--- |
| `schemaVersion` | `string` | Version of the JSON structure (currently "1.0"). |
| `quizId` | `string` | Unique ID for the quiz. Changing this triggers a fresh session. Use a different ID for each new quiz. |
| `title` | `string` | Title of the quiz (shown on instruction and result pages). |
| `description` | `string` | Brief description (optional). |
| `duration` | `number` | Quiz duration in minutes. |
| `startTime` | `string` (ISO 8601) | Quiz becomes available after this time. (Before this, a “not started” message is shown.) |
| `endTime` | `string` (ISO 8601) | Quiz is no longer accessible after this time. (After this, a “quiz ended” message appears.) |
| `passingMarks` | `number` | Percentage required to pass (e.g., 40 means 40%). |
| `shuffleQuestions` | `boolean` | If true, question order is randomised per student. |
| `shuffleOptions` | `boolean` | If true, options order is randomised per question. |
| `showCorrectAnswers` | `boolean` | (Reserved – currently not used, but can be implemented to show correct answers after submission.) |
| `negativeMarking` | `number` | Penalty per wrong answer (e.g., 0.25 deducts 0.25 marks). Set to 0 for no negative marking. |
| `questions` | `array` | Array of question objects (see details below). |

---

### Question Object Fields

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | `string` | Unique identifier for the question (e.g., `"q1"`). |
| `question` | `string` | The question text. Supports full Markdown formatting. |
| `image` | `string` | Optional URL of an image to display with the question (can be empty `""`). |
| `options` | `array of strings` | Exactly 4 options representing choices A, B, C, and D. |
| `correct` | `number` | Index of the correct option (0‑based: `0` = first option). |

---

### Markdown Support in Questions

The `question` field natively renders Markdown. You can format text using the following styles:

* **Bold**: `**text**` or `__text__`
* **Italic**: `*text*` or `_text_`
* **Inline code**: `` `code` ``
* **Code blocks**: 
  ```text
  python
  print("hello")
  ```
* **Tables**:
  ```text

  | Header 1 | Header 2 |
  |----------|----------|
  | Cell 1   | Cell 2   |
  ```
* **Images**: `![alt text](image_url)`
* **Unordered lists**: `- item` or `* item`
* **Headings**: `#`, `##`, `###`
* **Links**: `[text](url)`

---

### Full JSON Example: [REFER THIS...](https://github.com/HarishDevLab/Quiz-Without-Backend/blob/main/data/quiz.json)

