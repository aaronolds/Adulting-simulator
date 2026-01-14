# Work Items for Adulting Simulator Implementation

This document outlines the recommended work items (GitHub issues) to implement the Adulting Simulator design. Each item is structured as a self-contained task with clear acceptance criteria.

## 🛠️ Tech Stack Requirements

**Frontend (Required):**
- Next.js 14+ with App Router
- **TypeScript** (required for type safety)
- TailwindCSS for styling
- Recharts for data visualization

**Backend (Required):**
- **.NET Core 10** with **Minimal API**
- C# for backend logic
- Entity Framework Core (optional, for database)

**Architecture:**
- Frontend: TypeScript-based React application
- Backend: .NET Core 10 Minimal API for calculations and data management
- Communication: RESTful API between frontend and backend

---

## Phase 1: Project Setup & Foundation

### Issue 1: Initialize Next.js Frontend Project with TypeScript
**Priority:** High  
**Labels:** setup, infrastructure, frontend, typescript

**Description:**
Set up a new Next.js 14+ project with **TypeScript** support for the Adulting Simulator frontend application.

**Tasks:**
- Initialize Next.js project with TypeScript using `create-next-app`
- Ensure TypeScript is configured (tsconfig.json)
- Configure ESLint and Prettier for TypeScript
- Set up folder structure (components, app, lib, types, data)
- Add basic package.json scripts (dev, build, lint, type-check)
- Create .gitignore for node_modules and build artifacts

**Acceptance Criteria:**
- Project runs with `npm run dev`
- TypeScript compilation works without errors (`npm run type-check`)
- Basic folder structure is in place
- TypeScript strict mode is enabled

---

### Issue 2: Initialize .NET Core 10 Backend with Minimal API
**Priority:** High  
**Labels:** setup, infrastructure, backend, dotnet

**Description:**
Set up a new .NET Core 10 project using **Minimal API** pattern for the Adulting Simulator backend.

**Tasks:**
- Initialize .NET Core 10 project with Minimal API template
- Configure project structure (Services, Models, DTOs)
- Set up CORS for frontend communication (Next.js origin)
- Add necessary NuGet packages (if needed for JSON, validation, etc.)
- Configure appsettings.json for development and production
- Set up logging and error handling middleware
- Create .gitignore for bin, obj, and build artifacts
- Configure Swagger/OpenAPI for API documentation

**Acceptance Criteria:**
- Backend runs with `dotnet run`
- Minimal API health check endpoint responds successfully
- CORS is configured to allow frontend origin
- Swagger UI is accessible at /swagger endpoint
- Basic project structure follows Minimal API patterns

---

### Issue 3: Define TypeScript Types for Frontend
**Priority:** High  
**Labels:** foundation, typescript, frontend

**Description:**
Create **TypeScript** interfaces and types for all core game entities in the frontend application.

**Tasks:**
- Create TypeScript types for Job (salary, hourly wage, hours, pay frequency)
- Create TypeScript types for Tax Configuration (filing status, rates, brackets)
- Create TypeScript types for Benefits (health plans, 401k options)
- Create TypeScript types for Expenses (housing, transportation, subscriptions, etc.)
- Create TypeScript types for Life Events (probability, severity, cost)
- Create TypeScript types for Player State (income, expenses, savings, debt, credit score)
- Create TypeScript types for API request/response contracts

**Acceptance Criteria:**
- All TypeScript types are properly defined in `types/` directory
- Types match the design document requirements
- No TypeScript compilation errors
- Types are exported and can be imported throughout the application

---

### Issue 4: Define C# Models for Backend
**Priority:** High  
**Labels:** foundation, backend, dotnet, csharp

**Description:**
Create C# record types and DTOs in the **.NET Core 10** backend to match frontend TypeScript types.

**Tasks:**
- Create C# models for Job (salary, hourly wage, hours, pay frequency)
- Create C# models for Tax Configuration (filing status, rates, brackets)
- Create C# models for Benefits (health plans, 401k options)
- Create C# models for Expenses (housing, transportation, subscriptions, etc.)
- Create C# models for Life Events (probability, severity, cost)
- Create C# models for Player State (income, expenses, savings, debt, credit score)
- Create DTOs for API request/response contracts
- Ensure models use appropriate C# features (records, nullable reference types)

**Acceptance Criteria:**
- All C# models are properly defined in Models/ directory
- Models match TypeScript types for consistency
- Models follow C# naming conventions (PascalCase)
- No compilation errors
- DTOs are optimized for API serialization

---

### Issue 5: Create JSON Configuration Files for Game Data
**Priority:** High  
**Labels:** data, configuration

**Description:**
Set up JSON files containing game data like job listings, rent tiers, subscription prices, and tax rates. These will be used by both frontend and backend.

**Tasks:**
- Create `data/jobs.json` with sample jobs and salaries
- Create `data/housing.json` with rent tiers by city
- Create `data/subscriptions.json` with streaming/service options
- Create `data/taxes.json` with federal/state tax information
- Create `data/benefits.json` with health plan options
- Create `data/lifeEvents.json` with random event definitions

**Acceptance Criteria:**
- JSON files are valid and can be imported
- Data covers realistic ranges for all categories
- Data structure matches TypeScript types and C# models

---

### Issue 6: Implement Backend Calculation API with Minimal API
**Priority:** High  
**Labels:** feature, calculation, backend, dotnet

**Description:**
Build backend calculation service using **.NET Core 10 Minimal API** pattern for financial calculations.

**Tasks:**
- Create CalculationService for income, tax, and expense calculations
- Implement Minimal API endpoints:
  - POST /api/calculate/income - Calculate gross and net income
  - POST /api/calculate/taxes - Calculate tax deductions
  - POST /api/calculate/cashflow - Calculate monthly cash flow
  - GET /api/data/jobs - Get job listings
  - GET /api/data/expenses - Get expense options
- Implement request validation using Data Annotations
- Add error handling and structured logging
- Return consistent API response format
- Document endpoints with XML comments for Swagger

**Acceptance Criteria:**
- All Minimal API endpoints work correctly
- API returns proper HTTP status codes (200, 400, 500)
- Calculations match business logic requirements
- Endpoints are documented in Swagger/OpenAPI
- CORS allows frontend to call endpoints

---

## Phase 2: Core Game Logic

### Issue 7: Implement Income Calculation Engine (Backend)
**Priority:** High  
**Labels:** feature, calculation

**Description:**
Build the core logic for calculating gross pay based on salary or hourly wages.

**Tasks:**
- Create `lib/income.ts` with calculation functions
- Support annual salary conversion to monthly
- Support hourly wage calculation (hours × rate × 52 / 12)
- Handle different pay frequencies (weekly, biweekly, semimonthly, monthly)
- Add support for overtime calculations
- Add support for bonuses and commissions

**Acceptance Criteria:**
- Functions correctly calculate gross pay for all scenarios
- Unit tests pass for various income configurations
- Edge cases are handled (0 hours, negative values, etc.)

---

### Issue 8: Implement Tax Calculation System
**Priority:** High  
**Labels:** feature, calculation

**Description:**
Create a tax calculation engine that handles federal, state, and FICA taxes.

**Tasks:**
- Create `lib/taxes.ts` with tax calculation functions
- Implement simple percentage mode for basic tax calculation
- Implement bracket-based mode for advanced tax calculation
- Calculate FICA (Social Security + Medicare)
- Support different filing statuses (single, married)
- Support state tax selection
- Apply standard deduction when applicable

**Acceptance Criteria:**
- Tax calculations are mathematically correct
- Both simple and advanced modes work
- Unit tests verify calculations against known examples

---

### Issue 9: Implement Benefits Deduction System
**Priority:** Medium  
**Labels:** feature, calculation

**Description:**
Build the system for calculating and deducting benefits from gross pay.

**Tasks:**
- Create `lib/benefits.ts` with deduction functions
- Calculate health insurance premiums (various plan types)
- Calculate 401k contributions (percentage-based)
- Apply employer 401k matching when enabled
- Calculate net pay after all deductions

**Acceptance Criteria:**
- Benefit deductions are correctly calculated
- Employer match logic works as expected
- Net pay calculation is accurate

---

### Issue 10: Implement Expense Tracking System
**Priority:** High  
**Labels:** feature, calculation

**Description:**
Create logic for tracking and calculating monthly expenses.

**Tasks:**
- Create `lib/expenses.ts` with expense functions
- Handle fixed expenses (rent, insurance, internet)
- Handle variable expenses (groceries, utilities)
- Support roommate rent splitting
- Calculate transportation costs (bus, used car, new car)
- Track subscription services
- Calculate eating out vs cooking costs
- Handle debt payments (student loan, credit card, car loan)

**Acceptance Criteria:**
- All expense categories are properly tracked
- Variable expenses support ranges
- Total monthly expenses are calculated correctly

---

### Issue 11: Implement Random Life Events System
**Priority:** Medium  
**Labels:** feature, game-logic

**Description:**
Build a system for generating and applying random life events during gameplay.

**Tasks:**
- Create `lib/lifeEvents.ts` with event logic
- Implement probability-based event generation
- Support different severity levels
- Include various event types (car repair, medical, social, etc.)
- Make events toggleable
- Track event history

**Acceptance Criteria:**
- Events occur with appropriate probability
- Event costs are applied to monthly budget
- Events can be enabled/disabled
- Event log is maintained

---

### Issue 12: Implement Monthly Cash Flow Calculator
**Priority:** High  
**Labels:** feature, calculation

**Description:**
Create the main cash flow engine that ties income, expenses, and events together.

**Tasks:**
- Create `lib/cashFlow.ts` with monthly calculation
- Calculate starting balance
- Apply income (net pay)
- Subtract expenses
- Apply life event costs
- Update savings
- Update debt balances
- Calculate ending balance
- Track month-over-month changes

**Acceptance Criteria:**
- Cash flow is calculated correctly
- All components (income, expenses, events) are integrated
- Monthly summary data is available
- Historical data is tracked

---

## Phase 3: UI Components

### Issue 13: Create Job Selection Page
**Priority:** High  
**Labels:** ui, page

**Description:**
Build the initial page where users select their job and configure income settings. Jobs should have education requirements that users must meet.

**Tasks:**
- Create `pages/job.tsx` (or app router equivalent)
- Display job options from JSON data with education requirements
- Filter or indicate jobs based on education level (high school, college, etc.)
- Allow selection of salary vs hourly wage
- Configure hours per week for hourly jobs
- Select pay frequency
- Show calculated monthly gross income
- Add navigation to next step

**Acceptance Criteria:**
- Page displays all job options with education requirements
- Jobs are organized or filtered by education level
- Job selection updates state
- Calculated income is shown
- User can proceed to next step

---

### Issue 14: Create Paycheck Detail View
**Priority:** High  
**Labels:** ui, component

**Description:**
Build a component that shows detailed paycheck breakdown with all deductions.

**Tasks:**
- Create `components/PaycheckDetail.tsx`
- Display gross pay
- Show tax deductions (federal, state, FICA)
- Show benefit deductions (health, 401k)
- Display net pay prominently
- Make sections collapsible for clarity
- Add tooltips for explanation

**Acceptance Criteria:**
- All deductions are clearly displayed
- Calculations match backend logic
- UI is clear and understandable
- Collapsible sections work

---

### Issue 15: Create Lifestyle/Expenses Selection Page
**Priority:** High  
**Labels:** ui, page

**Description:**
Build the page where users choose their lifestyle and expenses.

**Tasks:**
- Create `pages/lifestyle.tsx`
- Add housing selection (city, rent tier, roommates)
- Add transportation selection (bus, car options)
- Add subscription toggles (streaming, gaming, etc.)
- Add food budget sliders (groceries, eating out)
- Display total monthly expenses
- Show remaining budget after expenses

**Acceptance Criteria:**
- All expense categories are configurable
- UI is intuitive and easy to use
- Total expenses update in real-time
- Budget preview is visible

---

### Issue 16: Create Monthly Summary Page
**Priority:** High  
**Labels:** ui, page

**Description:**
Build the page that shows the monthly budget summary and results.

**Tasks:**
- Create `pages/summary.tsx`
- Display income vs expenses comparison
- Show savings/deficit for the month
- Display updated savings balance
- Show debt balances
- Show credit score meter
- Add "stress meter" based on obligations
- Include "Run next month" button
- Display any life events that occurred

**Acceptance Criteria:**
- All financial data is clearly presented
- Visualizations are easy to understand
- User can progress to next month
- Historical data is accessible

---

### Issue 17: Create "What If" Comparison Tool
**Priority:** Medium  
**Labels:** ui, feature

**Description:**
Build an interactive tool for comparing different financial scenarios.

**Tasks:**
- Create `pages/whatif.tsx` or modal component
- Add sliders for adjusting rent
- Add sliders for adjusting income
- Add sliders for tax rate
- Add inflation rate slider
- Show side-by-side comparison
- Display impact on monthly budget
- Show long-term projections

**Acceptance Criteria:**
- Sliders adjust parameters smoothly
- Comparison updates in real-time
- Differences are highlighted
- User can save/reset scenarios

---

### Issue 18: Build Reusable UI Components Library
**Priority:** Medium  
**Labels:** ui, components

**Description:**
Create a library of reusable components used throughout the application.

**Tasks:**
- Create `components/Slider.tsx` for numeric inputs
- Create `components/Toggle.tsx` for binary choices
- Create `components/Card.tsx` for content containers
- Create `components/Button.tsx` for actions
- Create `components/Select.tsx` for dropdowns
- Create `components/ProgressBar.tsx` for meters
- Add consistent styling and theming

**Acceptance Criteria:**
- Components are reusable and well-documented
- Components have consistent styling
- Components are accessible (a11y)
- Components accept proper props/types

---

### Issue 19: Add Data Visualization Charts
**Priority:** Medium  
**Labels:** ui, visualization

**Description:**
Integrate charts for visualizing financial data over time.

**Tasks:**
- Choose and install chart library (e.g., Recharts, Chart.js)
- Create `components/CashFlowChart.tsx` for cash over time
- Create `components/SavingsChart.tsx` for savings progress
- Create `components/DebtChart.tsx` for debt tracking
- Create `components/ExpenseBreakdown.tsx` for pie/bar chart
- Support multiple time ranges (3, 6, 12 months)

**Acceptance Criteria:**
- Charts display data correctly
- Charts are interactive and responsive
- Multiple time ranges are supported
- Charts update with new data

---

## Phase 4: Data & Configuration

### Issue 20: Populate Comprehensive Price Book
**Priority:** Medium  
**Labels:** data, content

**Description:**
Expand JSON data files with comprehensive, realistic pricing data covering all US states with location-based pricing.

**Tasks:**
- Add 15-20 job options with realistic salaries and education requirements (high school, college, etc.)
- Include wide range of jobs: entry-level (minimum wage to $40k) to professional careers (engineer, nurse, teacher)
- Add rent tiers for multiple cities representing low, medium, and high cost-of-living areas
- Add location selection feature data (all US states)
- Add 20+ subscription service options
- Add detailed transportation costs by location
- Add grocery price ranges by region
- Add utility costs by region
- Research and validate all prices against real data
- Ensure diverse job examples for inclusive design

**Acceptance Criteria:**
- Job data includes education requirements for each position
- Data covers all US states for location-based pricing
- Prices vary realistically by location
- Data covers wide range of scenarios
- Prices are realistic and current
- Multiple options exist for each category
- Data is well-organized and documented
- Job options represent diverse careers and backgrounds

---

### Issue 21: Configure Accurate Tax Information
**Priority:** High  
**Labels:** data, taxes

**Description:**
Set up accurate tax brackets and rates for federal and state taxes covering all US states. Start with simplified calculations, with capability to add advanced mode later.

**Tasks:**
- Add current federal tax brackets for single filers
- Add current federal tax brackets for married filers
- Add tax rates for all US states (or indicate states with no income tax)
- Configure FICA rates (Social Security, Medicare)
- Add standard deduction amounts
- Document tax year for the data
- Implement simplified tax calculation as the default
- Design structure to support advanced mode addition in future

**Acceptance Criteria:**
- Tax data is accurate for current/recent tax year
- Both filing statuses are supported
- All US states are represented
- Simplified tax calculations work correctly
- Code structure allows for future advanced mode
- Documentation explains tax calculations and simplifications

---

### Issue 22: Define Benefit Plan Options
**Priority:** Medium  
**Labels:** data, benefits

**Description:**
Create realistic benefit plan options with costs and coverage.

**Tasks:**
- Define 3-5 health insurance plan options
- Set realistic premium costs
- Define deductible and out-of-pocket costs
- Configure 401k contribution limits
- Define employer match scenarios
- Add dental/vision options

**Acceptance Criteria:**
- Plans represent realistic options
- Costs are appropriate for plan types
- 401k rules follow IRS guidelines
- Documentation explains each plan

---

### Issue 23: Configure Random Life Events
**Priority:** Medium  
**Labels:** data, game-logic

**Description:**
Create a comprehensive list of random life events with probabilities and costs.

**Tasks:**
- Define 20-30 different life events
- Set realistic cost ranges for each event
- Assign appropriate probabilities (per month)
- Categorize events (medical, auto, social, home, personal)
- Include both positive and negative events
- Add event descriptions/messages

**Acceptance Criteria:**
- Wide variety of events exist
- Probabilities feel balanced
- Costs are realistic
- Events enhance gameplay without being overwhelming

---

## Phase 5: Features & Polish

### Issue 24: Implement Local Storage for Profile Saving
**Priority:** Medium  
**Labels:** feature, storage

**Description:**
Add functionality to save and load player profiles using browser local storage.

**Tasks:**
- Create `lib/storage.ts` with save/load functions
- Save complete player state to local storage
- Load saved profiles on app start
- Support multiple saved profiles
- Add profile management UI (save, load, delete)
- Handle storage errors gracefully

**Acceptance Criteria:**
- Profiles persist across browser sessions
- Multiple profiles can be managed
- Loading works correctly
- Errors don't crash the app

---

### Issue 25: Add Advanced Tax Calculation Mode
**Priority:** Low  
**Labels:** feature, enhancement

**Description:**
Implement a more detailed tax calculation mode with real tax brackets.

**Tasks:**
- Create toggle between simple and advanced modes
- Implement marginal tax bracket calculations
- Add itemized deduction options
- Include tax credits
- Show detailed tax breakdown
- Add educational tooltips explaining brackets

**Acceptance Criteria:**
- Advanced mode uses real tax brackets
- Calculations are accurate
- Mode toggle works smoothly
- Educational content is helpful

---

### Issue 26: Implement Stress Meter Calculation
**Priority:** Low  
**Labels:** feature, game-logic

**Description:**
Create a "stress meter" that reflects the player's financial burden.

**Tasks:**
- Create `lib/stressMeter.ts` with calculation logic
- Factor in debt-to-income ratio
- Factor in expense-to-income ratio
- Consider emergency fund adequacy
- Account for number of obligations
- Create visual component for stress level
- Add tips for reducing stress

**Acceptance Criteria:**
- Stress level reflects financial health
- Formula is balanced and meaningful
- Visual representation is clear
- Helpful tips are provided

---

### Issue 27: Implement Credit Score Tracking
**Priority:** Medium  
**Labels:** feature, game-logic

**Description:**
Add a simplified credit score system that responds to player actions.

**Tasks:**
- Create `lib/creditScore.ts` with scoring logic
- Start players at reasonable baseline score
- Increase score for on-time payments
- Decrease score for missed payments
- Factor in debt utilization
- Factor in payment history length
- Display score with visual indicator
- Show factors affecting score

**Acceptance Criteria:**
- Score changes based on player actions
- Changes are realistic and educational
- Score range is accurate (300-850)
- Factors are clearly explained

---

### Issue 28: Create Game Tutorial/Onboarding
**Priority:** Medium  
**Labels:** ui, ux

**Description:**
Build an onboarding experience for first-time players.

**Tasks:**
- Create welcome screen explaining the game
- Add step-by-step tutorial for first playthrough
- Highlight key UI elements
- Explain game mechanics
- Add tips for financial success
- Make tutorial skippable for returning users

**Acceptance Criteria:**
- New users understand how to play
- Tutorial is clear and concise
- Tutorial can be skipped
- Tutorial can be replayed from settings

---

### Issue 29: Add Settings and Configuration Page
**Priority:** Low  
**Labels:** ui, feature

**Description:**
Create a settings page for game configuration and preferences.

**Tasks:**
- Create `pages/settings.tsx`
- Add toggle for random events on/off
- Add difficulty settings (event frequency)
- Add toggle for simple vs advanced tax mode
- Add option to reset game
- Add theme selection (light/dark mode)
- Add sound/animation preferences

**Acceptance Criteria:**
- All settings are functional
- Settings persist in local storage
- Reset functionality works correctly
- UI is clear and organized

---

### Issue 30: Implement Comparison View for Scenarios
**Priority:** Low  
**Labels:** feature, ui

**Description:**
Create a view to compare different financial scenarios side-by-side.

**Tasks:**
- Build comparison interface
- Allow selection of 2-3 scenarios
- Compare same income with different lifestyles
- Show monthly, annual, and 5-year projections
- Highlight key differences
- Show trade-offs clearly

**Acceptance Criteria:**
- Up to 3 scenarios can be compared
- Differences are visually clear
- Projections are accurate
- Helps players make informed decisions

---

### Issue 31: Add Export/Share Functionality
**Priority:** Low  
**Labels:** feature, enhancement

**Description:**
Allow users to export or share their financial scenarios.

**Tasks:**
- Add export to PDF option
- Add export to CSV option
- Create shareable link generation
- Add screenshot functionality
- Include all relevant data in exports
- Respect user privacy in sharing

**Acceptance Criteria:**
- Multiple export formats work
- Exported data is complete and formatted
- Shareable links work correctly
- Privacy is maintained

---

### Issue 32: Create Responsive Mobile Layout
**Priority:** High  
**Labels:** ui, mobile, responsive

**Description:**
Ensure the application works well on mobile devices.

**Tasks:**
- Test all pages on mobile viewports
- Adjust layouts for small screens
- Make sliders touch-friendly
- Ensure text is readable
- Optimize navigation for mobile
- Test on iOS and Android browsers

**Acceptance Criteria:**
- App is fully functional on mobile
- UI is usable and attractive on small screens
- Touch interactions work smoothly
- Performance is acceptable on mobile

---

### Issue 33: Write Documentation and README
**Priority:** Medium  
**Labels:** documentation

**Description:**
Create comprehensive documentation for the project.

**Tasks:**
- Update README.md with project description
- Add setup instructions
- Document architecture and design decisions
- Create user guide
- Document data structures
- Add contributing guidelines
- Include license information

**Acceptance Criteria:**
- README is complete and clear
- New developers can set up the project
- Users understand how to play
- Code is well-documented

---

## Testing & Quality Assurance

### Issue 34: Set Up Testing Infrastructure
**Priority:** High  
**Labels:** testing, infrastructure

**Description:**
Configure testing tools and create initial test suite.

**Tasks:**
- Install and configure Jest
- Install and configure React Testing Library
- Set up test script in package.json
- Create test utilities and helpers
- Set up code coverage reporting
- Create CI/CD pipeline for tests

**Acceptance Criteria:**
- Tests can be run with `npm test`
- Coverage reports are generated
- CI runs tests on PR

---

### Issue 35: Write Unit Tests for Calculation Logic
**Priority:** High  
**Labels:** testing

**Description:**
Create comprehensive unit tests for all calculation functions.

**Tasks:**
- Test income calculations
- Test tax calculations
- Test benefit deductions
- Test expense tracking
- Test cash flow calculations
- Test edge cases and error conditions
- Achieve >80% code coverage for lib/ directory

**Acceptance Criteria:**
- All calculation functions have tests
- Tests cover happy path and edge cases
- Code coverage meets target
- All tests pass

---

### Issue 36: Write Component Tests
**Priority:** Medium  
**Labels:** testing, ui

**Description:**
Create tests for React components.

**Tasks:**
- Test component rendering
- Test user interactions
- Test prop handling
- Test state management
- Test accessibility
- Achieve >70% code coverage for components

**Acceptance Criteria:**
- Critical components have tests
- User flows are tested
- Tests are maintainable
- All tests pass

---

### Issue 37: Conduct Accessibility Audit
**Priority:** Medium  
**Labels:** accessibility, a11y

**Description:**
Ensure the application is accessible to all users.

**Tasks:**
- Run automated accessibility tests (axe, lighthouse)
- Test keyboard navigation
- Test screen reader compatibility
- Ensure proper ARIA labels
- Check color contrast ratios
- Test with various assistive technologies

**Acceptance Criteria:**
- No critical accessibility issues
- Keyboard navigation works throughout
- Screen readers can navigate the app
- Color contrast meets WCAG standards

---

### Issue 38: Performance Optimization
**Priority:** Low  
**Labels:** performance, optimization

**Description:**
Optimize application performance for smooth user experience.

**Tasks:**
- Analyze bundle size
- Implement code splitting
- Optimize re-renders
- Lazy load components
- Optimize images and assets
- Run Lighthouse audits
- Aim for 90+ performance score

**Acceptance Criteria:**
- App loads quickly
- Interactions are smooth
- Bundle size is reasonable
- Lighthouse scores are good

---

## Deployment

### Issue 39: Set Up Deployment Pipeline
**Priority:** Medium  
**Labels:** deployment, infrastructure

**Description:**
Configure deployment to Azure hosting platform for both frontend and backend.

**Tasks:**
- Configure Azure App Service for .NET Core 10 backend
- Configure Azure Static Web Apps or Azure App Service for Next.js frontend
- Set up automatic deployment from main branch (CI/CD pipeline)
- Configure environment variables for both frontend and backend
- Set up custom domain when available
- Configure SSL certificates
- Set up privacy-focused analytics (no personal data collection)
- Test deployment process for both services
- Document deployment process

**Acceptance Criteria:**
- Backend API deploys successfully to Azure
- Frontend app deploys successfully to Azure
- Automatic deployment works for both services
- Production builds are optimized
- Both services are accessible via URLs
- API communication between frontend and backend works in production
- Analytics configured with privacy protections

---

### Issue 40: Create Demo Mode
**Priority:** Low  
**Labels:** feature, demo

**Description:**
Create a demo mode with pre-populated scenarios for showcasing.

**Tasks:**
- Create 3-5 example scenarios
- Add "Demo Mode" button on home page
- Pre-fill data for quick exploration
- Include guided tour of features
- Make it easy to reset and try different demos

**Acceptance Criteria:**
- Demo mode loads quickly
- Scenarios are realistic and interesting
- Users can explore without setup
- Easy to exit demo mode

---

## Summary

This represents **40 work items** organized into phases:
- **Phase 1:** 6 issues (Project Setup - Frontend TypeScript + Backend .NET)
- **Phase 2:** 6 issues (Core Logic - Backend calculations)
- **Phase 3:** 7 issues (UI - Frontend TypeScript components)
- **Phase 4:** 4 issues (Data configuration)
- **Phase 5:** 8 issues (Features & Polish)
- **Testing:** 5 issues (Frontend + Backend tests)
- **Deployment:** 4 issues (Frontend + Backend deployment)

**Architecture:**
- **Frontend:** Next.js 14+ with TypeScript (required)
- **Backend:** .NET Core 10 with Minimal API (required)
- **Communication:** RESTful API

**Recommended Implementation Order:**
1. Start with Phase 1 (setup both frontend and backend)
2. Build Phase 2 (backend calculation API with tests)
3. Create Phase 3 (frontend UI consuming backend API)
4. Populate Phase 4 (data)
5. Add Phase 5 (enhancements)
6. Complete testing and deployment

**Estimated Timeline:**
- **MVP (Issues 1-6, 7-12, 13-16, 20-21):** 4-6 weeks
- **Full Featured (All 40 issues):** 8-12 weeks

**Priority Levels:**
- **High:** Core functionality needed for MVP (frontend + backend)
- **Medium:** Important features for complete experience
- **Low:** Nice-to-have enhancements

---

## Notes for Implementation

1. **Start with data models** - Having clear types will guide all development
2. **Test calculations thoroughly** - Financial accuracy is critical
3. **Keep UI simple initially** - Focus on functionality before polish
4. **Use real data** - Realistic numbers make the simulation educational
5. **Make it fun** - Balance realism with engaging gameplay
6. **Think mobile** - Many users will access on phones
7. **Document as you go** - Good docs help future contributors
8. **Iterate based on feedback** - Test with actual kids/users early

