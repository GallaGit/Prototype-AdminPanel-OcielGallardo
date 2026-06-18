# AgentHub Frontend Specification

## 1. Vision

AgentHub is a SaaS dashboard prototype for companies that rent configurable AI agents built from reusable skills. This frontend is a visual reference for future backend developers and stakeholders. The prototype must communicate product positioning, information architecture, and interactive states without relying on any server, API, or persistence layer.

The UI should feel production-oriented rather than tutorial-grade: dense enough for SaaS users, clear enough for demos, and polished enough to validate layout, hierarchy, and component behavior.

## 2. Project Goal

Build a visually complete static frontend using only:

- HTML
- TailwindCSS via CDN
- Vanilla JavaScript

Constraints:

- No backend
- No APIs
- No frameworks
- No build step
- All data hardcoded in JavaScript
- All interactions simulated on the client side

Primary objective:

- Provide a high-fidelity dashboard prototype that future backend developers can use as a reference for screens, data shapes, and UI states.

## 3. Deliverables

The implementation phase should produce the following minimum deliverables:

- A main dashboard entry page
- A reusable sidebar/topbar SaaS layout
- A hardcoded dataset representing agents, skills, teams, usage metrics, and invoices
- Interactive filtering/searching/sorting using Vanilla JavaScript
- At least one modal or drawer for detailed agent inspection
- Responsive behavior for desktop, tablet, and mobile

Recommended file structure for implementation:

- index.html
- styles.css
- app.js

Optional additional files only if needed:

- assets/* for logos or decorative SVGs

## 4. Product Narrative

The product story the UI must communicate:

- Companies subscribe to AgentHub.
- Each company can browse and activate AI agents.
- Each agent is assembled from skills such as summarization, ticket triage, CRM enrichment, onboarding, and reporting.
- Admins can inspect usage, seat allocation, status, and estimated monthly cost.
- Teams can review available skills, agent health, and recent operational activity.

The prototype is not a consumer marketplace. It is a B2B admin panel.

## 5. UX Direction

### Tone

- Professional
- Modern
- High information density
- Premium SaaS
- Calm but not bland

### Visual Style

- Light-first interface
- Strong card structure
- Soft gradients in hero/summary areas
- Distinct accent color for status and calls to action
- Rounded corners, subtle borders, layered surfaces

### Avoid

- Generic beginner dashboard look
- Default Tailwind-only appearance without customization
- Excessive animation
- Fake charts rendered as static images

## 6. Design System Specification

### Color Tokens

Define color intent through CSS variables and use them consistently.

Suggested palette intent:

- Background base: warm off-white or cool mist
- Surface: white
- Surface secondary: slightly tinted panel
- Primary accent: deep teal, blue-green, or cobalt
- Secondary accent: amber or coral for emphasis
- Success: green
- Warning: amber
- Danger: red
- Text primary: near-slate
- Text secondary: muted slate
- Border: low-contrast neutral

The final implementation may refine exact hex values, but the following contrast rules are mandatory:

- Primary text must meet readable contrast on white cards.
- Accent buttons must have strong contrast.
- Status pills must be distinguishable by both color and text.

### Typography

- Use a more distinctive web-safe or CDN-loaded font pairing than default sans.
- Suggested direction: one strong display face for headings and a readable sans for UI copy.
- Heading hierarchy must be obvious.
- Numeric metrics should have stronger visual weight and tighter tracking.

### Spacing

- Use a 4px or 8px spacing rhythm.
- Dashboard cards must have generous internal padding.
- Dense data areas such as tables may reduce vertical space while preserving readability.

### Radius and Shadow

- Card radius: medium to large
- Buttons and pills: medium radius
- Shadows: subtle, not floating excessively

## 7. Information Architecture

Implement the prototype as a single-page dashboard experience with internal sections, not multiple HTML pages.

Main layout areas:

1. Sidebar navigation
2. Top bar
3. Overview hero / summary section
4. KPI metrics row
5. Agent catalog section
6. Skills library section
7. Usage and billing section
8. Activity timeline / audit feed

## 8. Required Sections

### 8.1 Sidebar

Purpose:

- Provide product navigation and brand presence.

Required content:

- Logo or wordmark: AgentHub
- Workspace switcher mock element
- Navigation items:
  - Overview
  - Agents
  - Skills
  - Usage
  - Billing
  - Activity
- Bottom utility area:
  - Admin profile summary
  - Support link/button

Interaction:

- Clicking nav items scrolls or jumps to corresponding sections on the page.
- Active section state must be visually highlighted.

### 8.2 Top Bar

Required content:

- Current page title: Dashboard or Agent Operations
- Short descriptive subtitle
- Search field for agents/skills
- Notification bell mock button
- Primary CTA: Add Agent or New Deployment

Interaction:

- Search input filters the agent catalog live.

### 8.3 Overview Hero

Purpose:

- Quickly explain the workspace state.

Required content:

- Workspace/company name, example: Nova Industries
- Plan badge, example: Enterprise
- Short summary sentence about active automation footprint
- Summary chips:
  - Active agents count
  - Enabled skills count
  - Monthly automations or executions count
  - Estimated savings or ROI metric

Required visual treatment:

- A featured summary card with stronger styling than the rest of the page
- One secondary panel showing deployment health breakdown or plan utilization

### 8.4 KPI Metrics Row

At least four KPI cards:

- Active Agents
- Skills in Use
- Monthly Runs
- Avg. Success Rate
- Optional fifth: Seats Used or Monthly Spend

Each card must include:

- Label
- Large metric value
- Delta or comparison text
- Small contextual note

### 8.5 Agent Catalog

Purpose:

- Display rentable/configurable AI agents.

Required controls:

- Search input reuse from top bar or local search
- Status filter tabs or pills:
  - All
  - Active
  - Paused
  - Draft
- Sort dropdown:
  - Most Used
  - Highest ROI
  - Recently Updated

Required card fields per agent:

- Agent name
- Category or department
- Short description
- Status badge
- Skill tags
- Monthly runs
- Success rate
- Estimated monthly cost
- Owner/team
- Last updated

Required interactions:

- Clicking an agent opens a drawer or modal with more details.
- Filter and sort controls update the visible list without reload.

### 8.6 Agent Detail Drawer or Modal

This is mandatory.

It opens from the agent catalog and must show:

- Agent name and status
- Purpose description
- Assigned team
- Included skills
- Setup checklist or configuration summary
- Performance summary:
  - Runs
  - Accuracy/success rate
  - Escalation rate
  - Estimated savings
- Activity snippet or recent events
- CTA buttons such as Pause Agent, Duplicate, View Logs

Interaction behavior:

- Open on agent card click
- Close via close button, background click, or Escape key

### 8.7 Skills Library

Purpose:

- Show reusable skill building blocks.

Presentation:

- Grid of compact cards or pills grouped by category

Required fields:

- Skill name
- Category
- Compatibility or usage count
- Short explanation
- Availability state such as Included, Premium, Beta

Suggested categories:

- Support
- Sales
- Operations
- Knowledge
- Compliance

Optional interaction:

- Clicking a skill highlights related agents in the catalog.

### 8.8 Usage and Billing

Purpose:

- Simulate operational and commercial visibility.

Required sub-sections:

- Usage chart panel
- Seats or team allocation panel
- Billing snapshot panel

Because no chart library is required, build charts using HTML/CSS primitives.

Accepted chart approaches:

- Vertical bar chart using flex columns
- Segmented progress bars
- Sparkline-style faux chart built with divs

Required metrics:

- Monthly runs by team or by agent
- Plan utilization percent
- Current month spend
- Next invoice date

Billing snapshot must include:

- Plan name
- Seat count
- Add-on skills count
- Estimated monthly total

### 8.9 Activity Timeline

Purpose:

- Convey admin observability.

Required fields per item:

- Timestamp
- Event title
- Event description
- Actor or system source
- Severity/state marker

Suggested events:

- Agent paused
- New skill enabled
- Threshold reached
- Billing updated
- Success rate drop detected

## 9. Data Model Requirements

All data must be hardcoded in JavaScript using arrays/objects.

Minimum hardcoded collections:

### agents

Each agent object should include:

- id
- name
- team
- category
- description
- status
- skills (array)
- monthlyRuns
- successRate
- costPerMonth
- roiLabel
- owner
- lastUpdated
- savingsEstimate
- escalationRate
- setupItems (array)
- recentEvents (array)

Minimum quantity:

- 6 agents

### skills

Each skill object should include:

- id
- name
- category
- description
- tier
- usageCount
- compatibleTeams (array)

Minimum quantity:

- 10 skills

### activity

Each item should include:

- id
- timestamp
- title
- description
- source
- severity

Minimum quantity:

- 8 activity records

### billingSummary

Object fields:

- planName
- seatsUsed
- seatsTotal
- addOnSkills
- projectedSpend
- nextInvoiceDate
- utilizationPercent

## 10. Interaction Requirements

Mandatory interactive behaviors:

1. Live search over agent name, team, and skill names
2. Status filtering for agents
3. Sorting agents by one selected criterion
4. Open/close agent details drawer or modal
5. Navigation links scroll to sections
6. Mobile sidebar toggle

Optional but recommended behaviors:

1. Highlight agents when a skill is selected
2. Count updates in headers when filters are active
3. Animated number entrance on initial load

Interaction rules:

- All interactions must be instant and client-side.
- No broken controls are allowed.
- If a control is present, it must visibly do something.

## 11. Responsive Requirements

### Desktop

- Persistent left sidebar
- Multi-column dashboard layout
- Agent cards in 2 or 3 columns depending on width

### Tablet

- Narrower sidebar or collapsible nav
- KPI cards may wrap to 2 columns
- Drawer/modal width adjusted to viewport

### Mobile

- Sidebar becomes overlay panel or slide-in menu
- Top bar stacks appropriately
- Cards collapse to single column
- Tables should be converted to stacked cards if any tabular content is used

The prototype must remain visually coherent at approximately:

- 1440px
- 1024px
- 768px
- 390px

## 12. Accessibility Requirements

Minimum accessibility expectations:

- Semantic landmarks where practical
- Buttons must be real button elements
- Search must have a visible or accessible label
- Sufficient color contrast
- Focus-visible styling on interactive controls
- Modal/drawer close behavior accessible by keyboard

## 13. Content Requirements

The copy should read like an actual SaaS admin product.

Use English for the UI to match common B2B dashboard conventions.

Examples of acceptable naming:

- Support Triage Agent
- Revenue Recovery Agent
- Onboarding Concierge
- Policy Monitor
- Knowledge Router
- Ops Forecast Assistant

Avoid lorem ipsum.

All labels, empty states, helper text, and status text should be intentional.

## 14. Empty and Edge States

The implementation must consider at least these visual states:

### No search results

- Show a friendly empty state in the agent catalog
- Include a reset filters action

### Paused or draft agents

- These agents must look visually distinct from active agents

### Skill tier differences

- Premium and Beta skills should have differentiated badges

## 15. Animation Guidelines

Animations should be subtle and purposeful.

Allowed:

- Fade/slide entrance on load
- Hover lift on cards
- Drawer slide-in
- Small transitions on filters and pills

Avoid:

- Long looping animations
- Decorative motion unrelated to information hierarchy

## 16. Technical Implementation Notes

### HTML

- Keep the document structure clean and sectioned.
- Use IDs on major sections for navigation.
- Prefer reusable card patterns.

### TailwindCSS

- Use Tailwind via CDN.
- Extend styling with custom CSS variables and small handcrafted utility classes in styles.css.
- Do not rely exclusively on raw utility clutter when a reusable class improves clarity.

### JavaScript

- Centralize hardcoded data in app.js.
- Render repeated UI regions from data arrays where useful, especially agent cards, skill cards, and activity items.
- Keep state simple, for example:
  - searchTerm
  - selectedStatus
  - selectedSort
  - selectedSkill
  - activeAgentId

Recommended JS responsibilities:

- Render UI from data
- Bind event listeners
- Re-render filtered/sorted views
- Control drawer/modal state
- Control mobile navigation state

## 17. Suggested Page Structure

High-level DOM order:

1. App shell wrapper
2. Sidebar
3. Main content area
4. Top bar
5. Overview section
6. KPI section
7. Agent catalog section
8. Skills section
9. Usage/Billing section
10. Activity section
11. Agent detail drawer/modal

## 18. Definition of Done

The implementation is complete when:

- The page loads locally with no backend
- The dashboard looks like a credible SaaS admin panel
- All required sections are present
- The dataset is hardcoded and internally consistent
- Search, filter, sort, and modal/drawer interactions work
- Mobile layout is usable
- The result can be shown to backend developers as a UI reference

## 19. Non-Goals

Explicitly out of scope:

- Real authentication
- Real billing logic
- Real analytics
- Data persistence
- API integration
- Login flow
- Multi-page routing

## 20. Implementation Sequence

The implementation phase should follow this order:

1. Build the shell layout and navigation
2. Define the hardcoded dataset in JavaScript
3. Render overview and KPI cards
4. Render agent catalog with filters and sorting
5. Implement agent details drawer/modal
6. Render skills library
7. Render usage and billing visuals
8. Render activity timeline
9. Add responsive behavior and final polish

## 21. QA Checklist

Before considering the implementation finished, verify:

- Search returns expected agents
- Status filters work correctly
- Sort order changes card order
- Agent modal/drawer always opens with matching content
- Empty search state appears correctly
- Mobile nav opens and closes correctly
- No console errors in normal use
- Layout remains stable across desktop and mobile widths

## 22. Final Guidance for the Implementing Developer

When implementing this prototype, optimize for clarity of product thinking over engineering abstraction. The goal is not to build a scalable component framework. The goal is to create a convincing, static, interactive visual spec that backend and product teams can inspect and discuss.