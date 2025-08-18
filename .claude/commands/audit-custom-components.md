# Audit Custom Components Command

This command generates a technical debt report of all custom components in the project.

## Usage

```
/audit-custom-components
```

## Process

### 1. Scan for Custom Components
Search the codebase for:
- Files with "CUSTOM COMPONENT:" header comments
- Import statements for components prefixed with "Custom"
- Components in `/src/components/` that aren't from Fluent UI

### 2. Extract Component Information
For each custom component found, extract:
- **Component name**
- **Base component** (what Fluent UI component it extends/replaces)
- **Reason** for customization
- **Creation date**
- **File location**
- **Complexity level**

### 3. Assess Technical Debt Level
Categorize each component:
- **Low**: Minor styling that could easily become Fluent tokens
- **Medium**: Moderate customization that could be addressed in future Fluent updates
- **High**: Significant deviation requiring substantial custom code

### 4. Generate Report

Output format:

```markdown
## Custom Component Audit Report

**Total Custom Components**: [X]
**Overall Technical Debt Level**: [Low/Medium/High]
**Last Updated**: [Current Date]

### Component Details

#### CustomCard
- **Base**: @fluentui/react-components/Card
- **Reason**: Custom hover states with scale animation and nested action buttons
- **Created**: 2024-01-15
- **File**: `/src/components/CustomCard.tsx`
- **Technical Debt Level**: Medium (could be addressed with future Card enhancements)
- **Lines of Code**: ~85
- **Dependencies**: None

#### CustomNavigationPanel  
- **Base**: @fluentui/react-components/Nav
- **Reason**: Nested submenu support with custom icons and animation
- **Created**: 2024-01-18
- **File**: `/src/components/CustomNavigationPanel.tsx`
- **Technical Debt Level**: High (significant deviation from design system)
- **Lines of Code**: ~240
- **Dependencies**: Custom icon library

### Summary by Technical Debt Level

#### High Priority (Technical Debt: High)
- **CustomNavigationPanel**: Complex nested menu system
  - *Recommendation*: Consider contributing pattern to Fluent UI
  - *Impact*: High maintenance cost, potential breaking changes

#### Medium Priority (Technical Debt: Medium)  
- **CustomCard**: Hover animations and nested buttons
  - *Recommendation*: Monitor Fluent UI roadmap for Card enhancements
  - *Impact*: Moderate maintenance, low risk

#### Low Priority (Technical Debt: Low)
- [None found]

### Recommendations

1. **Priority for design system contribution**: CustomNavigationPanel (high complexity, reusable pattern)
2. **Monitor for future Fluent updates**: CustomCard (functionality might become available)
3. **Consider refactoring**: [Any components with high maintenance burden]
4. **Total custom components**: [X] ([assessment of whether this is reasonable for a prototype])

### Technical Debt Metrics
- **Total Lines of Custom Component Code**: [X]
- **Average Lines per Custom Component**: [X]
- **Components with External Dependencies**: [X]
- **Components Created This Month**: [X]

### Design System Gap Analysis
These custom components reveal gaps in Fluent UI:
- **Animation support**: Need for micro-interactions in Card component
- **Complex navigation**: Need for nested menu patterns in Nav component
- **[Other patterns]**: [Description of gap]
```

### 5. Actionable Insights

Include specific recommendations:

```markdown
### Next Steps

#### Immediate Actions
- [ ] Review high-debt components for refactoring opportunities
- [ ] Document any new patterns that could benefit future features
- [ ] Consider contributing complex patterns back to Fluent UI

#### Future Monitoring
- [ ] Check Fluent UI releases for features that could replace custom components
- [ ] Track maintenance time spent on custom components
- [ ] Reassess technical debt levels quarterly

#### Design System Feedback
Consider sharing these patterns with Fluent UI team:
- [Pattern 1]: [Business case for inclusion]
- [Pattern 2]: [Business case for inclusion]
```

## Expected Use Cases

### During Development
- Check technical debt before major features
- Identify patterns that could be standardized
- Make decisions about custom vs. existing components

### Project Health Checks
- Monthly/quarterly technical debt assessment
- Planning refactoring efforts
- Justifying design system contributions

### Handoff Documentation
- New developer onboarding
- Technical debt documentation for stakeholders
- Planning future architecture decisions

## Integration

This command works with:
- Custom component tracking system (header documentation)
- Design intent documentation (references custom components)
- Technical debt management workflows
- Design system gap analysis

## Example Output

```
/audit-custom-components

## Custom Component Audit Report

**Total Custom Components**: 3
**Overall Technical Debt Level**: Medium
**Last Updated**: 2024-01-20

### Component Details

#### CustomCard
- **Base**: @fluentui/react-components/Card
- **Reason**: Custom hover states with scale animation
- **Technical Debt Level**: Medium
- **Recommendation**: Monitor Fluent Card roadmap

#### CustomNavigationPanel
- **Base**: @fluentui/react-components/Nav  
- **Reason**: Nested submenu support
- **Technical Debt Level**: High
- **Recommendation**: Consider design system contribution

#### CustomButton
- **Base**: @fluentui/react-components/Button
- **Reason**: Custom loading state with spinner positioning
- **Technical Debt Level**: Low
- **Recommendation**: Could be replaced with Fluent Button variants

### Summary
Total technical debt is manageable for a prototype. CustomNavigationPanel should be prioritized for refactoring or design system contribution.
```