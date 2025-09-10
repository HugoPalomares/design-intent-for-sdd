# Foundation: Semi-Bold Link Typography

**Context**: Unified interactive element hierarchy across Microsoft My Account portal
**Custom Decisions**: All links use semi-bold font weight regardless of underline presence

## Design Dialect

- **Link Weight**: `tokens.fontWeightSemibold` applied to all interactive text elements
- **Universal Application**: Applies to links with and without underlines, in all contexts
- **Visual Hierarchy**: Creates clear distinction between static text and interactive elements
- **Accessibility Benefit**: Provides additional visual cue beyond color alone for link identification

## Implementation

- **Font Token**: `tokens.fontWeightSemibold` from Fluent UI design tokens
- **Application Method**: Direct style application or CSS class targeting all link elements
- **Coverage**: All interactive text including navigation links, action links, and in-content links
- **Consistency Rule**: Never use normal font weight for clickable text elements

## When to Use

- **All clickable text**: Any text element that triggers navigation or actions
- **Navigation elements**: Breadcrumbs, menu items, sidebar navigation
- **Action links**: "View details", "Edit", "Delete" and similar action text
- **Count displays**: User counts like "2 users", "1 group" that link to detailed views
- **In-content links**: Links within paragraphs, tables, or other content blocks

## When NOT to Use

- **Static text labels**: Non-interactive content like headings, descriptions
- **Button text**: Buttons have their own styling hierarchy (use button components)
- **Disabled elements**: Disabled links should follow disabled state styling
- **Secondary text**: Help text, captions, and supplementary information

## Examples

### Interactive Link Styling
```tsx
// Count links in access lists
<Link style={{ fontWeight: tokens.fontWeightSemibold }}>2 users</Link>
<Link style={{ fontWeight: tokens.fontWeightSemibold }}>1 group</Link>

// Agent name links in tables
<Text style={{ 
  fontWeight: tokens.fontWeightSemibold,
  color: tokens.colorBrandForeground1,
  cursor: 'pointer'
}}>Agent Name</Text>

// CSS approach for consistent application
'& a': {
  fontWeight: tokens.fontWeightSemibold,
}
```

### Usage in Different Contexts
```tsx
// Table headers (semi-bold for hierarchy)
'& .fui-TableHeaderCell': {
  fontWeight: tokens.fontWeightSemibold,
}

// Section titles with interactive elements
sectionTitle: {
  fontSize: tokens.fontSizeBase400,
  fontWeight: tokens.fontWeightSemibold,
  color: tokens.colorNeutralForeground1,
}
```

## Rationale

### Visual Hierarchy Benefits
- **Clearer Interaction Models**: Users immediately understand what's clickable
- **Improved Scannability**: Bold text draws attention to actionable elements
- **Consistent Expectations**: Uniform treatment reduces cognitive load

### Accessibility Advantages
- **WCAG Compliance**: Provides non-color dependent indication of interactivity
- **Screen Reader Support**: Semi-bold text often announced differently by assistive technology
- **Low Vision Support**: Increased font weight improves text visibility and contrast

### Design System Consistency
- **Token-Based**: Uses established Fluent UI design tokens for maintainability
- **Scalable Pattern**: Easy to apply across all components and contexts
- **Future-Proof**: Changes to font weight can be updated globally through tokens

## Related Patterns

- **[Component: DataTable](../components/data-table.md)**: Headers use semi-bold for visual hierarchy
- **[Pattern: Page Template System](../patterns/page-template-system.md)**: L1/L2 pages both follow this link styling
- **Button alternatives**: When text needs button-like treatment, consider actual Button components instead

## Technical Implementation

### Global CSS Rules
```css
/* Apply to all anchor elements */
a {
  font-weight: var(--fontWeightSemibold);
}

/* Fluent UI Link components */
.fui-Link {
  font-weight: var(--fontWeightSemibold);
}
```

### Component-Level Application
```tsx
const useStyles = makeStyles({
  interactiveText: {
    fontWeight: tokens.fontWeightSemibold,
    cursor: 'pointer',
    '&:hover': {
      textDecoration: 'underline',
    }
  }
});
```

### Key Decision
**Why semi-bold over bold?** Semi-bold provides sufficient visual weight to indicate interactivity without competing with true headings or creating excessive contrast that could feel overwhelming in data-dense interfaces.