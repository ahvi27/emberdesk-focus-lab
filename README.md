# EmberDesk Focus Lab ✦

A personal study dashboard built with HTML, CSS, and vanilla JavaScript.

Manage tasks, run focused work sessions, and track your daily progress
without creating an account.

## What's New in Version 2

- Custom focus and break durations
- Daily focus-session goal
- Daily goal progress bar
- Task priorities: high, medium, and low
- Task search combined with completion filters
- Automatic task sorting by completion status and priority
- Timer recovery after refreshing the page
- Accurate focus-minute totals for custom session lengths
- Automatic migration of saved Version 1 tasks and statistics

## Features

### Focus Timer

- Start, pause, resume, and reset
- Separate focus and break modes
- Custom focus duration from 1 to 180 minutes
- Custom break duration from 1 to 60 minutes
- Session progress bar
- Remaining time displayed in the browser tab while running
- Saved running or paused timer state

### Task Board

- Add tasks up to 140 characters long
- Assign a priority when creating a task
- Mark tasks as completed
- Delete individual tasks
- Clear completed tasks
- Search task text
- Filter all, active, or completed tasks

Active tasks appear before completed tasks. Within each group,
high-priority tasks appear first.

### Daily Progress

- Completed focus-session count
- Total completed focus minutes
- Custom daily session goal from 1 to 30
- Goal progress indicator
- Daily statistics reset using the browser's local calendar date

### Appearance

- Light and dark themes
- Responsive mobile and desktop layouts
- Daily focus suggestions
- Keyboard focus indicators
- Accessible labels and status messages

## Technology

- HTML5
- CSS3
- Vanilla JavaScript
- Browser localStorage

No frameworks, external assets, dependencies, or build tools are required.

## Project Structure

```text
emberdesk-focus-lab/
├── index.html
└── README.md
```

## Run Locally

Download the files into the same folder.

You can open `index.html` directly, or serve the project with Python:

```bash
python3 -m http.server 8000
```

Open:

```text
http://localhost:8000
```

Using a local server provides more consistent browser storage behavior
than opening the file directly.

## How to Use

1. Add a task and choose its priority.
2. Select Focus mode.
3. Click Start session.
4. Pause and resume when needed.
5. Complete a session to add it to your daily statistics.
6. Switch to Break mode for a rest period.
7. Mark completed tasks on the task board.

Open Customize your workspace to change timer lengths or your daily goal.

Saving settings resets the current timer. Switching timer modes also
resets the current timer.

## Timer and Statistics Rules

- Only fully completed focus sessions count toward statistics.
- Break sessions do not add focus minutes.
- Paused or reset sessions do not add focus minutes.
- Each completed focus session contributes its actual configured duration.
- Reloading restores the saved timer.
- A running timer continues to use its saved deadline after a reload.
- If the browser suspends or closes the page, elapsed time is reconciled
  when the page becomes active again.
- Sessions are credited to the local day when completion is processed.
- Timers do not automatically start the next session.

For example, completing a 40-minute focus session adds one session and
40 minutes to today's statistics.

## Saved Data

The app stores the following in localStorage:

- Tasks, priorities, and completion status
- Theme preference
- Timer durations and daily goal
- Daily statistics
- Current timer state

Version 2 uses this storage key:

```text
emberdesk-focus-lab-v2
```

If Version 2 data is absent, the app attempts to import Version 1 data
from the same browser origin.

Version 1 session totals are converted to minutes using the original
25-minute focus duration.

## Privacy and Limitations

- No account, backend, analytics, or cloud synchronization
- Data stays in the current browser profile and origin
- Clearing browser storage removes saved progress
- Private browsing or browser restrictions may prevent saving
- Storage failures are reported inside the dashboard
- Multiple open tabs do not synchronize and can overwrite saved state
- Manual system-clock changes may affect the timer
- No sound alerts or operating-system notifications are included
- Deleted tasks cannot be restored

## Customization

Edit the CSS variables in `:root` and `body.light` to change the theme.

Update the `tips` array to customize focus suggestions.

Default settings are defined in the JavaScript settings initialization:

```javascript
const settings = {
  focus: validInt(raw.settings?.focus, 1, 180, 25),
  break: validInt(raw.settings?.break, 1, 60, 5),
  goal: validInt(raw.settings?.goal, 1, 30, 4)
};
```

Saved user settings take precedence over these defaults.

## Deployment

The project can be hosted as a static website.

Publish `index.html` at the root of your static hosting directory.
No installation or build command is needed.

## Manual Check Suggestions

- Add tasks with different priorities and inspect their order.
- Combine a search with the Active or Completed filter.
- Complete tasks and clear them.
- Change the theme and refresh.
- Set a one-minute focus session and let it finish.
- Confirm that one session and one minute are added.
- Start a timer, refresh, and confirm it continues.
- Pause a timer, refresh, and confirm it remains paused.
- Change timer settings and confirm the timer resets.

## Future Improvements

- Editable task priorities
- Task deadlines
- Weekly progress history
- JSON export and import
- Optional completion sounds
- Multi-tab synchronization
