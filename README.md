# Adulting Simulator

An interactive web-based financial literacy game that teaches budgeting, taxes, and money management through realistic simulation.

## 📋 Project Overview

The Adulting Simulator helps young people (ages 15-25) learn about personal finance by simulating real-world financial decisions. Users choose a job, manage expenses, make lifestyle choices, and experience the consequences of their financial decisions in a safe, educational environment.

**Target Audience:** High school and college/young adults (ages 15-25)  
**Use Cases:** Home use by individual families and classroom settings (teacher-led)

### Key Features (Planned)

**Critical (MVP):**
- **Job Selection**: Choose from various careers with different salaries and pay structures
  - Jobs have education requirements (high school, college, etc.)
- **Tax Calculations**: Learn about gross vs. net pay, tax withholding, and deductions
  - Start with simplified tax calculations, advanced mode added later
- **Lifestyle Choices**: Select housing, transportation, food, and entertainment options
  - Prices vary by user-selected location
- **Monthly Budgeting**: Track income vs. expenses and see your cash flow

**Important:**
- **Savings Tracking**: Monitor savings over time
- **401k and Retirement Planning**: Learn about long-term financial planning
- **Health Insurance Selection**: Understand healthcare costs and options

**Nice-to-Have:**
- **Random Life Events**: Experience unexpected expenses like car repairs or medical bills
- **Debt Tracking**: Manage student loans and credit cards
- **Credit Score Simulation**: See how decisions affect creditworthiness
- **Multi-Month Progression**: Track financial health over multiple months
- **"What If" Scenarios**: Compare different financial decisions side-by-side
- **Charts and Visualizations**: Visual representations of financial data
- **Save/Load Profiles**: Preserve progress and experiment with different scenarios
- **Tutorial/Onboarding**: Guided introduction to features

## 📚 Documentation

- **[Design Document](Design)** - Original vision and requirements
- **[Work Items](WORK_ITEMS.md)** - Detailed list of 37 implementation tasks
- **[Implementation Roadmap](IMPLEMENTATION_ROADMAP.md)** - Phase-by-phase development guide
- **[Questions](QUESTIONS.md)** - Pre-implementation questions to clarify requirements

## 🚀 Project Status

**Current Phase:** Planning & Requirements Gathering

The project is currently in the planning phase. The design has been analyzed and broken down into 37 actionable work items organized into 6 phases:

1. **Phase 1: Project Setup** (3 issues)
2. **Phase 2: Core Game Logic** (6 issues)
3. **Phase 3: UI Components** (7 issues)
4. **Phase 4: Data & Configuration** (4 issues)
5. **Phase 5: Features & Polish** (8 issues)
6. **Testing & Deployment** (9 issues)

## 🎯 Next Steps

Before starting implementation:

1. **Review** the [QUESTIONS.md](QUESTIONS.md) file - ✅ **Completed**
2. **Answer** the questions to clarify requirements - ✅ **Completed**
3. **Prioritize** features based on your needs - ✅ **Completed**
4. **Start** with Phase 1 work items

### Key Requirements & Constraints
- **Must work offline** (offline-first approach)
- **Must be very fast** (<1 second load time)
- **Must be printable** for classroom use
- **Standard web accessibility** is sufficient
- **Inclusive design:** Diverse job examples, various family structures, different starting points

## 🛠️ Planned Tech Stack

### Frontend
- **Framework:** Next.js 14+ (React with App Router)
- **Language:** TypeScript (required for type safety)
- **Styling:** Tailwind CSS
- **Charts:** Recharts or similar
- **Testing:** Jest + React Testing Library
- **Analytics:** Privacy-focused only (no personal data collection)

### Backend
- **Framework:** .NET Core 10
- **API Style:** Minimal API
- **Language:** C#
- **Testing:** xUnit or NUnit

### Deployment
- **Frontend & Backend:** Azure
- **Domain:** To be determined later

### Geographic Scope
- **Coverage:** All US states
- **Location Selection:** Users can choose their location for accurate cost-of-living and tax calculations

## 📖 Educational Goals

This simulator aims to teach:
- **Financial responsibility** (Primary Goal #1)
- **Understanding taxes** and the difference between gross and net pay (Primary Goal #2)
- **Impact of lifestyle choices on budget** (Primary Goal #3)
- How tax withholding works
- Importance of emergency savings
- Credit score factors
- Trade-offs in financial decisions
- Long-term financial planning

### Teaching Approach
The app uses a combination of:
- Explicit lessons/tutorials upfront
- Learning by doing (discover through gameplay)
- Tooltips and hints throughout

## 🤝 Contributing

This project is in early development. 

### Future Vision
- Ongoing updates with new features
- Open source for others to use/modify
- Community contributions welcome

### Project Approach
- **MVP First:** Focus on core features, then iterate
- **Quality Over Speed:** No rush, prioritizing quality implementation
- **Full Implementation:** Complete development without requiring external content creation

Once implementation begins, contribution guidelines will be added.

## 📄 License

See [LICENSE](LICENSE) file for details.

## 💡 Questions or Ideas?

Please review the [QUESTIONS.md](QUESTIONS.md) file and provide your input to help shape the project direction.