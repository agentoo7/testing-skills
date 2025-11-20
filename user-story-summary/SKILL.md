---
name: user-story-summary
description: Create comprehensive user story summaries from various sources (Jira, uploaded files, Google Drive). Use when users need to collect, format, and validate user stories into a standardized summary document. Triggers include requests to "create user story summary", "summarize user stories", "collect stories from Jira/files", or "format user stories".
---

# User Story Summary Skill

Create standardized, high-quality user story summaries from multiple sources with built-in quality validation.

## Workflow

Follow this workflow when creating user story summaries:

### 1. Determine Source

Ask the user to specify the source of user stories:

- **Jira MCP**: Request cloud ID/URL and project key or JQL query.
- **Uploaded File**: Request user to upload file (CSV, Excel, text, etc.)
- **Google Drive**: Request file/folder link or search criteria

**Example questions:**
- "Where are your user stories located? I can collect them from Jira, uploaded files, or Google Drive."
- "Do you have a specific Jira project or filter, or would you like to upload a file?"

### 2. Collect User Stories

Based on the source, collect the user stories:

#### From Jira MCP
1. Use `Atlassian:search` or `Atlassian:searchJiraIssuesUsingJql` to find stories
2. Use `Atlassian:getJiraIssue` to get full details of each story
3. Use `Atlassian:getJiraIssueRemoteIssueLinks` to identify related stories
4. Extract: ID, title, description, acceptance criteria, status, links

#### From Uploaded Files
1. Use `view` tool to read file contents
2. Parse the file format (CSV, Excel, JSON, text)
3. Extract user story fields from the structure
4. If using Python libraries needed, install with `--break-system-packages`

#### From Google Drive
1. Ask user to enable Google Drive integration if not already connected
2. Use Google Drive tools to search and fetch files
3. Parse the retrieved documents for user story data

### 3. Apply User Story Template

For each collected user story, format it according to the template in `references/template.md`.

**Read the template before formatting:**
```bash
view references/template.md
```

**Template fields to populate:**
- Story ID (from source system)
- Title (clear, concise summary)
- Preconditions (any setup or prerequisites)
- Description (As a... I want... so that... format)
- Acceptance Criteria (numbered list of testable conditions)
- Status (current state in workflow)
- Related Stories (dependencies, blocked by, relates to)
- Additional Notes (any supplementary information)

**Best practices:**
- If the source doesn't use "As a... I want... so that..." format, translate it appropriately
- Extract acceptance criteria from description or comments if not explicitly listed
- Identify relationships between stories (epic/story, story/subtask, blockers, etc.)
- Preserve original IDs for traceability

### 4. Organize and Group Stories

Group related user stories into functional areas or features:

- Identify common themes, features, or modules
- Create clear group names and descriptions
- Ensure each story is assigned to at least one group
- Document cross-cutting concerns that span multiple groups

### 5. Create Summary Document

Generate a comprehensive markdown document:

**Structure:**
1. **Executive Summary**: Overview of total stories, groups, key insights
2. **Table of Contents**: Navigate to different groups
3. **Functional Groups**: Organized sections with stories
4. **Statistics**: Metrics on stories, status distribution, relationships
5. **Metadata**: Source information, generation date, version

Save as `user-story-summary.md` in `/mnt/user-data/outputs/`

### 6. Validate Against Checklist

Read and apply the quality checklist:

```bash
view references/checklist.md
```

**Key validation areas:**
1. **Completeness**: All source stories collected, all fields populated
2. **Format Compliance**: Template structure followed, proper markdown
3. **Grouping Quality**: Logical organization, clear boundaries
4. **Relationship Accuracy**: Valid links, no broken references
5. **Data Integrity**: Unique IDs, consistent formatting, traceable to source

Create a validation report documenting:
- Items checked from checklist
- Any issues found (Critical, Major, Minor)
- Overall assessment (Pass/Conditional Pass/Fail)
- Recommendations for improvement

Save as `verification-report.md` in `/mnt/user-data/outputs/`

### 7. Deliver Results

Provide the user with:
1. Main summary document (`user-story-summary.md`)
2. Verification report showing quality validation results
3. Brief overview of findings, statistics, and any issues

### 8. Data Collection Report

- [ ] Create data collection report documenting:
  - Source(s) accessed
  - Number of user stories retrieved
  - Collection timestamp
  - Any issues or errors encountered
  - Success/failure statistics
- [ ] Save report as: `data-collection-report.md`
- [ ] Generate web HTML version `data-collection-report.html`
    - [ ] Use mermaid for flow
    - [ ] Use treeviw for tree
    - [ ] Head menu can collase

- [ ] Include summary statistics and metrics

## Tips for Success

**Data Collection:**
- Verify credentials and permissions before attempting to access sources
- Handle pagination for large datasets (>50 stories)
- Log any stories that fail to collect with reasons
- Preserve original data for reference

**Formatting:**
- Be consistent with terminology and structure across all stories
- If source data is incomplete, note missing fields explicitly
- Use clear, professional language in descriptions
- Link related stories bidirectionally when possible

**Validation:**
- Don't skip validation even if the document looks good
- Document both strengths and areas for improvement
- Prioritize critical and major issues
- Be honest about data quality limitations

**Progressive Disclosure:**
- For large collections (100+ stories), consider creating a summary-of-summaries
- Break very large documents into multiple files by functional area
- Always provide statistics and navigation aids for large datasets

## Example Usage

**User**: "Create a user story summary from our Jira project MOBILE-APP"

**Claude**:
1. Searches Jira (Use jira mcp) for stories in MOBILE-APP project
2. Collects all story details and relationships
3. Applies template to format each story
4. Groups stories by feature (Login, Dashboard, Profile, Settings, etc.)
5. Creates summary document with all stories organized
6. Validates against checklist
7. Delivers summary and verification report

**User**: "I uploaded a CSV with our user stories, can you summarize them?"

**Claude**:
1. Reads the uploaded CSV file
2. Parses columns to extract story data
3. Applies template to standardize format
4. Creates functional groupings
5. Generates summary document
6. Validates quality
7. Provides final deliverables

## Reference Files

- `references/template.md` - Standard user story template format
- `references/checklist.md` - Comprehensive quality validation checklist

Load these files as needed during the workflow using the `view` tool.
