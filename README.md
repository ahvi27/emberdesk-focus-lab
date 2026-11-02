# EmberDesk Focus Lab ✦

A responsive study dashboard built with HTML, CSS, and vanilla JavaScript.

Organize your tasks, complete focused study sessions, and track your daily progress in one workspace.

## Features

- **Focus timer:** 25-minute sessions with start, pause, and reset controls.
- **Break timer:** Switch to a 5-minute rest period.
- **Session progress:** Visual progress bar for the current timer.
- **Task manager:** Add, complete, and delete tasks.
- **Task filters:** View all, active, or completed tasks.
- **Bulk cleanup:** Clear completed tasks.
- **Daily statistics:** Track completed focus sessions and focus minutes.
- **Theme switch:** Choose a light or dark appearance.
- **Automatic saving:** Tasks, theme, and daily statistics use localStorage.
- **Responsive layout:** Works on mobile and desktop screens.
- **Daily focus cues:** Simple suggestions to support your study routine.

## Technologies

- HTML5
- CSS3
- Vanilla JavaScript
- Browser localStorage

No frameworks, packages, or build tools are required.

## Project Structure

```text
emberdesk-focus-lab/
├── index.html
└── README.md
```

## Getting Started

Download the project and open `index.html` in your browser.

For a consistent local development setup, run a Python server from the project folder:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## How to Use

1. Add the tasks you want to complete.
2. Select **Focus · 25m**.
3. Click **Start session**.
4. Pause or reset the timer when needed.
5. After completing a focus session, select **Break · 5m**.
6. Mark finished tasks as completed.
7. Review your daily sessions and focus minutes.

Changing timer modes resets the current timer.

## Data and Privacy

The application saves these items in your browser:

- Tasks and completion status
- Theme preference
- Today's completed focus-session count

There is no backend, account system, or cross-device synchronization.

Clearing browser storage removes saved data. Storage behavior when opening
the HTML file directly can vary by browser; using a local server is recommended.

## Timer Behavior

- The timer uses a clock deadline to account for background-tab delays.
- A completed focus session adds 25 minutes to today's total.
- Paused or reset sessions do not count as completed sessions.
- Daily statistics reset on the next local calendar day.
- Tasks remain saved across days.
- Reloading or closing the page resets the timer.
- If the browser suspends the page, completion is processed when it resumes.
- Sessions are counted on the day their completion is processed.
- No sound or system notification is included.

## Customization

Change session lengths in `index.html`:

```javascript
const durations = {
  focus: 25 * 60,
  break: 5 * 60
};
```

If you change the focus duration, also update the timer button labels,
initial display, and daily-minute calculation to match.

Customize the colors through the CSS variables in `:root` and `body.light`.

Edit the `tips` array to add your own study reminders.

## Deployment

Upload `index.html` to any static hosting service.

For GitHub Pages, place the file at the root of the branch configured as
your Pages publishing source.

## Future Ideas

- Custom session durations
- Task priorities and deadlines
- Weekly progress charts
- Optional completion sounds
- Task export and import
- Saved timer state
- Multi-tab synchronization
