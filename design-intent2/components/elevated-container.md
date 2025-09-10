# Pattern: Elevated Container

## Context
Content requiring visual separation and hierarchy within page layouts

## Decision
Smart container that adapts elevation style based on page context - shadows on grey backgrounds, borders on white backgrounds

## When to Use
- **Data tables**: Complex tabular data needs separation from page background
- **Form sections**: Multi-field forms benefit from contained presentation
- **Content blocks**: Dense information requiring visual grouping
- **Widget collections**: Multiple related components forming cohesive units

## Components
- `ElevatedContainer` - Context-aware container component

## Why
Prevents nested elevation problems - only one layer of visual depth per view; automatically adapts to maintain appropriate contrast in different page contexts

## Dependencies
Page layout context (L1/L2), design tokens for consistent styling

---

## Usage Guidelines

### Context-Aware Behavior
- **In L1 (grey background)**: Uses shadow elevation for separation
- **In L2 (white background)**: Uses border outline to avoid nested shadows
- **Single elevation layer**: Never nest elevated containers

### When NOT to Use
- Page headers or titles
- Simple text blocks
- Navigation elements
- Standalone buttons or single actions

## Examples

- **L1 pages**: Data tables, form sections, content widgets on grey background
- **L2 pages**: Secondary content groupings within white card layouts