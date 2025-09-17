# Overview of the Declarative Agent template

With the declarative agent, you can build a custom version of Copilot that can be used for specific scenarios, such as for specialized knowledge, implementing specific processes, or simply to save time by reusing a set of AI prompts. For example, a grocery shopping Copilot declarative agent can be used to create a grocery list based on a meal plan that you send to Copilot.

## What's included in the template

| Folder       | Contents                                                                                 |
| ------------ | ---------------------------------------------------------------------------------------- |
| `.vscode`    | VSCode files for debugging                                                               |
| `appPackage` | Templates for the application manifest, the GPT manifest and the API specification |
| `env`        | Environment files                                                                        |

The following files can be customized and demonstrate an example implementation to get you started.

| File                               | Contents                                                                     |
| ---------------------------------- | ---------------------------------------------------------------------------- |
| `appPackage/declarativeAgent.json` | Define the behaviour and configurations of the declarative agent.            |
| `appPackage/manifest.json`         | application manifest that defines metadata for your declarative agent. |

The following are Microsoft 365 Agents Toolkit specific project files. You can [visit a complete guide on Github](https://github.com/OfficeDev/TeamsFx/wiki/Teams-Toolkit-Visual-Studio-Code-v5-Guide#overview) to understand how Microsoft 365 Agents Toolkit works.

| File           | Contents                                                                                                                                  |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `m365agents.yml` | This is the main Microsoft 365 Agents Toolkit project file. The project file defines two primary things: Properties and configuration Stage definitions. |

## Agent behavior and configuration

This template includes a declarative agent configured to act as a Chief of Staff assistant for running projects. Key behavior and defaults:

- Role: Chief of Staff — the agent searches Microsoft 365 content and prepares concise, executive-focused weekly summaries for active projects.
- Enabled knowledge sources (capabilities): Email, Teams messages, OneDrive & SharePoint, Meetings, and Code Interpreter. By default these are broad (not scoped) so the agent searches all accessible content the signed-in user can see. The `Meetings` capability enables the agent to include calendar/meeting items and meeting content in summaries; `CodeInterpreter` enables programmatic generation tasks (for example, producing files such as PPTX via the built-in interpreter).
- Default timeframe: last 7 days (confirmable by user).
- Summary contents: per-project snapshot (health), mandatory updates (with links), action items (Action | Owner | Due date | Status | Source), prioritized to‑do tasks to focus on (top 3), risks & blockers, open decisions, and next steps with owners.
- Conversation starters: the manifest includes helpful starters such as "Weekly project summary", "Show action items only", "Top to-do tasks", and a new starter: "Generate PPT summary (last week)". The `appPackage/instruction.txt` file contains detailed guidance the agent follows for tone, formatting, clarifying questions, and privacy rules. A new scenario was added to `instruction.txt` describing how to generate a PowerPoint presentation programmatically (one slide per project, speaker notes, action-items table) via the built-in Code Interpreter and how to save the output to OneDrive.

## Recent changes (2025-09-17)

- Added capabilities: `Meetings` (include calendar and meeting content) and `CodeInterpreter` (enable programmatic code execution for tasks such as file generation).
- Added a conversation starter: "Generate PPT summary (last week)" that triggers a flow to produce a PowerPoint summary of the last week's updates.
- Added a new scenario in `appPackage/instruction.txt` that instructs the agent to use the built-in Code Interpreter to assemble and generate a PPTX file with one slide per project, speaker notes, and an action-items table. The scenario also instructs the agent to save the resulting PPTX to OneDrive (suggested path: `/Documents/ProjectReports/WeekSummaries/`) and return a download link.

See `appPackage/declarativeAgent.json` for the updated capabilities and conversation starter, and `appPackage/instruction.txt` for the full PPT generation scenario details.

## Addition information and references

- [Declarative agents for Microsoft 365](https://aka.ms/teams-toolkit-declarative-agent)
