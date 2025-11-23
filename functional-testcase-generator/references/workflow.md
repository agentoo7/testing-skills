# Functional Test Case Generation Workflow

This document provides detailed guidance for generating functional test cases from user story summaries.

## Workflow Overview

The test case generation process involves these key phases:

1. **Context Gathering** - Read project documentation and reference materials
2. **Input Verification** - Locate and validate the user story summary file
3. **Output Storage Configuration** - Locate and validate place to output TestCase files
4. **Analysis** - Map user story relationships and dependencies
5. **Generation** - Create test cases per user story following the template
6. **Validation** - Review against quality checklist
7. **Approval** - Get user review and approval per user story
8. **Reporting** - Generate final summary report

## Detailed Steps

### Phase 1: Context Gathering

**Objective:** Understand project context and requirements.
- Clarify the project context and requirements are supplied
- If not, ask user provide it
- The `template--functional-test-case.md` and `checklist--functional-testcase.md` already have, but ask user if they want to override it. 
- User can use command as `view the system template for functional test case` to view the `--functional-test-case.md` file 
- User can use command as `view the system checklist for functional test case` to view `checklist--functional-testcase.md` file

**What to Extract:**
- Project name and code
- The general business of this project, the detail will be included later
- Domain-specific terminology
- Quality standards
- Testing priorities


### Phase 2: Input Verification

**Objective:** Ensure the user story summary file is available and readable.

**Actions:**
- Check user input the user story summary document, user can typing the content of user story or upload it
- If not found any related user story summary info, ask user for the correct info
- Read and extract all user stories
- Identify user story IDs, titles, and acceptance criteria

**Output:** List of all user stories requiring test cases


### Phase 3: Output Storage Configuration 

**Objective:**

**Actions:**
- Ask user provide place to store the Test Cases that created based on User Stories
- Storage can be:
  - Jira (Use jira mcp)
  - file systems
  - Google Drive

### Phase 4: User Story Analysis

**Objective:** Understand relationships between user stories.

**Actions:**
- List all user stories from summary
- Identify dependencies between stories
- Note related user stories
- Document any cross-story test scenarios
- Understand workflow sequences

**Considerations:**
- Some user stories may require coordinated testing
- Dependencies affect test data and pre-conditions
- Related stories may share test scenarios

---

### Phase 4: Test Case Generation (Per User Story)

**Objective:** Generate comprehensive test cases for each user story.

#### 4.1 Extract User Story Details

For each user story, extract:
- User Story ID
- User Story Title
- Description/narrative
- Acceptance Criteria
- Business Rules
- Related User Stories

#### 4.2 Plan Test Coverage

Determine what needs testing:
- **Happy Path**: Main success scenario
- **Alternative Flows**: Valid variations
- **Edge Cases**: Boundary conditions
- **Error Scenarios**: Invalid inputs and error handling
- **Negative Tests**: Invalid operations

#### 4.3 Generate Test Cases

**File Naming:** `{{us-id}}.md` (one file per user story)
**Output Location:** `{{us-id}}.md`

**Follow Template Structure:**
- follow the `template.md` file 

**Quality Guidelines:**

#### 4.4 Ensure Complete Coverage

**Acceptance Criteria Mapping:**
- Every acceptance criterion must be covered
- Map each criterion to specific test steps
- Use checkboxes to track coverage

**Coverage Types:**
- Positive testing (valid inputs, expected behavior)
- Negative testing (invalid inputs, error handling)
- Boundary testing (min/max values, limits)
- Edge cases (empty, null, special characters)
- Alternative flows (different paths to success)

---

### Phase 5: Validation

**Objective:** Ensure test case quality before user review.

**Actions:**
1. Review generated test case against references/checklist.md
2. Verify completeness of all sections
3. Check acceptance criteria coverage
4. Validate test step clarity
5. Ensure traceability to user story
6. Verify test data sufficiency

**Quality Checks:**
- All template sections completed
- Clear, unambiguous language
- Specific, measurable expected results
- Logical step sequence
- No implicit assumptions
- Proper formatting

---

### Phase 6: User Review and Approval

**Objective:** Get user approval before proceeding to next user story.

**Presentation:**
Present the generated test case with:
- User story ID and title
- Number of test scenarios created
- Coverage summary (happy path, edge cases, errors)
- Any assumptions made
- Dependencies or prerequisites noted

**Approval Process:**
- WAIT for explicit user approval
- User can request changes
- User can approve individually or all at once
- If changes requested, update and re-present
  

**Do NOT proceed** to the next user story without approval.

---

### Phase 7: Store Test Case 
**Save file**:
- After user approval, you should save to file with name `{{us-id}}.md`


### Phase 8: Iteration

**Objective:** Generate test cases for all user stories.

**Process:**
1. After approval of current user story, move to next
2. Repeat Phases 4-6 for each remaining user story
3. Track progress
4. Maintain consistency across test cases

---

### Phase 9: Final Reporting

**Objective:** Provide comprehensive summary of test case generation.

**Report Contents:**
- Project information
- User stories processed
- Total test cases created
- Coverage statistics
- Test case distribution by priority/type
- Assumptions and notes
- Recommendations

**Report Formats:**
- Markdown: `testcase-generation-report.md`
- HTML: `testcase-generation-report.html`
  - [ ] Use mermaid for flow
  - [ ] Use treeviw for tree
  - [ ] Head menu can collase

---

## Best Practices

### Test Case Writing

1. **Be Specific**: Use exact field names, button labels, and UI elements
2. **Be Clear**: Anyone should be able to execute the test
3. **Be Complete**: Include all necessary information
4. **Be Realistic**: Use plausible test data
5. **Be Traceable**: Link clearly to user story and acceptance criteria

### Coverage Considerations

1. **Positive Scenarios**: Verify expected functionality works
2. **Negative Scenarios**: Verify system handles errors gracefully
3. **Boundary Testing**: Test limits and edge conditions
4. **Integration**: Consider interactions with other features
5. **Security**: Validate permissions and data protection

### Common Pitfalls to Avoid

1. **Ambiguous Steps**: Avoid vague terms like "appropriate" or "several"
2. **Missing Test Data**: Every input should have example values
3. **Unmeasurable Results**: Expected results must be verifiable
4. **Skipping Cleanup**: Always document post-conditions
5. **Ignoring Edge Cases**: Don't forget boundary and error scenarios
6. **Poor Traceability**: Always link to acceptance criteria

---

## Decision Points

### When to Create Multiple Test Cases

Create separate test cases for:
- Different acceptance criteria with distinct workflows
- Complex scenarios with many variations
- Different user roles or permissions
- Different data types or conditions

### When to Combine into One Test Case

Combine when:
- Testing closely related functionality
- Steps naturally flow together
- Acceptance criteria are interdependent
- Splitting would create redundancy

---

## Output Structure

```
output/
└── functional-testcases/
    ├── US-001.md
    ├── US-002.md
    ├── US-003.md
    └── ...
```

Each file contains complete test case(s) for one user story.

---

## Quality Standards

Every test case must:
1. Follow the template structure exactly
2. Pass all checklist items
3. Cover all acceptance criteria
4. Include positive, negative, and edge case scenarios
5. Provide specific, executable steps
6. Specify measurable expected results
7. Include necessary test data
8. Document assumptions clearly
9. Maintain traceability to user story
10. Be reviewed and approved by user

---

## Automation Considerations

When evaluating automation:
- **Automation Feasibility**: Can it be automated?
- **Automation Priority**: Should it be automated?
- **Automation Approach**: How would you automate it?
- **Automation Challenges**: What makes it difficult?

High-priority candidates for automation:
- Regression tests
- Repetitive tests
- Data-driven tests
- Tests with deterministic results
- Tests run frequently
