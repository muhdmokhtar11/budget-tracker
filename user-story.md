**Title**: Track Monthly Income and Expenses

**As a** User of the personal budget manager website
**I want** to be able to easily record and categorize my income and expenses each month
**So that** I can understand where my money is coming from and going, and identify areas where I can save.

**Business Logic**:
- Each transaction (income or expense) must be associated with a category.
- The system should automatically calculate the total income, total expenses, and net savings/deficit for each month.
- The system should prevent users from entering future dates for transactions.

**Acceptance Criteria**:
1. I can add new income transactions with details like date, amount, source (e.g., salary, investment), and category (e.g., salary, dividends).
2. I can add new expense transactions with details like date, amount, payee, and category (e.g., groceries, rent, entertainment).
3. The system accurately calculates and displays the total income, total expenses, and net savings/deficit for the current month.
4. I can edit and delete existing income and expense transactions.
5. The system displays an error message if I try to enter a transaction date in the future.

**Functional Requirements**:
- Ability to add new income and expense transactions.
- Ability to edit and delete existing transactions.
- Categorization of income and expenses.
- Automatic calculation of monthly totals and net savings/deficit.
- Date validation to prevent future-dated transactions.
- Display of transaction history for the current month.

**Non-Functional Requirements**:
- The system should be responsive and accessible on different devices (desktop, tablet, mobile).
- The system should be performant, with quick loading times for transaction entry and display.
- The system should be secure, protecting user data from unauthorized access.

**UI Design**:
- A clear and intuitive form for entering income and expense transactions.
- A visually appealing display of monthly totals and net savings/deficit.
- A user-friendly interface for browsing and editing transaction history.
- Use of color-coding to differentiate between income and expenses.
