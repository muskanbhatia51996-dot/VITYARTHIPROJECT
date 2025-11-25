Simple Command-Line Task Manager (SCTM)

Problem Statement
In fast-paced work environments, individuals often rely on quick, temporary notes (like digital sticky notes or ephemeral terminal output) to track tasks.
This leads to data impermanence and the cognitive burden of recreating lists or migrating data. 
Existing full-featured software (GUIs, web apps) introduces too much friction, requiring accounts, network access, or complex navigation that defeats the purpose of rapid note-taking.
The core problem is the lack of a lightweight, persistent, and low-friction tool that combines the speed of a Command-Line Interface (CLI) with the reliability of automated data storage.

Scope of the Project
The scope of the Simple Command-Line Task Manager (SCTM) is strictly limited to the core functionality of task management and persistence within a local, single-user environment.
In Scope:
Adding, Viewing, and Marking tasks as Complete.
Automated saving and loading of the task list to a local JSON file.
Basic input validation and error handling to prevent crashes.

Out of Scope (Future Work/Enhancements):
Multi-user support, authentication, or network capabilities.
Graphical User Interface (GUI).
Advanced features like prioritization, filtering, or task deletion.
Integration with external calendars or services.

Target Users
The primary target audience for the SCTM is defined by their need for speed and their working environment:

Developers and IT Professionals: Individuals who spend most of their time working within a terminal or command prompt and require a tool that aligns with their workflow.
Students and Researchers: Users needing a simple, distraction-free way to maintain project checklists or reading lists without switching context to complex applications.
Users Requiring Local Control: Individuals who prefer an offline tool where their data is stored locally and securely, rather than in the cloud.

High-Level Features
The system provides a clear and fast set of capabilities:
Frictionless Entry: Rapid task addition via a simple CLI menu option.
Persistent Storage: Automatic handling of task data using JSON serialization, ensuring tasks are retained across sessions.
Status Tracking: Clear visual distinction between [PENDING] and [DONE] tasks.
Reliable Operation: Robust error handling that guarantees the application does not crash due to typical user mistakes or missing save files.
