# Adulting Simulator - Implementation Roadmap

This document provides a quick reference and recommended implementation path for the Adulting Simulator project.

## Quick Start Guide

### Prerequisites
Before starting implementation, you'll need:
- Node.js (v18 or later)
- npm or yarn
- Basic understanding of React/Next.js
- TypeScript knowledge (recommended)

### First Steps
1. Review the [Design document](/Design) to understand the vision
2. Review [WORK_ITEMS.md](/WORK_ITEMS.md) for all implementation tasks
3. Set up the project (Issues #1-3)
4. Start building core logic (Issues #4-9)

## Project Architecture

```
adulting-simulator/
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
│   ├── lib/                 # Core business logic
│   │   ├── income.ts       # Income calculations
│   │   ├── taxes.ts        # Tax calculations
│   │   ├── benefits.ts     # Benefits logic
│   │   ├── expenses.ts     # Expense tracking
│   │   ├── lifeEvents.ts   # Random events
│   │   ├── cashFlow.ts     # Monthly cash flow
│   │   ├── creditScore.ts  # Credit score logic
│   │   └── storage.ts      # Local storage
│   ├── types/               # TypeScript definitions
│   │   ├── job.ts
│   │   ├── expense.ts
│   │   ├── player.ts
│   │   └── ...
│   └── data/                # JSON configuration
│       ├── jobs.json
│       ├── housing.json
│       ├── subscriptions.json
│       ├── taxes.json
│       ├── benefits.json
│       └── lifeEvents.json
├── public/                  # Static assets
├── tests/                   # Test files
└── docs/                    # Additional documentation
```

## Implementation Phases

### Phase 0: Planning & Questions (START HERE)
**Before implementing, clarify these questions:**

1. **Target Audience:**
   - What age range are the kids? (This affects complexity and UI design)
   - Is this for home use or classroom use?

2. **Geographic Scope:**
   - Should we focus on a specific state or keep it generic US?
   - Do we need to support different regions/countries?

3. **Tax Complexity:**
   - Start with simple percentage-based taxes or real brackets?
   - How detailed should state taxes be?

4. **Feature Priority:**
   - Which features are must-haves vs nice-to-haves?
   - Is there a target launch date?

5. **Technical Preferences:**
   - Any preferred hosting platform?
   - Any design system or UI framework preferences?
   - Any analytics or tracking requirements?

### Phase 1: Foundation (Week 1-2)
**Goal:** Get a working Next.js project with core types and data structures.

**Critical Path:**
1. Issue #1: Initialize Next.js Project → 1 day
2. Issue #2: Define Core Data Models → 2 days
3. Issue #3: Create JSON Configuration Files → 2 days
4. Issue #31: Set Up Testing Infrastructure → 1 day

**Deliverable:** Empty Next.js app with types and sample data.

### Phase 2: Core Calculations (Week 3-4)
**Goal:** Build and test all calculation logic.

**Critical Path:**
1. Issue #4: Income Calculation Engine → 2 days
2. Issue #5: Tax Calculation System → 3 days
3. Issue #6: Benefits Deduction System → 2 days
4. Issue #7: Expense Tracking System → 2 days
5. Issue #9: Monthly Cash Flow Calculator → 2 days
6. Issue #32: Write Unit Tests → 3 days

**Deliverable:** Fully tested calculation engine.

### Phase 3: Minimum Viable UI (Week 5-7)
**Goal:** Create basic user interface for core gameplay loop.

**Critical Path:**
1. Issue #15: Build Reusable UI Components → 3 days
2. Issue #10: Job Selection Page → 2 days
3. Issue #11: Paycheck Detail View → 2 days
4. Issue #12: Lifestyle/Expenses Selection → 3 days
5. Issue #13: Monthly Summary Page → 3 days
6. Issue #29: Responsive Mobile Layout → 2 days

**Deliverable:** Playable MVP from start to summary.

### Phase 4: Data & Events (Week 8)
**Goal:** Populate with realistic data and add random events.

**Critical Path:**
1. Issue #17: Populate Comprehensive Price Book → 2 days
2. Issue #18: Configure Accurate Tax Information → 1 day
3. Issue #19: Define Benefit Plan Options → 1 day
4. Issue #8: Random Life Events System → 2 days
5. Issue #20: Configure Random Life Events → 1 day

**Deliverable:** Rich, realistic simulation experience.

### Phase 5: Enhanced Features (Week 9-10)
**Goal:** Add features that enhance educational value.

**Critical Path:**
1. Issue #21: Local Storage for Profiles → 2 days
2. Issue #16: Data Visualization Charts → 3 days
3. Issue #24: Credit Score Tracking → 2 days
4. Issue #14: "What If" Comparison Tool → 3 days
5. Issue #25: Game Tutorial/Onboarding → 2 days

**Deliverable:** Feature-complete application.

### Phase 6: Testing & Polish (Week 11-12)
**Goal:** Ensure quality and accessibility.

**Critical Path:**
1. Issue #33: Component Tests → 3 days
2. Issue #34: Accessibility Audit → 2 days
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
- [ ] Environment variables configured
- [ ] Build process succeeds
- [ ] Production build tested locally
- [ ] Deployment platform configured
- [ ] Custom domain configured (if applicable)
- [ ] SSL certificate valid
- [ ] Analytics configured (if needed)

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
