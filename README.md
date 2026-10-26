Personal Expense Tracker for Students
A responsive web application that helps students track daily expenses, manage monthly budgets, understand spending habits, and build better saving practices.

The project is designed around a simple question: Where is my money going, and am I staying within my budget?
Features
- Authentication — Sign up, log in, log out, and reset passwords using Firebase Authentication.
- Expense management — Add, view, edit, and delete expense transactions.
- Monthly budgets — Set or update a budget for a selected calendar month.
- Dashboard analytics — View total spending, remaining budget, budget utilization, and category breakdowns.
- Category tracking — Organize expenses into Food, Travel, Education, Shopping, Entertainment, Bills, Health, and Other.
- Monthly history — Switch between months to review previous spending and budgets.
- Spending insights — Display rule-based observations based on spending patterns and budget progress.
- Responsive interface — Designed for mobile screens, tablets, and desktops.
- Data protection — User-owned records are intended to be protected with Firebase Authentication and Firestore Security Rules.
Project status: Update this section to reflect the current implementation. Do not describe features as complete until they have been implemented and tested.

Tech Stack
Technology	Purpose
React	User interface
Vite	Development server and build tooling
Tailwind CSS	Styling and responsive layouts
Firebase Authentication	Email/password authentication
Cloud Firestore	Persistent user and expense data
JavaScript	Application logic


Expense Categories
- Food
- Travel
- Education
- Shopping
- Entertainment
- Bills
- Health
- Other
Budget Calculations
The dashboard can derive its metrics from the selected month's transactions and budget:
- Total spent: Sum of expenses for the selected month.
- Remaining budget: Monthly budget − total spent.
- Budget utilization: Total spent ÷ monthly budget × 100.
- Average daily spend: Total spent ÷ days elapsed.
- Projected spend: Average daily spend × days in the month.
- Potential savings: Maximum of (monthly budget − projected spend) and zero.
Budget status thresholds in the design specification:
Status	Budget utilization
On track	Below 70%
Caution	70% to below 90%
High usage	90% to 100%
Over budget	Above 100%


These indicators are estimates based on recorded expenses, not financial guarantees.
Getting Started
Prerequisites
- Node.js and npm
- A Firebase project
- Access to the project repository
1. Clone the repository
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_PROJECT_FOLDER>
Replace the placeholders with your GitHub repository URL and the actual project folder name.
2. Install dependencies
npm install
3. Configure Firebase
In the Firebase Console:
1. Create or select a Firebase project.
2. Enable Email/Password under Authentication sign-in providers.
3. Create a Cloud Firestore database.
4. Configure restrictive Firestore Security Rules so each signed-in user can access only their own records.
5. Register a web app and copy its Firebase configuration values.
4. Add environment variables
Create a .env.local file in the project root and add the following Vite environment variables:
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
Replace the example values with your Firebase web app configuration. Do not commit .env.local or private credentials to GitHub. Ensure the file is covered by .gitignore.

Firebase web configuration values are used by the client SDK; Firestore Security Rules are essential for protecting user data. Never place Firebase Admin SDK credentials or service-account private keys in frontend code.
5. Start the development server
npm run dev
Open the local URL printed by Vite in your terminal.
6. Build for production
npm run build
If the project includes a preview script, you can inspect the production build locally with:
npm run preview
Available scripts depend on the repository's package.json.
Data Structure
The planned Cloud Firestore structure is organized by authenticated user:
/users/{uid}
/users/{uid}/transactions/{transactionId}
/users/{uid}/budgets/{yyyy-MM}
/users/{uid}/categories/{categoryId}
Each expense transaction is associated with a user and includes fields such as amount, category, date, month key, and optional note or payment method. Monthly budgets are stored separately.
Security
Security is a core requirement of this project:
- Require authentication for protected user data.
- Restrict reads and writes to the signed-in user's own records.
- Validate expense and budget values before writing.
- Keep Firestore Security Rules restrictive; never use blanket public read/write rules.
- Test authorization rules with the Firebase Emulator Suite before production deployment.
- Keep private credentials out of source control.
Client-side validation improves usability but does not replace server-enforced Firestore Security Rules.
Suggested Project Roadmap
- [ ] Configure React, Vite, Tailwind CSS, and Firebase
- [ ] Implement authentication and protected routes
- [ ] Add expense creation, editing, deletion, and filtering
- [ ] Implement monthly budget management
- [ ] Build dashboard metrics and category analysis
- [ ] Add deterministic spending insights
- [ ] Test responsive layouts, validation, and error states
- [ ] Test Firestore security rules and critical user journeys
- [ ] Verify the production build and deployment configuration
Update this checklist as work is completed.
Scope
The initial version focuses on personal expense tracking and monthly budget awareness. The following are outside the planned MVP scope:
- Automatic bank transaction imports
- UPI or payment gateway integration
- Investment tracking
- Receipt OCR
- Shared wallets and group budgets
- AI-generated financial advice
- Native Android or iOS applications
Contributing
Contributions and suggestions are welcome. For substantial changes, open an issue first to discuss the proposed improvement. Please keep financial calculations centralized and preserve user-level access controls.
License
No license has been specified yet. Add a LICENSE file and update this section before presenting the repository as open source.
Built to help students make their spending more visible and their budgets easier to manage.