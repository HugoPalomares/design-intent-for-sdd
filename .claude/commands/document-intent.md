# Document Intent Command

This command captures design dialect patterns after successful implementation and user satisfaction.

## Usage

### Global Documentation
```
/document-intent
```
Documents all design dialect patterns found in the current implementation.

### Contextual Documentation  
```
/document-intent [pattern-name]
```
Documents only the specified pattern (e.g., `card-layout`, `navigation-pattern`, `spacing-system`).

## Implementation

When this command is triggered, immediately execute:
```
Use design intent specialist to document design dialect patterns from current implementation
```

## Process

### 1. Design Intent Specialist Activated
The specialist is automatically invoked to:
- Apply specialized design dialect vs. design system knowledge
- Leverage visual extraction expertise and MCP tools
- Ensure consistent documentation format and quality

### 2. Validate Trigger (Specialist Action)
- Only execute when user is satisfied with implementation results
- This should happen AFTER iteration phase, not during implementation
- Ensure there are actual patterns worth documenting

### 3. Audit Current Implementation (Specialist Action)
- Scan current implementation for design decisions using specialist expertise
- Apply trained knowledge of "design dialect" vs "design system artifacts"
- Focus on custom decisions that won't come from Fluent UI

### 4. Extract Design Dialect Only (Specialist Action)

#### What TO Document:
- **Custom Layout Patterns**: App-specific compositions ("3-card grid with 24px gaps")
- **Contextual Spacing**: Deviations from standard tokens ("48px section breaks for emphasis")  
- **Content Hierarchies**: Information architecture patterns ("Feature cards: icon top-left, title, 2-line description max")
- **Custom Compositions**: How standard components are combined uniquely
- **Component Adaptations**: When and why custom components were needed

#### What NOT to Document:
- Colors that are just Fluent tokens
- Typography using standard Fluent scales
- Component props that are library defaults
- Standard responsive breakpoints
- Default spacing values

### 5. Create Documentation Files (Specialist Action)

#### For Global Documentation (`/document-intent`):
Specialist creates files in appropriate locations using standardized format:
- `/design-intent/patterns/[pattern-name].md` for layout patterns
- `/design-intent/foundations/[property].md` for foundational decisions
- `/design-intent/components/[component-name].md` for custom component patterns

#### For Contextual Documentation (`/document-intent [pattern]`):
Specialist creates or updates the specific pattern file only.

### 6. Documentation Format (Specialist Standards)

Use this format for design dialect documentation:

```markdown
## Pattern: [Pattern-Name]
**Context**: [Where this pattern is used]
**Custom Decisions**: [What makes this different from design system defaults]

### Design Dialect
- [Specific decision]: [Value] (reasoning: [why this choice])
- [Layout pattern]: [Description of composition]
- [Spacing decision]: [Value with justification]

### Implementation
- **Components Used**: [List of Fluent + custom components]
- **Custom Elements**: [Any custom components with justification]
- **Responsive Behavior**: [How pattern adapts across breakpoints]

### Reuse Guidelines
- **When to use**: [Appropriate contexts for this pattern]
- **Variations**: [Acceptable modifications]
- **Dependencies**: [What this pattern requires]
```

### 7. Custom Component Documentation (Specialist Action)

Specialist automatically identifies and documents custom components:

```markdown
### Custom Components in this Pattern
- **CustomCard**: Extends Fluent Card with hover animations (see `/src/components/CustomCard.tsx`)
- **Reason**: Fluent Card doesn't support scale transforms on hover
- **Technical Debt**: Medium (could be addressed with future Fluent enhancements)
```

### 8. Output Report (Specialist Summary)

Specialist provides this standardized summary after documentation:

```markdown
## Design Intent Documentation Complete

### Design Dialect Captured
- [Pattern]: [Custom decision] documented at `/design-intent/[path]`
- [Pattern]: [Custom decision] documented at `/design-intent/[path]`

### Design System Artifacts Skipped  
- [Standard element]: [Reason why not documented]
- [Standard element]: [Reason why not documented]

### Files Created/Updated
- Created: `/design-intent/patterns/[pattern].md`
- Updated: `/design-intent/foundations/[property].md`

### Custom Components Found
- CustomCard: Hover animations (technical debt: medium)

### Future Consistency
These patterns can now be referenced by future features for consistency.
```

## Important Notes

1. **Only document after success**: This command should only run when user is satisfied with results
2. **Design dialect focus**: Ignore standard design system elements
3. **Proven patterns only**: Document what actually worked, not theoretical specs
4. **Reuse orientation**: Write documentation to help future implementations
5. **Custom component tracking**: Always note custom components for technical debt management

## Examples

### Example 1: Global Documentation
```
User: "Perfect! This gallery looks exactly right. /document-intent"

AI: "Documenting design dialect patterns from current implementation...

✓ Gallery-Layout: 3-card grid with 24px gaps documented
✓ Custom-Spacing: 48px section breaks documented  
✓ Card-Composition: Fluent Card + custom header pattern documented
✓ Custom component found: CustomCard (hover animations)

Design dialect captured in:
- /design-intent/patterns/gallery-layout.md
- /design-intent/foundations/custom-spacing.md"
```

### Example 2: Contextual Documentation
```
User: "The card hover effect is perfect now. /document-intent hover-states"

AI: "Documenting hover-states pattern only...

✓ Hover-States: Scale transform with 0.2s ease documented
✓ Custom component: CustomCard for hover animations

Design dialect captured in:
- /design-intent/patterns/hover-states.md"
```

## Integration

This command automatically invokes the Design Intent Specialist agent, which:
- Has specialized expertise in design dialect vs. design system distinctions
- Uses MCP tools (Figma, Fluent UI) for enhanced extraction when needed
- Maintains consistency with Constitution Article VII (implementation-first documentation)
- Integrates with custom component tracking system for technical debt management
- Ensures documented patterns are properly formatted for future feature consistency