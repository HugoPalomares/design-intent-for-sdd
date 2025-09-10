# Pattern: L2 Mobile Space Optimization

**Context**: L2 detail pages on mobile devices (< 1024px breakpoint)
**Custom Decisions**: Maximize content space by eliminating unnecessary padding while maintaining visual hierarchy

## Design Dialect

### Space Maximization Strategy
- **Flush card edges**: White card extends to screen edges (0px wrapper padding)
- **Reasoning**: On mobile, 16px side margins waste ~10% of screen width just to show card edges
- **Visual impact**: Creates immersive detail view that maximizes content area

### Asymmetric Padding Pattern
- **Card padding**: 24px vertical, 16px horizontal (instead of uniform 24px)
- **Reasoning**: Maintains comfortable vertical rhythm while reclaiming 16px horizontal space
- **Content gain**: ~5% more horizontal space for content without sacrificing readability

### Navigation Compensation
- **Hamburger padding**: Independent 16px horizontal padding
- **Reasoning**: When card is flush, hamburger needs its own spacing to avoid cramped appearance
- **Visual balance**: Maintains touch target size and visual breathing room

### Border Radius Adaptation
- **Mobile**: 0px border radius when flush to edges
- **Desktop**: 12px 12px 0 0 (top corners only)
- **Reasoning**: Rounded corners look broken when card touches screen edges

## Implementation

### Components Used
- **L2Layout**: Standard Fluent layout with custom responsive adjustments
- **No custom components**: Achieved through responsive CSS only

### Responsive Behavior
```css
/* Mobile (<1024px) */
.contentWrapper {
  padding: 0; /* Remove wrapper padding */
}

.cardContainer {
  borderRadius: 0; /* No rounded corners */
  padding: 24px 16px; /* Asymmetric padding */
}

.hamburgerContainer {
  paddingLeft: 16px;
  paddingRight: 16px;
}

/* Desktop (≥1024px) */
/* Standard behavior with 1300px max-width and 24px uniform padding */
```

## Reuse Guidelines

### When to Use
- **All L2 detail pages**: Apply consistently to maintain pattern recognition
- **Mobile-first contexts**: When content space is premium
- **Form pages**: Where input fields benefit from extra width

### When NOT to Use
- **L1 overview pages**: They don't have card containers
- **Modal dialogs**: They have their own spacing rules
- **Embedded content**: When L2 content appears in other contexts

### Variations
- **Tablet (768px-1023px)**: Could use intermediate padding (20px) if needed
- **Landscape mobile**: Pattern still applies, maintains consistency

## Impact Metrics

- **Content space gain**: ~10% more horizontal space on mobile
- **Touch target maintained**: Hamburger still has 44px+ touch area
- **Readability preserved**: 16px horizontal padding meets minimum requirements
- **Visual hierarchy intact**: White card still creates focus area

## Dependencies

- **L2Layout component**: Implements responsive behavior
- **1024px breakpoint system**: Triggers mobile optimizations
- **Page template system**: Part of larger L1/L2 architecture