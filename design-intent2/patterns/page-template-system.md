# Pattern: Page Template System

## Context
Core information architecture for multi-page applications with navigation and content hierarchy

## Decision
Two-tier page hierarchy using grey background for overview pages and white card container for detail pages

## When to Use
- **L1 (Grey background)**: Landing pages, lists, dashboards, galleries, navigation hubs - anywhere users scan and choose their next destination
- **L2 (White card)**: Detail views, forms, settings, focused tasks - anywhere users need concentrated workspace separate from navigation
- **Key rule**: Ask "Is this overview or detail?" - the answer determines the template

## Components
- `L1Layout` - Grey background overview template
- `L2Layout` - White card detail template

## Why
Creates clear visual and cognitive distinction that users learn once and apply everywhere. Grey = browse/navigate, white card = focus/work. Prevents navigation complexity and cognitive overload.

## Dependencies
React Router nested layouts, responsive breakpoint system, navigation context for mobile/desktop states

---

## Usage Guidelines

- Never create pages without choosing L1 or L2 template
- URL structure follows pattern: `/` for home, `/section` for L1s, `/section/detail` for L2s  
- Both templates maintain visual consistency with 1300px max-width centering
- L1 uses elevated containers for complex content like tables
- L2 provides infinite-extension white card workspace

## Examples

- **L1 pages**: Account dashboard, subscription list, device overview, billing history
- **L2 pages**: Edit profile form, subscription details, device settings, payment method setup