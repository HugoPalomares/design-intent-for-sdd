## Pattern: Responsive Tab Overflow
**Context**: TabList that shows overflow menu when tabs don't fit available space
**Custom Decisions**: Custom overflow menu implementation with visibility detection

### Design Dialect
- **Overflow Trigger**: MoreHorizontal bundled icon for overflow menu (reasoning: clear universal symbol for "more options")
- **Visibility Logic**: Hide overflow menu when not needed using useIsOverflowItemVisible (reasoning: clean interface without unnecessary elements)
- **Menu Integration**: Standard Fluent Menu pattern for overflow items (reasoning: consistent with platform patterns)
- **Tab Selection**: Maintains selected state and onTabSelect callback integration (reasoning: seamless UX regardless of tab location)

### Implementation
- **Components Used**: Fluent TabList, Overflow, OverflowItem, Menu components
- **Custom Elements**: OverflowMenuItem component with visibility detection logic
- **Responsive Behavior**: Automatically shows/hides overflow based on available space

### Reuse Guidelines
- **When to use**: Any TabList that might have too many tabs for smaller screens
- **Variations**: Icon can be customized, menu styling follows Fluent patterns
- **Dependencies**: Requires Fluent Overflow components, proper tab data structure