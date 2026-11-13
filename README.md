# Student Chatbot (local version, no Supabase)

NOTE: This is NOT the original Lovable code. It was rebuilt from the project description with
Vite + React + TypeScript + Tailwind + React Router. Supabase has been removed.

## Run in VS Code
1. Install Node.js 18+.
2. `npm install`
3. `npm run dev`
4. Open http://localhost:5173/

No account, keys or .env file are needed.

## How data is saved
All data (accounts, check-ins, messages, alerts, settings, notifications) is saved in the browser's localStorage
(see `src/store.ts`). It stays in this one browser on this one computer. Clearing browser data erases it.
To see both sides, create one student account and one counsellor account (sign-up has a role choice)
and use Sign out / Sign in to switch.

## Status
Implemented: sign-up/login (local), student check-ins + history, support-indicator results,
messages + counsellor replies and status updates, chatbot with keyword risk check, alerts
(medium/high, high = urgent), counsellor dashboard, alert threshold setting in the account menu,
role-specific notification preferences, and a role-targeted in-app notification center with unread counts.
Student check-ins/messages notify counsellors; counsellor replies and follow-up updates notify
the relevant student. Notifications can be opened from the bell menu and marked as read.
In-app notification sounds can be enabled or muted in Settings and previewed with Test sound.

The check-in analyzes the student's written thoughts using local phrase patterns and
common wording variations to suggest an initial support level. This is not a diagnosis or
a reliable measure of mental health. Older check-ins may still show mood and intensity
saved before the text-only flow.
The built-in chat reply writer is a short local script, not an AI service, and chat messages
are not saved after leaving the page. A high-risk result asks the student to contact a
trusted adult or appropriate local emergency support; the companion is not a crisis service
or a replacement for a professional counsellor.

Changed from the original idea:
- Passwords are only hashed in the browser. This is demo-level, not real security.
- Anyone can choose "counsellor" at sign-up (demo only).
- No email verification (it needs a server).
- Chatbot replies come from a small built-in script (`src/bot.ts`), not an AI service.

Not implemented: weekly PDF report, per-mood thresholds, browser/OS push notifications,
or a permission model for counsellor access to individual wellbeing notes. Notifications
are stored locally in this browser and do not sync across devices. The counsellor
activity view shows mood and intensity only; alert details can include the student's note.
