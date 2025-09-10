# Pattern: Menu Actions

## Context
Action menus throughout applications for table actions, navigation options, and contextual commands

## Decision
Prefer MenuButton component over Button+Menu combinations for cleaner implementation and better accessibility

## When to Use
- **Table row actions**: "..." menus for individual items in data tables
- **Navigation headers**: Dropdown menus in page headers  
- **Standard action menus**: Any menu where trigger is a simple button
- **Accessibility priority**: When reliable keyboard and screen reader support is needed

## Components
- `MenuButton` - Preferred integrated trigger and menu component
- `Button` + `Menu` - Legacy pattern for complex custom styling needs

## Why
MenuButton provides cleaner implementation with fewer components, automatic ARIA labeling, built-in keyboard navigation, and consistent visual treatment across the application

## Dependencies
Fluent UI Menu components, established appearance and sizing standards

---

## Usage Guidelines

### MenuButton Appearances
- **`transparent`**: Table actions, subtle menu triggers
- **`outline`**: Primary navigation actions, prominent menu buttons
- **`subtle`**: Secondary menu triggers, toolbar actions

### Size Guidelines
- **Standard**: Table actions, inline menus, compact interfaces
- **`large`**: Navigation headers, primary page actions
- **Match context**: Align with surrounding interactive elements

### When to Use Button+Menu Instead
- Custom trigger styling beyond MenuButton appearance options
- Non-button trigger elements (images, icons)
- Legacy compatibility requirements

## Examples

- **Table actions**: Transparent MenuButton with MoreHorizontal icon
- **Navigation headers**: Large outline MenuButton with "Manage" text
- **Toolbar actions**: Subtle MenuButton for secondary options