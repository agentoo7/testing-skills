# Testing Skills

This repository contains Agent Skills for generating test cases and summarizing user stories.

## Available Skills

### 1. Functional Test Case Generator (`functional-testcase-generator`)
Generates comprehensive functional test cases from user story summaries. It follows a strict workflow including input verification, analysis, generation, validation, and reporting.

- **Trigger Phrases**: "generate test cases", "create functional tests", "write test cases for user stories".
- **Input**: User story summary (text or file).
- **Output**: Markdown files for each test case and a final report.

### 2. User Story Summary (`user-story-summary`)
Collects and formats user stories from various sources (Jira, files, Google Drive) into a standardized summary document.

- **Trigger Phrases**: "create user story summary", "summarize user stories", "collect stories from Jira".
- **Input**: Jira project/filter, uploaded files, or Google Drive links.
- **Output**: A structured `user-story-summary.md` file.

## User Guide

To upload these skills to Claude, please refer to the official guide:
[**How to use Skills in Claude**](https://www.claude.com/blog/skills)

## Development

### Directory Structure
```
.
├── functional-testcase-generator/       # Source code for test case generator
├── functional-testcase-generator.skill  # Compiled skill package (zip)
├── user-story-summary/                  # Source code for user story summary
└── user-story-summary.skill             # Compiled skill package (zip)
```

### Updating Skills

1.  Modify the source files in the respective directories (`functional-testcase-generator/` or `user-story-summary/`).
2.  Repackage the skill using the `zip` command.

**For Functional Test Case Generator:**
```bash
zip -r functional-testcase-generator.skill functional-testcase-generator
```

**For User Story Summary:**
```bash
zip -r user-story-summary.skill user-story-summary
```

3.  Commit and push both the source changes and the updated `.skill` files.

### Upload Skills to Claude

1.  Go to the [Claude Skills](https://claude.ai/settings/capabilities) page.
2.  Click on the "Upload Skill" button.
3.  Select the `.skill` file for the skill you want to upload.
4.  Click on the "Upload" button.
