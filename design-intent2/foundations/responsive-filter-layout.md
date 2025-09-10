## Foundation: Responsive Filter Layout
**Context**: Standard approach for search and filter controls across data views
**Custom Decisions**: Mobile-first input prioritization with structured responsive behavior

### Design Dialect
- **Desktop Layout**: Horizontal flex with search growing, fixed-width dropdowns (reasoning: optimal space utilization)
- **Mobile Transformation**: Search takes full width row 1, dropdowns share row 2 at 50% each (reasoning: search is primary action, secondary filters get equal treatment)
- **Gap Consistency**: Standard Fluent spacingHorizontalM for desktop, spacingVerticalM for mobile (reasoning: maintain rhythm while adapting to layout changes)
- **Dropdown Sizing**: Calc(50% - 6px) to account for gap spacing (reasoning: precise alignment without overlap)
- **Order Control**: CSS order property to reorganize elements on mobile (reasoning: semantic HTML with visual reordering)

### Implementation
- **Components Used**: Fluent SearchBox, Dropdown components
- **Responsive Strategy**: CSS media queries with flex layout adaptation
- **Gap Management**: Fluent spacing tokens with mathematical gap compensation

### Reuse Guidelines
- **When to use**: Any page with search + multiple filter controls
- **Variations**: Number of dropdowns can vary, search always takes priority on mobile
- **Dependencies**: Requires 1023px breakpoint consistency, Fluent spacing tokens