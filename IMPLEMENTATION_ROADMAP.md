# Adulting Simulator - Implementation Roadmap

This document provides a quick reference and recommended implementation path for the Adulting Simulator project.

## Tech Stack Overview

**Frontend:** Next.js 14+ with **TypeScript** (App Router)  
**Backend:** **.NET Core 10** with **Minimal API**  
**Architecture:** Separated frontend and backend with RESTful API communication

## Quick Start Guide

### Prerequisites
Before starting implementation, you'll need:
- **Frontend:**
  - Node.js (v18 or later)
  - npm or yarn
  - TypeScript knowledge (required)
  - Basic understanding of React/Next.js
- **Backend:**
  - .NET Core 10 SDK
  - C# knowledge
  - Understanding of Minimal API pattern

### First Steps
1. Review the [Design document](/Design) to understand the vision
2. Review [WORK_ITEMS.md](/WORK_ITEMS.md) for all implementation tasks
3. Set up both frontend and backend projects (Issues #1-2)
4. Define data models for both TypeScript and C# (Issues #3-4)
5. Set up API communication layer (Issue #6)

## Project Architecture

### Frontend (TypeScript/Next.js)
```
frontend/
├── src/
│   ├── app/                 # Next.js app directory (pages)
│   │   ├── page.tsx        # Home/start page
│   │   ├── job/            # Job selection
│   │   ├── lifestyle/      # Lifestyle choices
│   │   ├── summary/        # Monthly summary
│   │   └── whatif/         # Comparison tool
│   ├── components/          # React components
│   │   ├── ui/             # Reusable UI components
│   │   ├── PaycheckDetail.tsx
│   │   ├── CashFlowChart.tsx
│   │   └── ...
│   ├── lib/                 # API client and utilities
│   │   ├── api-client.ts   # Backend API calls
│   │   └── storage.ts      # Local storage
│   ├── types/               # TypeScript definitions
│   │   ├── job.ts
│   │   ├── expense.ts
│   │   ├── player.ts
│   │   ├── api.ts          # API request/response types
│   │   └── ...
│   └── data/                # Static JSON (optional)
├── public/                  # Static assets
└── tests/                   # Frontend tests
```

### Backend (.NET Core 10 Minimal API)
```
backend/
├── Program.cs               # Minimal API endpoints
├── Services/
│   ├── CalculationService.cs
│   ├── TaxService.cs
│   └── DataService.cs
├── Models/
│   ├── Job.cs
│   ├── TaxConfiguration.cs
│   ├── Expense.cs
│   └── PlayerState.cs
├── DTOs/
│   ├── IncomeRequest.cs
│   ├── TaxCalculationRequest.cs
│   └── CashFlowResponse.cs
├── Data/                    # JSON configuration files
│   ├── jobs.json
│   ├── housing.json
│   ├── taxes.json
│   └── ...
└── Tests/                   # Backend tests
```

## Implementation Phases

### Phase 0: Planning & Questions ✅ **COMPLETED**
**Key decisions have been made through QUESTIONS.md:**

1. **Target Audience:** ✅ **Decided**
   - Age range: High school and college/young adults (15-25 years)
   - Use case: Home use by individual families AND classroom setting (teacher-led)

2. **Geographic Scope:** ✅ **Decided**
   - Coverage: All US states
   - Users can choose their location for accurate pricing and taxes

3. **Tax Complexity:** ✅ **Decided**
   - Start simple, add advanced mode later (recommended approach confirmed)
   - Begin with simplified calculations, then add detailed state-specific taxes

4. **Feature Priority:** ✅ **Decided**
   - **Critical for MVP:** Job selection, tax calculation, expense selection, monthly budget summary
   - **Important:** Savings tracking, 401k/retirement planning, health insurance
   - **Nice-to-have:** Random life events, debt tracking, credit score, multi-month progression

5. **Technical Preferences:** ✅ **Decided**
   - Hosting: Azure (both frontend and backend)
   - Design system: Tailwind CSS
   - Analytics: Privacy-focused only (no personal data)
   - Domain: Will be determined later

6. **Additional Requirements:** ✅ **Confirmed**
   - Must work offline (offline-first)
   - Must be very fast (<1 second load time)
   - Must be printable
   - Jobs have education requirements
   - Wide range of jobs from entry-level to professional careers
   - Standard web accessibility
   - Inclusive design (diverse jobs, various family structures, different starting points)

### Phase 1: Foundation (Week 1-2)
**Goal:** Get working Next.js and .NET Core projects with data models.

**Critical Path:**
1. Issue #1: Initialize Next.js Frontend with TypeScript → 1 day
2. Issue #2: Initialize .NET Core 10 Backend with Minimal API → 1 day
3. Issue #3: Define TypeScript Types for Frontend → 1 day
4. Issue #4: Define C# Models for Backend → 1 day
5. Issue #5: Create JSON Configuration Files → 1 day
6. Issue #6: Implement Backend Calculation API → 2 days

**Deliverable:** Both frontend and backend running with API communication.

### Phase 2: Core Calculations (Week 3-4)
**Goal:** Build and test all calculation logic in backend.

**Critical Path:**
1. Issue #7: Income Calculation Engine (Backend) → 2 days
2. Issue #8: Tax Calculation System (Backend) → 3 days
3. Issue #9: Benefits Deduction System (Backend) → 2 days
4. Issue #10: Expense Tracking System (Backend) → 2 days
5. Issue #12: Monthly Cash Flow Calculator (Backend) → 2 days
6. Backend unit tests → 3 days

**Deliverable:** Fully tested backend calculation API.

### Phase 3: Minimum Viable UI (Week 5-7)
**Goal:** Create frontend UI consuming backend API.

**Critical Path:**
1. Issue #18: Build Reusable UI Components → 3 days
2. Issue #13: Job Selection Page (TypeScript) → 2 days
3. Issue #14: Paycheck Detail View (TypeScript) → 2 days
4. Issue #15: Lifestyle/Expenses Selection (TypeScript) → 3 days
5. Issue #16: Monthly Summary Page (TypeScript) → 3 days
6. Mobile responsive layout → 2 days

**Deliverable:** Playable MVP from start to summary with API integration.

### Phase 4: Data & Events (Week 8)
**Goal:** Populate with realistic data and add random events.

**Critical Path:**
1. Issue #20: Populate Comprehensive Price Book → 2 days
2. Issue #21: Configure Accurate Tax Information → 1 day
3. Issue #22: Define Benefit Plan Options → 1 day
4. Issue #11: Random Life Events System → 2 days
5. Issue #23: Configure Random Life Events → 1 day

**Deliverable:** Rich, realistic simulation experience.

### Phase 5: Enhanced Features (Week 9-10)
**Goal:** Add features that enhance educational value.

**Critical Path:**
1. Local Storage for Profiles (Frontend) → 2 days
2. Issue #19: Data Visualization Charts (TypeScript) → 3 days
3. Credit Score Tracking (Backend + Frontend) → 2 days
4. Issue #17: "What If" Comparison Tool (TypeScript) → 3 days
5. Game Tutorial/Onboarding (Frontend) → 2 days

**Deliverable:** Feature-complete application.

### Phase 6: Testing & Polish (Week 11-12)
**Goal:** Ensure quality and accessibility.

**Critical Path:**
1. Frontend Component Tests (TypeScript/Jest) → 3 days
2. Backend Integration Tests (.NET/xUnit) → 3 days
3. Accessibility Audit → 2 days
3. Issue #35: Performance Optimization → 2 days
4. Issue #30: Documentation and README → 2 days
5. Issue #36: Deployment Pipeline → 1 day

**Deliverable:** Production-ready application.

## Development Workflow

### For Each Feature:
1. **Design:** Review requirements and design approach
2. **Types:** Update TypeScript types if needed
3. **Logic:** Implement core logic in `lib/`
4. **Tests:** Write unit tests and verify
5. **UI:** Create React components
6. **Integration:** Connect UI to logic
7. **Manual Test:** Verify in browser
8. **Review:** Code review and refactor
9. **Document:** Update relevant docs

### Testing Strategy:
- **Unit tests:** All functions in `lib/` directory
- **Component tests:** Critical user-facing components
- **Integration tests:** Key user flows (optional for MVP)
- **Manual testing:** Every feature before PR merge
- **Accessibility testing:** Before each release

### Code Quality:
- Use TypeScript for type safety
- Follow ESLint rules
- Use Prettier for formatting
- Write self-documenting code
- Add comments for complex logic
- Keep functions small and focused

## Data Specifications

### Sample Data Ranges (Use for JSON files)

**Jobs:**
- Entry level: $25,000 - $35,000/year
- Mid-level: $40,000 - $70,000/year
- Professional: $75,000 - $120,000/year
- Hourly: $12 - $30/hour

**Housing (Monthly Rent):**
- Small city / Roommates: $400 - $800
- Medium city: $900 - $1,500
- Large city: $1,600 - $2,500
- Large city prime: $2,600+

**Transportation:**
- Bus pass: $70 - $100/month
- Used car: $250 loan + $100 insurance + $150 gas
- New car: $450 loan + $150 insurance + $180 gas

**Food:**
- Groceries: $200 - $400/month
- Eating out: $0 - $300/month

**Utilities:**
- Electric: $60 - $120/month
- Internet: $50 - $80/month
- Phone: $40 - $100/month
- Water/Gas: $40 - $80/month

**Subscriptions (each):**
- Streaming: $8 - $18/month
- Gaming: $10 - $15/month
- Music: $10 - $15/month

**Life Events (one-time costs):**
- Minor: $50 - $200 (flat tire, doctor visit)
- Medium: $300 - $800 (car repair, ER visit)
- Major: $1,000 - $3,000 (major repair, emergency)

### Tax Rates (2024 Reference)

**Federal (Single, Simple Mode):**
- Up to $30k: 10%
- $30k - $70k: 12%
- $70k+: 22%

**State (Examples):**
- No income tax: 0% (TX, FL, WA, etc.)
- Low: 3-5% (PA, IL, etc.)
- Medium: 6-8% (CA, NY, etc.)
- High: 9-10% (CA high earners)

**FICA:**
- Social Security: 6.2% (up to $168,600)
- Medicare: 1.45%

## UI/UX Guidelines

### Design Principles:
1. **Simplicity:** Clean, uncluttered interface
2. **Clarity:** Make numbers and concepts easy to understand
3. **Feedback:** Show immediate impact of choices
4. **Education:** Explain financial concepts without lecturing
5. **Fun:** Use colors, animations, and positive reinforcement

### Visual Style:
- **Color scheme:** Bright, friendly colors (not too childish)
- **Typography:** Clear, readable fonts (16px+ body text)
- **Layout:** Card-based design with clear sections
- **Feedback:** Green for positive, red for negative, yellow for warnings
- **Responsive:** Mobile-first design

### Key Interactions:
- **Sliders:** For adjustable values (groceries, 401k %)
- **Toggle buttons:** For subscriptions (on/off)
- **Cards:** For selection (jobs, housing, cars)
- **Progress bars:** For debt, savings, credit score
- **Charts:** For historical data and comparisons

### Educational Elements:
- **Tooltips:** Explain financial terms (FICA, 401k, etc.)
- **Examples:** Show real-world scenarios
- **Tips:** Offer money management advice
- **Comparisons:** Show trade-offs between choices
- **Goals:** Help users set and track financial goals

## Common Calculations

### Monthly Gross Income:
```typescript
// Salary
const monthlyGross = annualSalary / 12;

// Hourly
const monthlyGross = (hourlyRate * hoursPerWeek * 52) / 12;
```

### Net Pay:
```typescript
const grossPay = calculateGrossPay(job);
const federalTax = grossPay * federalRate;
const stateTax = grossPay * stateRate;
const fica = grossPay * 0.0765;
const healthPremium = selectedPlan.premium;
const retirement401k = grossPay * (contribution401k / 100);

const netPay = grossPay - federalTax - stateTax - fica - healthPremium - retirement401k;
```

### Cash Flow:
```typescript
const startingBalance = previousBalance;
const income = netPay;
const fixedExpenses = rent + insurance + internet + phone;
const variableExpenses = groceries + utilities + eating out + transportation;
const subscriptions = streamingServices + gaming + music;
const debtPayments = studentLoan + creditCard + carLoan;
const lifeEvents = randomEventCost;

const totalExpenses = fixedExpenses + variableExpenses + subscriptions + debtPayments + lifeEvents;
const endingBalance = startingBalance + income - totalExpenses;
const monthlyChange = endingBalance - startingBalance;
```

### Credit Score (Simplified):
```typescript
const baseScore = 650;
const onTimePayments = paymentHistory.filter(p => p.onTime).length;
const latePayments = paymentHistory.filter(p => !p.onTime).length;

const paymentFactor = (onTimePayments * 2) - (latePayments * 50);
const utilizationFactor = (creditUsed / creditLimit) > 0.3 ? -30 : 0;
const historyFactor = monthsActive * 1;

const creditScore = Math.min(850, Math.max(300, 
  baseScore + paymentFactor + utilizationFactor + historyFactor
));
```

## Testing Examples

### Unit Test Example (Income):
```typescript
import { calculateMonthlyGross } from '@/lib/income';

describe('Income Calculations', () => {
  test('calculates salary correctly', () => {
    const job = { type: 'salary', annualSalary: 60000 };
    expect(calculateMonthlyGross(job)).toBe(5000);
  });

  test('calculates hourly correctly', () => {
    const job = { type: 'hourly', hourlyRate: 20, hoursPerWeek: 40 };
    expect(calculateMonthlyGross(job)).toBeCloseTo(3466.67, 2);
  });
});
```

### Component Test Example:
```typescript
import { render, screen } from '@testing-library/react';
import PaycheckDetail from '@/components/PaycheckDetail';

test('displays gross and net pay', () => {
  const paycheck = {
    grossPay: 5000,
    netPay: 3500,
    deductions: { federal: 800, state: 300, fica: 400 }
  };
  
  render(<PaycheckDetail paycheck={paycheck} />);
  
  expect(screen.getByText(/gross.*5,000/i)).toBeInTheDocument();
  expect(screen.getByText(/net.*3,500/i)).toBeInTheDocument();
});
```

## Deployment Checklist

### Pre-Deployment:
- [ ] All tests passing
- [ ] No console errors or warnings
- [ ] Accessibility audit complete
- [ ] Performance benchmarks met
- [ ] Mobile testing complete
- [ ] Cross-browser testing done
- [ ] Documentation updated
- [ ] README has deployment instructions

### Deployment:
- [ ] Environment variables configured (Frontend and Backend)
- [ ] Backend build process succeeds (.NET Core 10)
- [ ] Frontend build process succeeds (Next.js)
- [ ] Production builds tested locally
- [ ] Azure deployment configured (both frontend and backend)
- [ ] Azure App Service configured for backend
- [ ] Azure Static Web Apps or App Service configured for frontend
- [ ] Custom domain configured (when available)
- [ ] SSL certificate valid
- [ ] Privacy-focused analytics configured (no personal data collection)

### Post-Deployment:
- [ ] Smoke test all major features
- [ ] Verify data loads correctly
- [ ] Test on various devices
- [ ] Monitor error logs
- [ ] Gather initial user feedback

## Resources & References

### Financial Education:
- [Consumer Financial Protection Bureau](https://www.consumerfinance.gov/)
- [IRS Tax Brackets](https://www.irs.gov/filing/federal-income-tax-rates-and-brackets)
- [Social Security FICA rates](https://www.ssa.gov/oact/cola/cbb.html)

### Technical Documentation:
- [Next.js Documentation](https://nextjs.org/docs)
- [React Documentation](https://react.dev/)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [.NET Core Documentation](https://learn.microsoft.com/en-us/dotnet/core/)
- [ASP.NET Core Minimal APIs](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis)
- [Azure App Service Documentation](https://learn.microsoft.com/en-us/azure/app-service/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)

### Design Inspiration:
- [Money Simulator Games](https://www.google.com/search?q=budget+simulator+games)
- [Financial Literacy Tools](https://www.google.com/search?q=financial+literacy+interactive+tools)

### Testing Resources:
- [Jest Documentation](https://jestjs.io/)
- [React Testing Library](https://testing-library.com/react)
- [Web Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

## Questions or Issues?

If you encounter problems or have questions during implementation:

1. **Review the Design document** - The original vision might have the answer
2. **Check WORK_ITEMS.md** - Detailed specifications for each task
3. **Search existing issues** - Someone might have asked already
4. **Create a new issue** - Tag with appropriate labels
5. **Ask for clarification** - Better to ask than assume

## Success Metrics

### MVP Success:
- [ ] User can select a job and see net pay
- [ ] User can choose lifestyle expenses
- [ ] User can see monthly budget summary
- [ ] Calculations are accurate
- [ ] App works on mobile and desktop

### Full Success:
- [ ] All 37 issues implemented
- [ ] Test coverage >80% for logic, >70% for components
- [ ] Lighthouse score >90
- [ ] No critical accessibility issues
- [ ] Positive user feedback from target audience
- [ ] Users report learning about budgeting

### Educational Success:
- [ ] Users understand tax deductions
- [ ] Users see impact of lifestyle choices
- [ ] Users learn about benefits like 401k
- [ ] Users appreciate emergency fund importance
- [ ] Users understand credit score factors

---

## Next Steps

1. **Answer the questions in Phase 0** (Target audience, tax complexity, etc.)
2. **Create a new GitHub repository or branch** (if not already done)
3. **Start with Issue #1** - Initialize Next.js Project
4. **Follow the critical path** outlined in each phase
5. **Test frequently** - Don't wait until the end
6. **Have fun!** This is an educational tool, so make it engaging

Good luck with the implementation! 🚀
