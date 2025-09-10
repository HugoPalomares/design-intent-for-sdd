# Foundation: Card Elevation Standard
**Context**: Unified elevation system for Microsoft My Account portal content containers  
**Custom Decisions**: Single shadow system with no hover effects for consistent elevation hierarchy

## Design Dialect

### Shadow Specification
- **Box Shadow**: `'0px 0.6px 1.8px 0px rgba(0,0,0,0.1), 0px 3.2px 7.2px 0px rgba(0,0,0,0.13)'`
- **Dual Layer System**: Combines subtle close shadow (0.6px/1.8px) with deeper ambient shadow (3.2px/7.2px)
- **Opacity Levels**: 10% opacity for close shadow, 13% opacity for ambient shadow
- **Color**: Pure black (`rgba(0,0,0,...)`) for neutral shadow that works on any background

### Hover Behavior Guidelines
- **No Hover Effects**: Avoid animations like `transform: translateY()` or shadow changes
- **Reasoning**: Prevents visual instability and maintains consistent depth perception
- **Exception**: Interactive cards may have subtle background color changes, but shadow remains static
- **Consistency**: All elevated surfaces maintain same visual weight regardless of interaction state

### Implementation Strategy
- **Use `div` containers**: Avoid Fluent `Card` component to prevent double padding issues
- **Background**: Pure white (`#ffffff`) for content contrast
- **Border Radius**: `4px` for consistent corner treatment matching other elevated elements
- **Overflow**: `hidden` to maintain clean container boundaries

## Technical Implementation

### Standard Elevated Container
```tsx
const elevatedContainerStyle = {
  backgroundColor: '#ffffff',
  borderRadius: '4px',
  boxShadow: '0px 0.6px 1.8px 0px rgba(0,0,0,0.1), 0px 3.2px 7.2px 0px rgba(0,0,0,0.13)',
  overflow: 'hidden',
  // No hover transforms or shadow changes
};
```

### CSS Implementation
```css
.elevated-container {
  background-color: #ffffff;
  border-radius: 4px;
  box-shadow: 0px 0.6px 1.8px 0px rgba(0,0,0,0.1), 
              0px 3.2px 7.2px 0px rgba(0,0,0,0.13);
  overflow: hidden;
}

/* Explicitly avoid hover effects */
.elevated-container:hover {
  /* Do not change box-shadow */
  /* Do not apply transform: translateY() */
}
```

### Fluent UI makeStyles Pattern
```tsx
const useStyles = makeStyles({
  elevatedCard: {
    backgroundColor: '#ffffff',
    borderRadius: '4px',
    boxShadow: '0px 0.6px 1.8px 0px rgba(0,0,0,0.1), 0px 3.2px 7.2px 0px rgba(0,0,0,0.13)',
    overflow: 'hidden',
    padding: tokens.spacingVerticalL,
  },
  // Interactive content inside can have hover effects
  interactiveContent: {
    '&:hover': {
      backgroundColor: tokens.colorNeutralBackground1Hover,
    }
  }
});
```

## Consistency with Table Containers

### Matching Elevation Levels
- **Data Tables**: Use same shadow specification for table container elevation
- **Card Groups**: Individual cards within groups should use identical shadow
- **Content Sections**: Any elevated content area should match this specification
- **Visual Hierarchy**: Same elevation = same importance level in content hierarchy

### Implementation Alignment
```tsx
// Table container elevation
const tableContainerStyle = {
  backgroundColor: '#ffffff',
  borderRadius: '4px',
  boxShadow: '0px 0.6px 1.8px 0px rgba(0,0,0,0.1), 0px 3.2px 7.2px 0px rgba(0,0,0,0.13)',
  overflow: 'hidden',
};

// Card elevation (should match exactly)
const cardElevationStyle = {
  backgroundColor: '#ffffff',
  borderRadius: '4px',
  boxShadow: '0px 0.6px 1.8px 0px rgba(0,0,0,0.1), 0px 3.2px 7.2px 0px rgba(0,0,0,0.13)',
  overflow: 'hidden',
};
```

## When to Apply Elevation

### Use Cases
- **Data Tables**: Complex tabular content needs visual separation
- **Content Cards**: Information groupings that require distinction from page background  
- **Form Sections**: Multi-field forms benefit from contained presentation
- **Widget Areas**: Interactive content areas that form cohesive units
- **Detail Panels**: Secondary content that supports primary page information

### When NOT to Apply
- **Page Headers**: Should integrate directly with page background
- **Navigation Elements**: Must feel connected to overall page structure
- **Simple Text Blocks**: Basic content doesn't require visual separation
- **Inline Elements**: Content that flows within text or simple layouts

## Background Context Requirements

### L1 Pages (Grey Background)
- **Shadow Application**: Full shadow specification provides clear separation
- **Background Contrast**: White elevated containers stand out clearly against grey page background
- **Visual Depth**: Shadow creates appropriate depth perception

### L2 Pages (White Background)  
- **Alternative Treatment**: Consider border treatment instead of shadow to avoid floating appearance
- **Context Awareness**: Same elevation standard but may need different visual treatment
- **Consistency Override**: If shadow is used, must be identical specification

## Accessibility Considerations

### Visual Hierarchy
- **Consistent Depth**: Same shadow = same content importance level
- **Clear Boundaries**: Elevation helps users understand content groupings
- **Focus Clarity**: Interactive elements within elevated containers have clear focus states

### Performance Considerations
- **Static Shadows**: No hover animations reduce GPU load and prevent visual distraction
- **Consistent Rendering**: Single shadow specification ensures uniform browser rendering
- **Reduced Complexity**: Simpler CSS reduces maintenance overhead

## Key Design Decisions

1. **No Hover Effects**: Prevents visual instability and maintains consistent depth perception
2. **Dual Shadow System**: Combines subtle and ambient shadows for natural depth appearance  
3. **Static Elevation**: Same visual weight regardless of interaction state
4. **White Background**: Provides optimal contrast for content readability
5. **4px Border Radius**: Consistent with other elevated elements in the system
6. **Div over Card**: Avoids double padding issues while maintaining full control over styling

## Related Patterns

- **[Component: Elevated Container](../components/elevated-container.md)**: Context-aware elevation that uses this shadow system
- **[Component: DataTable](../components/data-table.md)**: Table containers that implement this elevation standard
- **[Pattern: Page Template System](../patterns/page-template-system.md)**: L1/L2 pages that provide context for elevation decisions