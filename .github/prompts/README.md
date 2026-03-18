# Structured Autonomy Prompts

This directory contains prompt templates for AI agents to work autonomously on CalcNote development tasks. These prompts implement a structured workflow that breaks complex features into manageable steps.

## 📂 Prompt Files

### 1. `structured-autonomy-plan.prompt.md`
**Purpose:** Planning phase - Research and design development plans

**When to use:** Start of any new feature or significant change

**What it does:**
- Runs comprehensive research (code search, documentation review, dependencies)
- Analyzes user request and breaks it into logical commits
- Creates a detailed plan with implementation steps
- Identifies areas needing clarification
- Saves plan to `plans/{feature-name}/plan.md`
- Pauses for user feedback before proceeding

**Example usage:**
> "Follow the structured-autonomy-plan prompt. I want to add a new export to HTML feature."

---

### 2. `structured-autonomy-implement.prompt.md`
**Purpose:** Implementation phase - Execute a pre-approved plan

**When to use:** After a plan has been created and approved

**What it does:**
- Reads the approved plan from `plans/{feature-name}/plan.md`
- Implements each step as a separate commit
- Runs tests after each significant change
- Verifies changes don't break existing functionality
- Creates clean, atomic commits with descriptive messages

**Example usage:**
> "Follow the structured-autonomy-implement prompt. Implement the plan in plans/html-export/plan.md"

---

### 3. `structured-autonomy-generate.prompt.md`
**Purpose:** Code generation phase - Create new code following patterns

**When to use:** Generating new modules, classes, or files that follow existing patterns

**What it does:**
- Analyzes existing code patterns in the repository
- Generates new code matching the project's style and architecture
- Ensures consistency with naming conventions, type hints, docstrings
- Creates comprehensive tests for new code
- Documents new features appropriately

**Example usage:**
> "Follow the structured-autonomy-generate prompt. Create a new design module for concrete slabs following the column module pattern."

---

## 🔄 Typical Workflow

1. **Planning** → Use `structured-autonomy-plan.prompt.md` to research and design
2. **Review** → User reviews the plan, provides feedback or approval
3. **Implementation** → Use `structured-autonomy-implement.prompt.md` to execute
4. **Testing** → Verify all tests pass, functionality works as expected
5. **Generation** (optional) → Use `structured-autonomy-generate.prompt.md` for repetitive patterns

---

## 🎯 Benefits

- **Consistency:** All features follow the same structured approach
- **Traceability:** Clear plans document decisions and rationale
- **Quality:** Research phase ensures understanding before coding
- **Atomicity:** Features broken into logical, reviewable commits
- **Collaboration:** Plans facilitate discussion and feedback

---

## 📝 Notes

- Plans are saved in `plans/` directory for future reference
- Each plan corresponds to a single PR on a dedicated feature branch
- Prompts are designed for AI agents (GitHub Copilot, Claude, etc.)
- Human review and approval is expected between planning and implementation
- Prompts can be customized for project-specific needs

---

*Last updated: February 2026*
