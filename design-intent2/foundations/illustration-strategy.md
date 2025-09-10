# Foundation: Illustration Asset Strategy
**Context**: Consistent illustration asset management across Microsoft My Account portal
**Custom Decisions**: PNG assets over inline SVGs with standardized sizing and fallback handling

## Design Dialect

### Asset Format Standards
- **Format**: Use PNG files from `/spot-light/` folder instead of inline SVGs
- **Reasoning**: PNG assets provide consistent rendering, smaller bundle sizes, and easier maintenance
- **Source Location**: All illustrations stored in `/public/spot-light/` directory
- **Naming Convention**: Descriptive names with spaces (e.g., "Person Book.png", "Shield Person.png")

### Sizing Specifications

#### Small Icons (36px)
- **Use Cases**: Table icons, inline indicators, compact UI elements
- **Dimensions**: 36x36px consistently applied
- **Context**: Data tables, status indicators, navigation elements
- **Implementation**: Direct width/height CSS properties

#### Medium Illustrations (100px)  
- **Use Cases**: Card illustrations, feature highlights, section headers
- **Dimensions**: 100x100px for primary card content
- **Context**: Homepage cards, feature showcases, empty states
- **Implementation**: Consistent sizing maintains visual hierarchy

#### Large Illustrations (Custom)
- **Use Cases**: Hero sections, full-width banners, detailed feature explanations
- **Dimensions**: Context-dependent but maintain aspect ratios
- **Context**: Landing pages, onboarding flows, detailed help sections

### Implementation Patterns

#### Standard Image Component
```tsx
const IllustrationImage = ({ 
  name, 
  size = 100, 
  alt, 
  className 
}) => {
  return (
    <img
      src={`/spot-light/${name}.png`}
      alt={alt || name}
      width={size}
      height={size}
      className={className}
      onError={(e) => {
        // Fallback handling
        e.target.style.display = 'none';
      }}
    />
  );
};
```

#### Usage Examples
```tsx
// Small table icon
<IllustrationImage 
  name="Person Book" 
  size={36} 
  alt="User management" 
/>

// Card illustration
<IllustrationImage 
  name="Shield Person" 
  size={100} 
  alt="Security settings" 
/>

// Custom sizing
<IllustrationImage 
  name="AI Chat" 
  size={150} 
  alt="AI chat feature" 
/>
```

## Fallback Strategy

### Error Handling
- **Missing Assets**: Graceful degradation when PNG files are unavailable
- **Alt Text**: Always provide meaningful alternative text for accessibility
- **Display Management**: Hide broken images rather than showing broken image icons
- **Loading States**: Consider loading placeholders for large illustrations

### Accessibility Requirements
```tsx
// Comprehensive fallback pattern
const AccessibleIllustration = ({ name, size, alt, decorative = false }) => {
  const [hasError, setHasError] = useState(false);
  
  if (hasError) {
    return decorative ? null : (
      <div 
        style={{ width: size, height: size }}
        aria-label={alt}
        role="img"
      >
        {/* Optional text fallback */}
      </div>
    );
  }
  
  return (
    <img
      src={`/spot-light/${name}.png`}
      alt={decorative ? "" : alt}
      width={size}
      height={size}
      onError={() => setHasError(true)}
      aria-hidden={decorative}
    />
  );
};
```

## Asset Organization

### Directory Structure
```
/public/spot-light/
├── AI Chat Person.png
├── AI Chat.png
├── Person Book.png
├── Shield Person.png
├── Document People.png
└── [200+ other PNG assets]
```

### Naming Conventions
- **Descriptive Names**: "Person Book.png" not "icon1.png"
- **Space Separation**: Use spaces, not underscores or hyphens
- **Title Case**: Capitalize each word for consistency
- **Semantic Meaning**: Names should describe the illustration content

### Asset Maintenance
- **Version Control**: PNG assets tracked in git for consistency
- **Size Optimization**: Compress PNGs for web delivery
- **Batch Updates**: Update multiple related assets together
- **Documentation**: Keep asset inventory for reference

## Performance Considerations

### Loading Optimization
```tsx
// Lazy loading for large illustrations
const LazyIllustration = ({ name, size, alt }) => {
  return (
    <img
      src={`/spot-light/${name}.png`}
      alt={alt}
      width={size}
      height={size}
      loading="lazy"
      decoding="async"
    />
  );
};
```

### Bundle Size Benefits
- **External Assets**: PNG files don't increase JavaScript bundle size
- **Parallel Loading**: Images load independently from application code
- **Caching**: Browser caching works efficiently with static PNG assets
- **CDN Friendly**: Easy to serve from content delivery networks

## Usage Guidelines

### When to Use PNG Illustrations
- **Feature Cards**: Homepage and section illustrations
- **Status Indicators**: Visual representations of system states
- **Navigation Icons**: Menu and button illustrations
- **Empty States**: Friendly illustrations for zero-data scenarios
- **Onboarding**: Visual guides and feature explanations

### When to Consider Alternatives
- **Simple Icons**: Basic geometric icons might work as SVGs
- **Interactive Graphics**: SVGs better for hover states and animations
- **Scalable Logos**: Brand elements that need perfect scaling
- **Custom Graphics**: Illustrations that require frequent modifications

## Sizing Decision Framework

### Context-Based Sizing
```tsx
// Size mapping by context
const getIllustrationSize = (context) => {
  switch (context) {
    case 'table-icon':
      return 36;
    case 'card-primary':
      return 100;
    case 'card-secondary':
      return 80;
    case 'hero-section':
      return 200;
    case 'feature-highlight':
      return 150;
    default:
      return 100;
  }
};
```

### Responsive Considerations
```tsx
// Responsive illustration sizing
const ResponsiveIllustration = ({ name, alt }) => {
  const breakpoint = useBreakpoint();
  const isMobile = breakpoint === 'small' || breakpoint === 'medium' || breakpoint === 'large';
  
  return (
    <IllustrationImage
      name={name}
      size={isMobile ? 80 : 100}
      alt={alt}
    />
  );
};
```

## Technical Implementation

### Asset Loading Pattern
```tsx
const useIllustration = (name) => {
  const [loaded, setLoaded] = useState(false);
  const [error, setError] = useState(false);
  
  const src = `/spot-light/${name}.png`;
  
  useEffect(() => {
    const img = new Image();
    img.onload = () => setLoaded(true);
    img.onerror = () => setError(true);
    img.src = src;
  }, [src]);
  
  return { src, loaded, error };
};
```

### Consistent Styling
```tsx
const useIllustrationStyles = makeStyles({
  illustration: {
    display: 'block',
    objectFit: 'contain',
    objectPosition: 'center',
  },
  small: {
    width: '36px',
    height: '36px',
  },
  medium: {
    width: '100px',
    height: '100px',
  },
});
```

## Key Design Decisions

1. **PNG over SVG**: Better performance, consistent rendering, easier maintenance
2. **Centralized Directory**: Single source location for all illustration assets  
3. **Descriptive Naming**: Clear, semantic file names improve maintainability
4. **Standard Sizes**: 36px and 100px cover majority of use cases
5. **Graceful Fallbacks**: Error handling prevents broken visual experiences
6. **Accessibility First**: Meaningful alt text and proper ARIA attributes

## Related Patterns

- **[Component: DataTable](../components/data-table.md)**: Uses 36px illustrations for agent icons
- **[Pattern: Background Decoration](../patterns/background-decoration.md)**: May incorporate illustration assets
- **[Foundation: Responsive Breakpoints](./responsive-breakpoints.md)**: Influences responsive illustration sizing decisions