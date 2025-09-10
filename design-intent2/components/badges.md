# Pattern: Badge Design System

## Context
Status indicators and informational tags across applications for communicating state, urgency, and categories

## Decision
Rounded badges with tint appearance and semantic color meanings for consistent status communication

## When to Use
- **Status communication**: Communicating state or urgency at a glance
- **Categorical labels**: Visual grouping or categorization of content
- **Quick scanning**: Information users need to identify immediately
- **Semantic color meaning**: When color reinforces the message (severe=urgent, brand=informational)

## Components
- `Badge` - Standard Fluent UI Badge component
- `StatusBadge` - Custom wrapper with status-to-color mapping

## Why
Rounded shape feels more professional than circular; tint appearance provides visual hierarchy without overwhelming content; semantic colors help users build consistent mental models across features

## Dependencies
Fluent UI Badge component, established color semantic meanings

---

## Usage Guidelines

### Universal Standards
- Always use `shape="rounded"` and `appearance="tint"`
- Default to `size="small"` for most contexts
- Maintain consistent color semantics: severe (urgent/expiring), brand (pending/requests), success (active/approved)

### When NOT to Use
- Interactive elements (use Button/Link instead)
- Long text (max ~20 characters)
- Primary actions where users expect to click

## Examples

- **Status indicators**: "Expires in 3 days", "Pending approval", "Active"
- **Categorical labels**: Request types, agent categories, content tags
- **Quick scanning**: Table status columns, card headers