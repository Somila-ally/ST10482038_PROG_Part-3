# ST10482038_PROG_Part-3

Overview

AEGIS Cyber Sentinel is a WPF (.NET 10) desktop application that provides:
- A friendly chatbot for cybersecurity awareness (keyword + fuzzy matching)
- A Task Assistant with local persistence (SQLite) and UI for add/complete/delete
- An interactive cybersecurity quiz with explanations and scoring
- Activity logging, message history export, and a small audio greeting utility
AEGIS Cyber Sentinel — Cybersecurity Awareness Bot

Quick Start

Prerequisites
- Windows with .NET 10 SDK installed
- Visual Studio 2022/2026 or the dotnet CLI
- Git (only required if using the included commit/tag helper script)

Build and run
1. Open CYBERSECURITYBOT.sln in Visual Studio and restore packages.
2. Build and run the CYBERSECURITYBOT project.
   - Or from the repository root: dotnet build && dotnet run --project CYBERSECURITYBOT/CYBERSECURITYBOT.csproj

First run
- Enter your name in the overlay; this is used in the chat and message history.

Key features (mapping to rubric)
- Chatbot: SupportStubs.cs — keyword/synonym map and fuzzy heuristics (Keyword Detection / NLP)
- Task Assistant: SupportStubs.cs (TaskAssistant) and Data/TaskRepository.cs (SQLite persistence) (Task Assistant, DB connection)
- Quiz: SupportStubs.cs (QuizEngine) — 15+ curated cybersecurity questions with per-answer feedback (Cybersecurity Quiz)
- Activity Log: ActivityLogger & UI (MainWindow.xaml / MainWindow.xaml.cs) with pageable "Show more" (Log Activity)
- Release helper: scripts/create_commits_tags.ps1 — creates example commits and annotated tags (GitHub Repository)

Task persistence and database
- Tasks persist to tasks.db (AppContext.BaseDirectory). The app falls back to in-memory storage if DB access fails.
- To reset tasks, close the app and delete tasks.db in the application directory.

Using the release helper script (example commits and tags)
- Preview (dry-run): pwsh .\scripts\create_commits_tags.ps1
- Execute (apply changes): pwsh .\scripts\create_commits_tags.ps1 -Execute
- The script now verifies git availability and avoids creating empty commits; it does not push to remotes. After running, push manually:
  git push origin <branch> && git push --tags

Repository and presentation links (placeholders — replace with real links)
- GitHub repository: https://github.com/<your-user>/<your-repo>  <-- replace with your repository URL
- Presentation video (YouTube): https://youtu.be/<your-video-id>  <-- replace with your video link

Screenshots and media
- Add screenshots to a folder like docs/screenshots/ and reference them in this README. Example markdown to include a screenshot:
  ![Main screen](docs/screenshots/main-window.png)
- Suggested captures: main chat view, tasks view, quiz result screen, activity log export dialog

Rubric checklist (code-related items)
1. README / Repo setup (5): README contains setup, usage, and script docs. Replace placeholders above with real links to score full marks.
2. GitHub Repository (10): scripts/create_commits_tags.ps1 helps produce commits/tags; run it on a clean branch and push tags to demonstrate releases.
3. Task Assistant (15): Add/Complete/Delete + suggested tasks + DB persistence present. To reach full score, add reminders/due-dates (optional enhancement).
4. Database connection (15): Data/TaskRepository.cs implements SQLite CRUD. Ensure tasks.db is present and not locked on startup; read-after-write verification is performed by TaskAssistant initialization.
5. Cybersecurity Quiz (15): 15+ curated questions with feedback are implemented in SupportStubs.cs.
6. Keyword Detection / NLP (15): Basic rule-based keywords + fuzzy matching implemented; expand synonyms or add fuzzy distance for stronger results.
7. Log Activity (10): ActivityLogger and UI with Show more button implemented; export and clear functionality available.
8. Integration / Cohesion (10): UI components are integrated; some catch blocks suppress errors — consider surfacing errors to the user for production quality.

Developer notes
- Task persistence uses Microsoft.Data.Sqlite via Data/TaskRepository.cs.
- Chatbot and quiz code are in CYBERSECURITYBOT/SupportStubs.cs. UI wiring is in MainWindow.xaml and MainWindow.xaml.cs.
- Message history file location: %LOCALAPPDATA%\AEGIS\message_history.txt (fallback to AppContext.BaseDirectory if needed).

How to demonstrate (suggested steps for submission)
1. Run the app and demonstrate chat, adding/completing tasks, and running the quiz.
2. Run the release helper script in dry-run mode to preview commits/tags; then run with -Execute on a throwaway branch and push tags for GitHub release evidence.
3. Export message history and activity log to show persistent records.
4. Add your GitHub repo link and video link above.

Contributing
- Please file issues and pull requests via GitHub and follow standard .NET contribution guidelines.

License
- Add a LICENSE file in the repo root (e.g., MIT) or replace with your preferred license. A sample MIT license is included as LICENSE if present.

Releases
- The included script can produce CHANGELOG.md and VERSION.txt entries to support demonstrating releases and tags.
