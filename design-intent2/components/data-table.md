# Pattern: DataTable

## Context
Reusable data table component used throughout applications for displaying structured data with loading states, infinite scroll, and filtering

## Decision
Fluent Table-based implementation with integrated skeleton loading, intelligent state management, and flexible column sizing

## When to Use
- **Structured data display**: Lists, directories, catalogs requiring tabular presentation
- **Interactive data**: Content that users scan, sort, filter, or select
- **Performance requirements**: Large datasets needing loading states and pagination
- **Consistent behavior**: Standardized table interactions across application

## Components
- `DataTable` - Main reusable table component
- `Skeleton` loading states for initial and infinite scroll loading
- Fluent Table components for base functionality

## Why
Migrated from DataGrid to Table for better column sizing control; skeleton loading prevents jarring content shifts; intelligent state management optimizes perceived performance; flexible column sizing adapts to content naturally

## Dependencies
Fluent UI Table components, Skeleton components, infinite scroll utilities, responsive breakpoint system

---

## Usage Guidelines

### Loading State Strategy
- **First visit**: Full skeleton (8 rows) for initial impression
- **Return visits**: No skeleton, direct data display for faster perceived performance  
- **Filter changes**: Instant update without loading indicators
- **Infinite scroll**: Bottom spinner only, preserves existing content

### Column Sizing Standards
- **Flexible columns**: Natural content-based sizing using CSS table-layout auto
- **Actions column**: Fixed width for consistent button placement
- **No resizing**: Removed for simpler, predictable layouts
- **Semi-bold headers**: Clear hierarchy without overwhelming content

### Responsive Behavior
- **Horizontal scroll**: Container-level scroll with configurable minimum width
- **Default minimum**: 800px ensures content legibility
- **Mobile adaptation**: Adjustable minWidth based on content needs

## Examples

- **Agent lists**: Directory tables with status, actions, metadata
- **Request queues**: Pending items with filtering and infinite scroll
- **Audit logs**: Historical data with sorting and search capabilities