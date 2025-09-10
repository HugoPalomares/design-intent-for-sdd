<div align="center">
    <h1>🎨 Design Intent for Spec-Driven Development</h1>
    <h3><em>If design systems are your language, design intent is your dialect</em></h3>
</div>

<p align="center">
    <strong>A design consistency layer for AI-driven development teams. Captures how your team specifically applies design systems.</strong>
</p>

---

## What is Design Intent?

**Design systems** provide the universal language - components, tokens, patterns that work everywhere.

**Design intent** captures your dialect - how your team specifically applies that language for your unique context.

### Language vs. Dialect Examples

**Language (Design System)**: Button component with primary, secondary, danger variants  
**Your Dialect**:
- **Enterprise**: "We never use danger buttons in data tables - only in confirmation dialogs for security compliance"
- **Consumer**: "We use danger buttons for 'Delete' actions everywhere to create urgency and prevent accidental data loss"

**Language (Design System)**: Standard spacing scale (8px, 16px, 24px...)  
**Your Dialect**:
- **Enterprise**: "We use 32px between sections for clear information hierarchy in dense dashboards"
- **Consumer**: "We use 48px between sections to create breathing room and reduce cognitive load"

**Language (Design System)**: Card component with elevation options  
**Your Dialect**:
- **Enterprise**: "We only use elevation on grey backgrounds, never nest elevated containers"
- **Consumer**: "We layer multiple card elevations to create depth and visual interest"

---

## Prerequisites

**Learn spec-driven development first**: [github/spec-kit](https://github.com/github/spec-kit)

This project adds design intent workflows on top of spec-driven development. You'll need to understand feature specs and implementation plans before adding design consistency.

---

## Getting Started

**Dependencies:** Claude Code and Figma MCP server

```bash
git clone https://github.com/HugoPalomares/design-intent-for-sdd.git
cd design-intent-for-sdd
```

**Onboard your AI:**
```
Onboard yourself to this project by reading the CLAUDE.md file before we can continue.
```

✅ **AI now understands the design intent workflow and available commands**

---

## Design Intent Workflow

### 1. Visual Implementation (`/design`)

When you have visual references (Figma, screenshots, mockups):

```
/design [screenshot of dashboard]
```

**What happens:**
- Launches Design Intent Specialist for visual accuracy
- Reviews existing design patterns for consistency  
- Implements section by section (header, nav, main, footer)
- Handles conflicts between reference and existing patterns
- Asks for guidance when design decisions conflict

### 2. Spec-Driven Implementation (`/implement`)

When building from feature specs with design components:

```
/feature "User dashboard with metrics widgets"
/plan
/implement
```

**What happens:**
- Reads implementation plan and identifies visual components
- Uses Design Intent Specialist for UI elements
- Uses general agent for backend/logic
- Coordinates full-stack implementation
- Maintains design consistency throughout

### 3. Pattern Documentation (`/document-design-intent`)

After building features, capture reusable patterns:

```
/document-design-intent
```

**What happens:**
- Analyzes recent work for reusable design decisions
- Suggests what should be documented and where
- Presents summary for your review
- **Does NOT automatically document** - you choose what to preserve
- Documents only your dialect, not design system artifacts

### 4. Iteration and Consistency

**Vibe coding with memory:**
```
Make the spacing tighter
Use our established card pattern from the agents list
Add the same hover treatment we used in the dashboard
```

**Design intent ensures:**
- New features automatically use established patterns
- Conflicts are surfaced and resolved consciously  
- Custom decisions are preserved and reused
- Design quality scales with your team

---

## Key Commands

- `/feature [description]` - Create feature specification
- `/plan` - Generate implementation plan  
- `/design [reference]` - Implement from visual references
- `/implement` - Execute feature plan (design + engineering)
- `/document-design-intent` - Analyze and suggest design patterns to preserve
- `/diary` - Document session progress

---

## File Structure

```
/design-intent/
  /components/        # Component-specific patterns
  /foundations/       # Base design decisions  
  /patterns/          # Layout and composition patterns
  design-intent-template.md  # Template for new patterns

/specs/               # Feature specifications and plans
/diary/               # Session documentation  
/memory/              # Project context and principles
```

---

## Why Design Intent Matters

**Without design intent:** Each AI interaction starts from scratch, leading to design drift and inconsistency as you build.

**With design intent:** Your design decisions become organizational memory that scales across features, teams, and time.

**The result:** Consistent, intentional design that feels cohesive even when built iteratively by AI.
