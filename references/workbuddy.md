# Use meeting-minutes in WorkBuddy

This repository contains one portable meeting-minutes skill. Keep its files together when importing or placing it in a project. The workflow uses the tools available in the current host and produces Traditional Chinese by default; request English when needed.

## Package contents

| Path | Role |
|---|---|
| SKILL.md | Shared skill name, trigger description, and meeting-processing workflow |
| references/meeting-domains.md | Construction, renovation, maintenance, procurement, costing, and general-meeting guidance |
| references/workbuddy.md | WorkBuddy setup and runtime guidance |
| agents/openai.yaml | Optional OpenAI-host metadata; the WorkBuddy workflow does not depend on this file |

No API key, server, external account, or executable installer is required by the text-based meeting workflow. Audio transcription is a separate capability, described below.

## Install through WorkBuddy

1. Download this repository using GitHub's **Code → Download ZIP**, or clone it. Extract the download and keep SKILL.md together with the references directory.
2. In WorkBuddy, open **Experts / Skills / Connectors → Skills → Add Skill → Upload Skill** and select the local skill package using the format accepted by your client. Keep the bundled reference files with the skill; importing only SKILL.md would omit them.
3. Locate **meeting-minutes** in the installed-skills list and ensure it is enabled.
4. Start a fresh task and select the skill if necessary. Use the explicit invocation below for the first run.

The official desktop documentation confirms local package upload but does not specify every archive nesting or file-picker variant. This repository has not been imported into a running WorkBuddy client during validation. If your client does not accept the downloaded archive layout, use its accepted local-package format or the documented project method below.

WorkBuddy's conversational marketplace installation is documented for marketplace skills. Do not assume that pasting this GitHub URL into a conversation installs this custom skill automatically. See the official [WorkBuddy Skills guide](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market).

## Project-local installation

For WorkBuddy's project development mode, place the complete skill in the project's .codebuddy/skills/meeting-minutes directory. The resulting paths must include:

- .codebuddy/skills/meeting-minutes/SKILL.md
- .codebuddy/skills/meeting-minutes/references/meeting-domains.md
- .codebuddy/skills/meeting-minutes/references/workbuddy.md
- .codebuddy/skills/meeting-minutes/agents/openai.yaml

For a project that does not already contain this skill, run the following from the project working directory:

```bash
mkdir -p .codebuddy/skills
git clone https://github.com/kellyleong/meeting-minutes.git .codebuddy/skills/meeting-minutes
```

If the destination already exists, inspect that existing installation before updating it. Open the intended project in WorkBuddy and start a fresh task. This is project-scoped discovery, not a claim that the skill is enabled globally for every project.

Source: [WorkBuddy Projects](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Project).

## Use with a transcript or notes

Attach or paste the meeting transcript. Add an agenda and the previous action register when available. Invoke the skill with:

> 請使用 meeting-minutes 技能整理這份會議逐字稿；有議程時按議程編排，並列出決議、主責人、期限、交接依賴及待確認事項。

Once the skill is installed and enabled, its description supports recognizing meeting recordings, transcripts, and notes from the task context. If it is not selected automatically, select it in the task or use its name explicitly. The description is an invocation cue, not a file-system watcher or scheduled automation.

The resulting minutes distinguish confirmed decisions from suggestions, preserve unresolved information, and track owners, deadlines, handovers, and completion evidence. They retain prior unfinished actions when a previous register is supplied.

## Use with a recording

- First use an available, authorized audio-understanding or transcription capability.
- WorkBuddy documents the optional **Local Whisper** skill, with installation name **local-whisper**, for local speech-to-text. Its model must be downloaded before offline transcription is available.
- If Local Whisper is already installed and usable, obtain the transcript with it and then apply meeting-minutes. Another authorized transcription capability can also be used.
- If no transcription capability is available, provide a transcript or install and enable an appropriate capability through WorkBuddy. Do not infer meeting content from an audio filename.
- Do not promise unsupported speaker identification, codecs, file-size limits, or recording lengths.

This repository does not bundle a speech model or transcriber. Transcript processing remains usable without either.

Source: [WorkBuddy Local Whisper](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/WorkBuddy-Zero-Cost-Skill-Top-10/Local-Whisper).

## Validation scope

The repository uses SKILL.md frontmatter with name and description and relative bundled references. Compatibility was checked against official WorkBuddy documentation on 2026-10-27. Frontmatter and reference checks do not establish successful desktop import, automatic selection in a particular session, or actual audio transcription; confirm those in the target WorkBuddy client.
