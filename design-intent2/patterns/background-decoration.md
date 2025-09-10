# Pattern: Background Decoration

**Context**: Decorative visual effects across Microsoft My Account portal pages
**Custom Decisions**: Use CSS background properties directly on containers instead of separate positioned elements

## Design Dialect

#### CSS Background Approach (Preferred)
- **Implementation**: `backgroundImage`, `backgroundSize`, `backgroundPosition` properties on layout containers
- **Positioning**: `fixed` attachment prevents scrolling with content
- **Performance**: Single DOM element, browser-optimized background rendering
- **Layering**: Natural CSS stacking without z-index complexity
- **Maintainability**: Contained within container styling, easy to modify or remove

#### Positioned Element Approach (Avoid)
- **Implementation**: Separate `<div>` or `<img>` elements with absolute positioning
- **Complexity**: Requires z-index management and precise positioning calculations
- **Performance**: Additional DOM elements, potential layout thrashing
- **Maintenance**: Separate elements to track, position, and coordinate with content

## When to Use CSS Background Properties

- **Decorative effects**: Visual enhancements that don't interfere with content accessibility
- **Full-page treatments**: Effects that span entire viewport or large layout areas
- **Non-interactive graphics**: Images or patterns that users don't need to interact with
- **Performance-critical contexts**: When minimizing DOM complexity is important
- **Responsive designs**: When decoration needs to scale or adapt to different screen sizes

## When to Use Positioned Elements

- **Interactive decorations**: Graphics that users need to click or interact with
- **Complex layering**: When decoration needs to appear between content layers
- **Dynamic content**: When decoration changes based on user interactions or data
- **Accessibility requirements**: When decoration provides meaningful information to screen readers

## Implementation Examples

### Portal Layout Background (Preferred Pattern)
```tsx
// PortalLayout.tsx - Background applied directly to layout container
const useStyles = makeStyles({
  portalLayout: {
    fontFamily: 'Segoe UI, system-ui, sans-serif',
    backgroundColor: '#f5f5f5',
    // CSS background properties for decoration
    backgroundImage: 'url(/images/page-background-effect.png)',
    backgroundSize: 'cover',
    backgroundPosition: 'center top', 
    backgroundRepeat: 'no-repeat',
    backgroundAttachment: 'fixed', // Effect doesn't scroll with content
    minHeight: '100vh',
    display: 'flex',
    flexDirection: 'column',
  },
  // Layouts inherit transparent backgrounds to show effect
  content: {
    backgroundColor: 'transparent', // Let background show through
    flex: 1,
  }
});
```

### Transparent Layout Strategy
```tsx
// Child layouts made transparent to reveal background decoration
const useStyles = makeStyles({
  l1Content: {
    backgroundColor: 'transparent', // Was #f5f5f5, now transparent
    padding: tokens.spacingVerticalXL,
  },
  l2Content: {
    backgroundColor: 'transparent', // Let portal background show
    flex: 1,
  }
});
```

### Alternative Positioned Approach (When Necessary)
```tsx
// Only use when CSS background properties are insufficient
const useStyles = makeStyles({
  container: {
    position: 'relative',
    minHeight: '100vh',
  },
  backgroundDecoration: {
    position: 'fixed',
    top: 0,
    left: 0,
    width: '100%',
    height: '100%',
    backgroundImage: 'url(/images/decoration.png)',
    backgroundSize: 'cover',
    pointerEvents: 'none', // Important: Don't block content interaction
    zIndex: -1, // Behind all content
  }
});

// JSX - Additional DOM element required
<div className={styles.container}>
  <div className={styles.backgroundDecoration} aria-hidden="true" />
  <main>Content goes here</main>
</div>
```

## Background Property Guidelines

### Background Size Options
```css
/* Cover: Scales to cover entire container (may crop) */
background-size: cover;

/* Contain: Scales to fit entirely within container */  
background-size: contain;

/* Fixed dimensions: Specific size control */
background-size: 1200px 800px;

/* Responsive: Percentage-based scaling */
background-size: 100% auto;
```

### Background Position Control
```css
/* Alignment keywords */
background-position: center top;    /* Centered horizontally, top vertically */
background-position: right bottom;  /* Bottom-right corner */

/* Precise positioning */
background-position: 50% 20%;      /* 50% from left, 20% from top */
background-position: 100px 50px;   /* Fixed pixel offset */
```

### Background Attachment Behavior
```css
/* Fixed: Background doesn't scroll with content (preferred for decoration) */
background-attachment: fixed;

/* Scroll: Background scrolls with content (default) */
background-attachment: scroll;

/* Local: Background scrolls with element's content */
background-attachment: local;
```

## Performance Benefits

#### CSS Background Advantages
- **Browser optimization**: Native rendering optimizations for background images
- **Reduced DOM complexity**: No additional elements to manage
- **Simplified event handling**: No interference with content interactions
- **Memory efficiency**: Browser handles image caching and rendering automatically

#### Layout Performance
- **No reflow triggers**: Background changes don't affect document flow
- **GPU acceleration**: Background images often GPU-accelerated by browsers
- **Reduced paint operations**: Changes contained within single element

## Responsive Considerations

### Mobile Adaptations
```tsx
const useStyles = makeStyles({
  container: {
    backgroundImage: 'url(/images/desktop-background.png)',
    // Mobile-specific background
    '@media (max-width: 768px)': {
      backgroundImage: 'url(/images/mobile-background.png)',
      backgroundPosition: 'center center', // Adjust positioning for mobile
      backgroundSize: 'cover', // Ensure full coverage on small screens
    }
  }
});
```

### High-DPI Display Support
```tsx
const backgroundImage = `
  url('/images/background.png'),
  url('/images/background@2x.png') 2x,
  url('/images/background@3x.png') 3x
`;

// Or using CSS image-set (when available)
backgroundImage: `
  -webkit-image-set(
    url('/images/background.png') 1x,
    url('/images/background@2x.png') 2x
  )
`;
```

## Accessibility Considerations

### Screen Reader Compatibility
```tsx
// Background images are automatically ignored by screen readers
const decorativeBackground = {
  backgroundImage: 'url(/images/decoration.png)',
  // No alt text needed - decoration is purely visual
};

// If background conveys meaning, provide alternative
<div 
  style={decorativeBackground}
  aria-label="Decorative background pattern"
  role="img"
>
  Content
</div>
```

### Motion Considerations
```tsx
// Respect user motion preferences
const useStyles = makeStyles({
  container: {
    backgroundImage: 'url(/images/static-background.png)',
    // Only animate if user hasn't reduced motion
    '@media (prefers-reduced-motion: no-preference)': {
      backgroundImage: 'url(/images/animated-background.gif)',
    }
  }
});
```

## Key Benefits

### Development Simplicity
- **Single responsibility**: Background styling contained within layout component
- **No positioning math**: Browser handles image positioning automatically
- **Declarative approach**: CSS properties clearly express intent
- **Easy modifications**: Change background by updating CSS properties only

### Maintainability Advantages
- **Centralized control**: All background styling in one location
- **No DOM coordination**: No need to sync positioned elements with content
- **Clear separation**: Decoration clearly separated from functional elements
- **Future flexibility**: Easy to change decoration approach without affecting content

### User Experience Benefits
- **Smooth performance**: Browser-optimized background rendering
- **No interaction blocking**: Background never interferes with content interaction
- **Consistent behavior**: Background behavior predictable across different contexts
- **Accessibility friendly**: Purely decorative backgrounds ignored by assistive technology

## Related Patterns

- **[Pattern: Page Template System](../patterns/page-template-system.md)**: L1/L2 layouts use transparent backgrounds to reveal portal decoration
- **[Component: Elevated Container](../components/elevated-container.md)**: White containers provide contrast against decorative backgrounds
- **[Foundation: Responsive Breakpoints](../foundations/responsive-breakpoints.md)**: Background images adapt to different screen sizes using media queries