# Foundation: Custom Responsive Breakpoint Strategy

**Context**: Navigation and layout behavior for Microsoft My Account portal
**Custom Decisions**: Mobile navigation triggers at extraLarge (1024px+) instead of standard large breakpoint

## Design Dialect

- **Mobile Navigation Trigger**: extraLarge breakpoint (1024px+) instead of typical 768px
- **Reasoning**: Content density requirements need more horizontal space before switching to mobile patterns
- **Visual Impact**: Desktop navigation remains visible longer, accommodating wider content layouts
- **User Benefit**: Reduces premature mobile patterns on tablets and small laptops

## Implementation

- **Components Used**: Custom useBreakpoint hook with modified breakpoint logic
- **Custom Elements**: 
  - Modified isMobile calculation: `breakpoint === 'small' || breakpoint === 'medium' || breakpoint === 'large'`
  - Reason: Standard Fluent breakpoints don't accommodate our content density needs
- **Responsive Behavior**: Navigation drawer switches to overlay mode only below 1024px

## Reuse Guidelines

- **When to use**: All navigation and layout responsive decisions across the portal
- **Consistency Rule**: Any component checking for mobile/desktop must use this same breakpoint logic
- **Dependencies**: useBreakpoint hook, must be consistent across all layout components

## Technical Implementation

### Breakpoint Detection
```tsx
const breakpoint = useBreakpoint();
const isMobile = breakpoint === 'small' || breakpoint === 'medium' || breakpoint === 'large';
```

### Breakpoint Ranges
```tsx
const breakpoints = {
  small: { min: 320, max: 479 },      // Mobile
  medium: { min: 480, max: 639 },     // Large mobile
  large: { min: 640, max: 1023 },     // Tablet
  extraLarge: { min: 1024, max: 1365 }, // Desktop (triggers non-mobile)
  // ... larger breakpoints remain desktop
};
```

### Navigation Logic
```tsx
// Navigation drawer type
const drawerType = isMobile ? 'overlay' : 'inline';

// Navigation visibility
const isNavOpen = isMobile ? mobileNavOpen : true;
```

### Design Decision Rationale
This breakpoint choice accommodates modern tablet usage patterns and ensures content doesn't feel cramped on devices like iPad Pro (1024px width). Users get desktop-class navigation until screen space truly requires mobile patterns.