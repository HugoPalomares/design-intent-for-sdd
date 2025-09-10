# Pattern: Component Extension Strategy

## Context
Building new features and pages while maintaining consistency across application

## Decision
Extend and reuse existing components rather than creating new ones from scratch

## When to Use
- **Similar functionality**: New feature needs functionality similar to existing component
- **Shared design patterns**: Visual treatment should match established components
- **Related data structures**: Working with same or similar data types
- **Consistent user expectations**: Users should experience familiar interaction patterns

## Components
Existing components that commonly get extended: `NavigationHeader`, `AgentHeader`, `DataTable`, `L1Layout`, `L2Layout`, elevated containers

## Why
Faster development, consistent behavior, centralized maintenance - changes to core components propagate automatically to all usage contexts

## Dependencies
Shared component library, established design patterns, backward compatibility requirements

---

## Usage Guidelines

### Extension Strategies
- **Prop-based extensions**: Add optional props for new functionality
- **Conditional rendering**: Extend behavior without breaking existing usage
- **Style overrides**: Allow customization while maintaining base styles

### When NOT to Extend
- Fundamentally different purpose
- Extension would compromise existing usage
- Single-use specialized cases
- Performance considerations with unnecessary overhead

## Examples

- **Headers**: `AgentHeader` extended to support owned agents with optional metadata
- **Layout**: `L1Layout`/`L2Layout` reused across different page types
- **Data display**: `DataTable` extended for various content types while maintaining consistent behavior