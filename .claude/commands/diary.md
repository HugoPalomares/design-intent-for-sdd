# /diary

This command creates a session diary entry to document development progress, decisions, and handoff context.

## Usage

```
/diary
```

Creates a new diary entry for the current date, or updates the existing entry if one already exists for today.

## Process

### 1. Determine File Path
- **File naming**: `/diary/session-YYYY-MM-DD.md` (e.g., `/diary/session-2024-01-15.md`)
- **Date format**: Use current date in YYYY-MM-DD format
- **Check existing**: If file already exists for today, update it instead of creating new

### 2. Gather Session Information
Before creating the entry, collect information about:
- **Session goals**: What was planned for this session
- **Accomplishments**: What was actually built or completed
- **Key decisions**: Important choices made during implementation
- **Current state**: Where the project stands now
- **Next priorities**: What should happen in the next session
- **Known issues**: Problems that aren't blocking but need attention

### 3. Create Diary Entry
Use this template structure:

```markdown
# Development Session - [Month DD, YYYY]

## Session Goals
[What you planned to accomplish this session - if this was discussed at start]

## What We Built
- [Concrete accomplishment 1 with specific details]
- [Concrete accomplishment 2 with specific details]
- [Feature/component with brief description]

## Key Implementation Details

### [Component/Feature Name]
- **Decision**: [What was decided and why]
- **Approach**: [How it was implemented]
- **Trade-offs**: [What was sacrificed for simplicity]

### [Another Component/Feature if applicable]
- **Decision**: [Key choice made]
- **Approach**: [Implementation strategy]
- **Trade-offs**: [Compromises for prototype goals]

### Critical Fixes Applied
1. **[Issue Name]**: [What was wrong and how it was fixed]
   ```typescript
   // Example code if relevant
   ```

## Current State
- [Description of where things stand]
- [What's working well]
- [What's not yet implemented]

## Tomorrow's Priorities
1. [Most important task for next session]
2. [Second priority]
3. [Nice to have if time allows]

## Known Issues
- [Issue that doesn't block progress but should be remembered]
- [Technical debt or improvement opportunity]

## Handoff Notes
[Specific context the next session needs to know - decisions, gotchas, patterns established]

## Design Intent Progress
[If any design intent was documented or patterns established]
- Pattern documented: [Name and location]
- Custom components created: [List any custom components and why]
- Consistency decisions: [Any design system choices made]
```

### 4. Content Guidelines

#### What We Built Section
Focus on **concrete outcomes**:
- ✅ "Built gallery component with 3-card responsive layout"
- ✅ "Implemented user authentication flow with mock data"
- ❌ "Worked on some components"
- ❌ "Made progress on the frontend"

#### Key Implementation Details
Document **decisions and reasoning**:
- Why specific approaches were chosen
- What alternatives were considered
- How constitution principles were applied
- Trade-offs made for prototype goals

#### Current State
Be **specific about status**:
- What functionality works end-to-end
- What's partially implemented
- What's blocked or needs attention
- Any integration points established

#### Tomorrow's Priorities
Make priorities **actionable**:
- ✅ "Add loading states to gallery cards"
- ✅ "Implement search functionality for user dashboard"
- ❌ "Continue working on UI"
- ❌ "Fix various issues"

### 5. Update Existing Entry
If a diary entry already exists for today:
- **Append to accomplishments**: Add new items to "What We Built"
- **Update current state**: Reflect latest progress
- **Revise priorities**: Update based on what was completed
- **Add new decisions**: Document any additional key choices made

### 6. Output Confirmation
After creating/updating the diary entry:

```markdown
## Diary Entry Complete

**File**: `/diary/session-[YYYY-MM-DD].md`
**Status**: [Created new / Updated existing]

### Session Summary
- **Accomplishments**: [X] items documented
- **Key Decisions**: [X] implementation choices recorded
- **Next Priorities**: [X] tasks identified for next session

### Handoff Ready
This entry provides context for:
- ✓ Current project state
- ✓ Recent decisions and trade-offs
- ✓ Next session priorities
- ✓ Known issues and considerations
```

## When to Use

### End of Session (Primary)
- User says "let's wrap up" or similar
- Natural stopping point reached
- Before committing major work

### Major Milestone
- Feature completion
- Significant architectural decision
- Integration point established

### Handoff Situations
- Switching context to different feature
- Long break between sessions expected
- Complex decisions that need documentation

### User Request
- User explicitly asks for documentation
- Project review or status check needed
- Planning next development phase

## Integration Points

### Session Continuity
- Next session starts by reading latest diary entry
- Provides context for where to resume work
- Maintains momentum across sessions

### Git Workflow
- Create diary entries before major commits
- Reference diary in commit messages if helpful
- Document decisions that affect architecture

### Design Intent Relationship
- Note any design patterns established
- Reference any `/document-intent` commands used
- Track custom components created

### Constitution Compliance
- Document how constitution principles were applied
- Note any trade-offs made for simplicity
- Record framework-first decisions

## Example Usage

### Session End Example
```
User: "Great work today, let's document this progress. /create-diary-entry"

AI: "Creating diary entry for today's session...

✓ Session documented at `/diary/session-2024-01-15.md`
✓ 3 major accomplishments recorded
✓ 2 key implementation decisions documented  
✓ 4 priorities identified for next session

Key highlights:
- Gallery component completed with responsive design
- Custom card hover animations implemented
- Design pattern documented for future consistency
- Next: Add search functionality and loading states"
```

### Mid-Session Documentation
```
User: "We just made some big decisions, let's capture them. /create-diary-entry"

AI: "Updating today's diary entry with recent decisions...

✓ Added navigation architecture decision
✓ Documented custom component justification
✓ Updated current state and priorities

The entry now includes the routing strategy we chose and why we went with custom navigation over standard patterns."
```

## Behavioral Notes

1. **Outcome-focused**: Document what was built, not how it was built
2. **Decision-focused**: Capture why choices were made, not just what was done
3. **Handoff-ready**: Write for someone else to continue the work
4. **Actionable**: Make priorities concrete and specific
5. **Honest**: Document both successes and known issues
6. **Pattern-aware**: Note design decisions that affect consistency