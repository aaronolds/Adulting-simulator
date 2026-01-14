# Questions Before Implementation

Before starting the implementation of the Adulting Simulator, please answer these questions to ensure the project meets your needs and vision.

---

## 1. Target Audience

### Primary Users
**Question:** What is the age range of the primary users (your kids)?
- [ ] Elementary (ages 8-11)
- [ ] Middle school (ages 12-14)
- [x] High school (ages 15-18)
- [x] College/Young adults (ages 18-25)
- [ ] Mixed ages
- [ ] Other: _______________

**Why this matters:** The age range affects UI complexity, vocabulary level, and which features to prioritize. Younger kids need simpler concepts and more guidance, while older teens can handle more complexity.

### Use Case
**Question:** How will this tool be used?
- [x] Home use by individual families
- [x] Classroom setting (teacher-led)
- [ ] After-school program
- [ ] Self-guided learning by teens
- [ ] Financial literacy workshops
- [ ] Other: _______________

**Why this matters:** This affects whether we need multi-user support, teacher dashboards, or sharing features.

---

## 2. Geographic & Regulatory Scope

### Location
**Question:** Which state/region should we optimize for?
- [ ] Generic US (no specific state)
- [ ] Specific state: _______________
- [x] Multiple specific states: all states
- [ ] International (which country/countries?): _______________

**Why this matters:** State income tax rates vary significantly (0% to 13%+), and cost of living differs by region. This affects the default data we include.

### Tax Complexity
**Question:** What level of tax detail do you want in the initial version?
- [ ] **Simple:** Fixed percentages by income bracket (easier to understand, less accurate)
- [ ] **Moderate:** Real tax brackets but simplified state taxes
- [ ] **Detailed:** Full federal brackets and state-specific taxes
- [x] **Start simple, add advanced mode later** (recommended)

**Why this matters:** More accurate taxes are more educational but also more complex to implement and understand.

---

## 3. Feature Priority

### Must-Have Features (for MVP)
**Question:** Which features are essential for the first usable version?

Please mark each as **Critical**, **Important**, or **Nice-to-have**:

- [x] Job selection and income calculation - critical
- [x] Tax calculation and deductions - critical
- [x] Expense selection (housing, food, etc.) - critical.
- [x] Monthly budget summary - important
- [x] Random life events (car repair, etc.) - nice to have.
- [x] Savings tracking - important
- [x] Debt tracking (student loans, credit cards) - nice to have
- [ ] Credit score simulation - nice to have
- [ ] 401k and retirement planning - important 
- [ ] Health insurance selection - important
- [ ] Multi-month progression - nice to have
- [ ] "What if" comparison tool - nice to have
- [ ] Charts and visualizations - nice to have
- [ ] Save/load profiles - nice to have
- [ ] Tutorial/onboarding - nice to have

### Additional Features
**Question:** Are there any features NOT in the design document that you'd like to add?

1. _______________
2. _______________
3. _______________

---

## 4. Technical Preferences

### Hosting
**Question:** Where would you like to host this application?
- [ ] Vercel (recommended for Next.js, free tier available)
- [ ] Netlify (free tier available)
- [ ] GitHub Pages
- [ ] Your own server
- [ ] No preference / you decide
- [x] Other: azure 

**Why this matters:** Some platforms have limitations or special requirements.

### Domain
**Question:** Do you have a custom domain for this project?
- [ ] Yes: _______________
- [ ] No, will use hosting provider's domain
- [x] Will get one later

### Design System
**Question:** Any preference for UI framework or design system?
- [x] Tailwind CSS (recommended, highly customizable)
- [ ] Material-UI / MUI (Google's Material Design)
- [ ] Chakra UI (accessible components)
- [ ] Custom CSS
- [ ] No preference / you decide
- [ ] Other: _______________

**Why this matters:** This affects development speed and the look/feel of the app.

### Analytics
**Question:** Do you want to track usage analytics?
- [ ] Yes, please include Google Analytics (or similar)
- [x] Yes, but privacy-focused only (no personal data)
- [ ] No analytics needed
- [ ] Decide later

---

## 5. Content & Realism

### Realism Level
**Question:** How realistic should the financial simulation be?
- [ ] **Simplified:** Round numbers, approximate taxes, general concepts
- [ ] **Realistic:** Accurate calculations, real prices, true-to-life complexity
- [ ] **Balanced:** Accurate numbers but simplified presentation (recommended)

**Why this matters:** Too simple might not be educational enough; too complex might be overwhelming.

### Price Data
**Question:** Should we base prices on:
- [ ] National averages
- [ ] Specific city/region: _______________
- [ ] Range of cities (low, medium, high cost)
- [x] Let users choose their location

**Why this matters:** A $1,500 apartment is cheap in San Francisco but expensive in rural Texas.

### Job Selection
**Question:** What types of jobs should we include?
- [ ] Entry-level only (minimum wage to $40k)
- [ ] Wide range (minimum wage to six figures)
- [ ] Focus on common jobs for young people (retail, food service, etc.)
- [ ] Include professional careers (engineer, nurse, teacher, etc.)
- [x] All of the above

**Question:** Should jobs have requirements?
- [ ] No requirements, all jobs available
- [x] Education requirements (high school, college, etc.)
- [ ] Unlock jobs as simulation progresses
- [ ] Other: _______________

---

## 6. Educational Goals

### Learning Objectives
**Question:** What are the top 3 things you want users to learn?

1. Financial responsibility.
2. Understanding taxes.
3. Impact of lifestyle choices on budget.

Examples:
- Understanding take-home vs. gross pay
- Importance of emergency savings
- Impact of lifestyle choices on budget
- How compound interest works
- Credit score factors
- Tax bracket system

### Teaching Style
**Question:** How should the app teach concepts?
- [ ] Explicit lessons/tutorials upfront
- [ ] Learning by doing (discover through gameplay)
- [ ] Tooltips and hints throughout
- [x] Combination of all above (recommended)
- [ ] Other: _______________

---

## 7. Timeline & Resources

### Timeline
**Question:** Is there a target launch date or deadline?
- [x] No rush, quality is more important than speed
- [ ] Target date: _______________
- [ ] Specific event/milestone: _______________

**Question:** Do you need the full feature set by that date, or is an MVP sufficient?
- [ ] Full feature set required
- [x] MVP first, then iterate
- [ ] Whatever is reasonable

### Resources
**Question:** Will you be able to help with content creation?
- [ ] Yes, I can provide/verify realistic prices and data
- [ ] Yes, I can test with target users
- [ ] Yes, I can provide feedback on UX/design
- [ ] Yes, I can help with documentation
- [x] No, need full implementation
- [ ] Other: _______________

---

## 8. Success Criteria

### How will you measure success?
**Question:** What does success look like for this project?

Please rank these by importance (1 = most important):

- [ ] Users understand budgeting better after using it (rank: 1)
- [ ] Kids are engaged and enjoy using it (rank: 1)
- [ ] Calculations are accurate and realistic (rank: 2)
- [ ] App is easy to use without instructions (rank: 1)
- [ ] Works well on phones and tablets (rank: 1)
- [ ] Users spend meaningful time exploring scenarios (rank: 1)
- [ ] Positive feedback from teachers/parents (rank: 1)
- [ ] Other: _______________ (rank: ___)

### Target Usage
**Question:** How many users do you expect?
- [ ] Just my own family (1-10 users)
- [ ] Local community/classroom (10-50 users)
- [ ] Public website (could be hundreds+)
- [x] Don't know yet

**Why this matters:** This affects hosting needs and whether we need user accounts.

---

## 9. Accessibility & Inclusivity

### Accessibility
**Question:** Are there specific accessibility needs?
- [ ] Must support screen readers
- [ ] Must have high contrast mode
- [ ] Must work without mouse (keyboard only)
- [ ] Must support multiple languages (which?): _______________
- [x] Standard web accessibility is fine
- [ ] Other: _______________

### Inclusivity
**Question:** Any specific considerations for diverse audiences?
- [ ] Include diverse job examples
- [ ] Support various family structures
- [ ] Acknowledge different starting points (debt, family support)
- [ ] Avoid assumptions about "normal" life paths
- [x] All of the above (recommended)
- [ ] Other: _______________

---

## 10. Future Vision

### Long-term Goals
**Question:** What's your vision for this project beyond the initial release?

- [ ] One-time project, minimal maintenance
- [x] Ongoing updates with new features
- [x] Community contributions welcome
- [ ] Potential commercial use
- [x] Open source for others to use/modify
- [ ] Not sure yet

**Question:** Should we design with specific future features in mind?
Examples: multiplayer mode, teacher dashboards, mobile app, API for third parties

_______________________________________________
_______________________________________________
_______________________________________________

---

## 11. Budget & Constraints

### Budget
**Question:** Is there a budget for this project?
- [ ] Open source / volunteer work
- [ ] Limited budget: $_______________
- [ ] Flexible budget
- [x] Not applicable

**Why this matters:** This affects whether we can use paid services, premium UI libraries, or paid hosting.

### Technical Constraints
**Question:** Are there any technical constraints or requirements?
- [x] Must work without internet (offline-first)
- [ ] Must work on old browsers (which?): _______________
- [x] Must be very fast (<1 second load time)
- [x] Must be printable
- [ ] Must export data in specific format: _______________
- [ ] No special constraints

---

## 12. Branding & Style

### Name
**Question:** Is "Adulting Simulator" the final name?
- [x] Yes, keep this name
- [ ] No, the name should be: _______________
- [ ] Not decided yet

### Visual Style
**Question:** Any preferences for look and feel?
- [ ] Fun and playful (bright colors, animations)
- [ ] Professional and serious (muted colors, minimal)
- [ ] Balanced (engaging but not childish)
- [ ] Match existing brand/website: _______________
- [x] No preference / you decide

**Question:** Any color preferences or requirements?
_______________________________________________

**Question:** Any inspiration websites or apps?
1. _______________
2. _______________
3. _______________

---

## Summary & Next Steps

Once you've answered these questions, the implementation can be tailored specifically to your needs. The answers will guide:

1. **What to build first** (MVP scope)
2. **How complex to make it** (realism vs. simplicity)
3. **What data to include** (geographic scope)
4. **How to design it** (age-appropriate UX)
5. **Where to deploy it** (hosting choice)

### Prioritization Note
If you're unsure about any answers, here are my recommendations for a successful first version:

- **Target Audience:** High school age (15-18)
- **Tax Complexity:** Start simple, add advanced mode later
- **Geography:** Generic US with optional state selection
- **Tech Stack:** Next.js + Tailwind CSS + Vercel (all free)
- **MVP Features:** Job selection, expenses, monthly summary (issues #1-13)
- **Timeline:** MVP in 4-6 weeks, full features in 8-12 weeks

### How to Provide Answers

Please either:
1. Edit this file directly with your answers
2. Create a new issue with your responses
3. Reply with your answers in whatever format works for you

---

**Last Updated:** 2026-01-14  
**Status:** ✅ **Completed - All questions answered**  
**Next Action:** Begin implementation following IMPLEMENTATION_ROADMAP.md
