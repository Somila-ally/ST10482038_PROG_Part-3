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
https://youtu.be/V_t-_wznNH4

