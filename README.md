<div align="center">
    <h1>📋 Spec-Driven Development Boilerplate</h1>
    <h3><em>From specifications to software - automatically.</em></h3>
</div>

<p align="center">
    <strong>Transform your specifications into working code through AI, treating specs as the primary development artifact.</strong>
</p>

> ## 🚀 **What's new?**
> - **Design Intent documentation** - A new workflow for documenting your design UX decisions
> - **Design intent specialized sub-agent** - Uses the design intent documentation to create designs that closely align with your decisions so far, increasing consistency.

---

>[!NOTE]
>This repository is heavily influenced by and based on the work of [John Lam](https://github.com/jflam).

---

This guide shows you exactly how to work with AI to build real software prototypes. No coding knowledge needed.

## Table of Contents

- [What is Spec-Driven Development?](#what-is-spec-driven-development)
- [Core Philosophy](#core-philosophy)
- [How SDD Differs from Vibe Coding](#how-sdd-differs-from-vibe-coding)
- [Getting Started (One-Time Setup)](#getting-started-one-time-setup)
- [Day 0 Example (your first feature!)](#day-0-example-your-first-feature)
- [Day 1 Example (continuing your project)](#day-1-example-continuing-your-project)
- [Advanced Techniques](#advanced-techniques)

---

## What is Spec-Driven Development?

**SDD treats specifications as executable code.** Instead of documentation that becomes outdated, your specifications generate the implementation and evolve with your project. When you write a clear spec, AI builds exactly what you described.

## Core Philosophy

- **Specifications ARE the source of truth** - Your PRD directly generates working software
- **Design intent persists** - Every decision is captured and reused across features  
- **AI as implementer** - You define what to build; AI handles how to build it
- **Quality through clarity** - Ambiguous specs create bugs; precise specs create great software

## How SDD Differs from Vibe Coding

| Vibe Coding | Spec-Driven Development |
|-------------|-------------------------|
| "Make it feel right" through iteration | Define "right" upfront, then generate |
| Design decisions lost in chat history | Design intent documented and reusable |
| Inconsistent AI outputs | Consistent results from clear specifications |
| Tribal knowledge disappears | Institutional memory that grows over time |

**The key difference:** Vibe coding optimizes for speed. SDD optimizes for sustainable quality at AI speed.

---

## Getting Started (One-Time Setup)

**If you cloned this repository**: Structure is already created. Skip to Day 0 Example.

**If you only have the markdown files**: Say exactly this to your AI:
```
Read the SETUP_INSTRUCTIONS.md file and create the project structure for me
```

✅ **Outcome**: A complete project structure with all folders, templates, and rules configured. Ready to start building.

---

## Day 0 Example (your first feature!)

### Step 1: Create Your Project Vision

Tell your AI what you want to build and ask for a brainstorm session to define the complete vision.

**Example**: "I want to build a Netflix-style app but for cloud gaming. Help me define my vision with a brainstorm session."

The AI will ask about the problem, users, success metrics, business model, and risks to capture your complete idea.

✅ **Outcome**: `/memory/project-vision.md` - Your complete vision documented.

### Step 2: Plan Your First Feature

Pick one piece of your vision to start building. Your vision gives the AI context for why this feature matters and how it fits the bigger picture.

**Say exactly this:**
```
/new-feature [specific feature from your vision]
```

**Optional: Add design references**
```
/new-feature [specific feature] styled like [these screenshots/this app]
```

The AI will ask about user assumptions, success metrics, and scope to create a feature specification covering WHAT you're building and WHY it matters. No technical details yet.

✅ **Outcome**: `/specs/001-game-library/feature-spec.md` - A detailed plan for your feature, not code yet.

### Step 3: Review and Perfect the Spec

Review what the AI created. Focus especially on the user stories - these are the outline of what to expect from your feature.

1. Open the file: `/specs/001-game-library/feature-spec.md`
2. **User stories**: Do they match what you imagined? These outline exactly what users will do.
3. **Success criteria**: Is this how you'll know it works?
4. **Missing pieces**: What did the AI not include?

**Watch out for**: Technical details (like "use React components") don't belong in the spec. The spec is only about WHAT and WHY, not HOW.

Make changes by telling the AI: "Add a search bar to the spec" or "The success metric should be 20 seconds, not 30."

✅ **Outcome**: A refined spec that captures exactly what you want to build.

### Step 4: Create implementation Plan

**Say exactly this:**
```
/generate-implementation-plan The spec looks perfect. Use React and Fluent UI v9
```

#### What happens next:

> **AI**: I'll create an implementation plan that covers HOW to build this technically.
>
> Creating `/specs/001-game-library/implementation-plan.md` with:
> - Technical architecture
> - Component structure  
> - Time estimates
> - Visual reference mapping (if you provided screenshots)

✅ **Outcome**: 
- `/specs/001-game-library/implementation-plan.md` - Technical plan ready for implementation

### Step 5: Build the Implementation

**Say exactly this:**
```
Go ahead and implement it now
```

✅ **Outcome**: A working prototype running at http://localhost:3000 (or the AI will tell you to run `npm start` in your terminal if it's not already running).

### Step 6: Refine Through Vibe Coding

Now comes the fun part - making it feel perfect. This typically takes 90% of your feature development time.

**Common refinements:**
```
Make the cards 20% bigger
Add more space between sections
The blue is too bright, make it softer
Add a subtle hover animation
Move the search bar to the right
```

Keep refining until it feels just right. The AI will make each adjustment instantly.

**When you're satisfied with the result:**
```
/document-intent
```
Documents all design patterns, or:
```
/document-intent card-layout
```
Documents only a specific pattern.

**Review what was documented:** Open the generated design intent files and review critically:
- Is the format reusable for future features?
- Did it capture design dialect (custom decisions) vs design system artifacts (standard tokens)?
- Does it need refactoring for clarity?

Tell the AI: "Remove the color section - those are just Fluent tokens" or "Refactor the spacing section to be more reusable."

✅ **Outcome**: 
- A polished prototype that feels delightful
- Reviewed and refined design patterns ready for reuse

### Step 7: Log Your Session

**Say exactly this (optional - AI usually offers automatically):**
```
/create-diary-entry
```

This creates a diary entry so the AI can pick up where you left off in future sessions.

#### What happens:

> **AI**: I'll document what we accomplished. Creating a diary entry with:
> - Project vision created
> - First feature (game browsing) specified and built
> - Key decisions made
> - What to work on next
>
> Diary saved! Next time you return, I'll read this and know exactly where we left off.

✅ **Outcome**: `/diary/session-2024-01-15.md` - Your project's history that keeps everyone on the same page.

### Step 8: Commit Your Work (Optional)

**Say exactly this:**
```
Commit all changes with a descriptive message
```

If you want to share your work:
```
Push to GitHub
```

✅ **Outcome**: Your work is saved in version control and optionally shared with others.

---

## Day 1 Example (continuing your project)

### Step 1: Onboard the AI

**Say exactly this:**
```
Onboard to this project by reading the latest diary entry and design intent folders
```

✅ **Outcome**: The AI understands your project context and existing design patterns, ready to build consistently.

### Steps 2-6: Follow Day 0 Workflow

The process is identical to Day 0 (Steps 2-6), but now the AI automatically:
- **Uses existing design patterns** from your design intent folders
- **Maintains visual consistency** across new features
- **Builds on proven decisions** rather than starting fresh

### Step 7: Log Your Session

**Say exactly this:**
```
/create-diary-entry
```

### Step 8: Commit Changes (Optional)

**Say exactly this:**
```
Commit all changes with a descriptive message
```

**Key difference from Day 0:** Your AI now has design memory, ensuring every new feature matches your established visual language.

---

## Advanced Techniques

### Design Intent Specialist (For Visual Accuracy & Consistency)

When you need to implement visual references accurately and maintain consistency across your project, use the Design Intent Specialist agent.

#### When to Use

Use the specialist when:
- You have Figma designs or screenshots to implement accurately
- You need complex visual extraction and implementation
- You're working with detailed visual references that require precision
- You want to ensure consistent visual language across features

#### How to Trigger

For visual implementations:
```
Use design intent specialist to create [feature] using [reference]
```

#### New Implementation-First Workflow

> **You**: Use design intent specialist to create the gallery using this Figma reference
>
> **AI**: Starting design intent specialist...
> 
> [Specialist focuses on visual accuracy through iteration until satisfied]
> 
> **You**: [After multiple refinements] This looks perfect now. /document-intent gallery-layout
> 
> **AI**: ✓ Design dialect documented at:
> - /design-intent/patterns/gallery-layout.md (3-card grid pattern)
> - /design-intent/foundations/custom-spacing.md (48px section breaks)

#### What Makes This Different

**Old approach**: Extract specs → Document → Implement → Often poor visual match
**New approach**: Focus on visual accuracy → Iterate until perfect → Document what worked

#### Key Features

- **Implementation-first**: Prioritizes visual accuracy over upfront documentation
- **Consistency enforcement**: Always checks and reuses existing design intent patterns first
- **Iteration support**: Helps you refine through "vibe coding" until satisfied  
- **Smart documentation**: Use `/document-intent` to capture only design dialect (not design system artifacts)
- **Custom component tracking**: Automatically tags and tracks custom components for technical debt auditing

#### Documentation Control

- **Global capture**: `/document-intent` - Documents all custom patterns
- **Focused capture**: `/document-intent card-layout` - Documents specific patterns only
- **On-demand only**: No documentation overhead during iteration phase

✅ **Outcome**: Visually accurate implementations that match references, with design dialect documented only after proven success.
