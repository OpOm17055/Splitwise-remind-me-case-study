# PRD: Remind Me and UPI Pay for Splitwise

**Author:** Omprakash Balara · **Status:** Draft · **Date:** October 2026

## 1. Research

I interviewed 10 Splitwise users, from college students (17) to salaried and married professionals (23 to 30s), about how they split group bills and settle up. Three interviews are written up in detail below; the other seven gave very similar answers.

| Participant | Profile | Key pain points |
|---|---|---|
| P1 | 23, salaried | Uncomfortable asking friends for money; pays from another app, forgets, and pays late; splitting is painful when he pays first |
| P2 | 17, college student | Uncomfortable asking for money back; adding friends' bills by hand is tedious; no idea where his money goes |
| P3 | Married, salaried | Forgets to pay his Splitwise dues and feels embarrassed when asked; typing long bills is hard; wants monthly expense reports |

The interviews raised four problems:

| Problem | Raised in detailed interviews | Already solved? |
|---|---|---|
| Entering long bills by hand | 3 of 3 | Yes, Splitwise Pro has receipt scanning and itemization |
| No monthly, category-wise view of spending | 3 of 3 | Yes, Splitwise Pro has charts and graphs |
| Awkward to ask for money, or to be asked | 3 of 3 | **No.** Only a manual Remind button |
| Forgetting to pay because paying happens in another app | 2 of 3 | **No.** There's no UPI payment inside Splitwise |

The first two are already covered by Splitwise Pro, so this PRD focuses on the last two.

## 2. Problem

Asking a friend for money feels awkward, and being asked feels embarrassing. Splitwise's Remind button does send a reminder, but the person who is owed has to decide to press it every time, so it still feels like asking personally. As a result:

- people who are owed feel uncomfortable reminding friends, so they put it off (P1, P2)
- people who owe simply forget, then feel embarrassed when a friend finally asks (P3)
- even after a reminder, paying means leaving Splitwise for a UPI app and then coming back to mark the debt as settled. People forget the payment, the "mark as settled" step, or both (P1, P3)

**Key insight:** the problem is social, not technical. If the person who owes sets their own reminders and can pay in one tap, the friend never has to ask, and nobody feels embarrassed.

## 3. Users

- **The borrower** (like P1, P3): means to pay but forgets, and would rather be reminded by their own phone than by a friend. This is the main user.
- **The lender** (like P1, P2): paid for the group and wants the money back without having to ask.

## 4. Solution: Remind Me with UPI Pay

### Part 1: Remind Me (the borrower sets their own reminders)
1. On a balance where they owe money ("You owe Priya ₹655"), the borrower turns on **Remind me to pay**.
2. They choose how often: daily, every 2 days, every 3 days, weekly, or a custom number of days, plus the time of day.
3. Splitwise sends **them** a private notification on that schedule: "You owe Priya ₹655 for Dinner at Barbeque Nation", with **Pay now** and **Remind me later** (snooze for 1 day).
4. Reminders keep going until the debt is settled, then stop automatically.
5. Optional, on by default: **Let Priya know I've set a reminder.** Priya sees "Rahul has set a reminder to pay you" on her side, so she knows she doesn't need to ask.
6. Splitwise also prompts it at the right moment: when a new expense makes someone owe money, it shows "Want a reminder to pay Priya?"

The lender keeps today's manual Remind button, but the aim is that they rarely need it.

### Part 2: Pay directly from Splitwise (UPI)
1. On any balance or reminder, the person who owes taps **Pay ₹655 via UPI**.
2. They pick their UPI app (GPay, PhonePe, Paytm, BHIM). It opens with the friend's UPI ID, the amount and a note ("Splitwise: Dinner at Barbeque Nation") already filled in.
3. They confirm with their UPI PIN as usual. The money goes straight from their bank to the friend's bank, and Splitwise never holds it.
4. When the payment succeeds, Splitwise marks the debt as settled, notifies the friend, and stops the reminders.
5. One-time setup: each user adds their UPI ID to their Splitwise profile. If the friend hasn't added one, the app asks them to ("Add your UPI ID to get paid faster").

**Defaults:** off until the borrower turns it on; quiet hours from 10pm to 9am; at most one reminder a day.

**Out of scope (v1):** a Splitwise wallet, card payments, SMS or WhatsApp reminders, different settings per expense.

## 5. Success metrics

| Type | Metric | Goal |
|---|---|---|
| North Star | % of debts settled within 7 days | +15% |
| Primary | Average days from expense to settle-up | Down 30% |
| Primary | % of borrowers who turn on Remind me | 25% in 3 months |
| Primary | % of settle-ups paid through UPI inside Splitwise | 30% in 3 months |
| Secondary | % of users who have added a UPI ID | 50% of active users |
| Secondary | Manual Remind button presses by lenders | Down (fewer people need to ask) |
| Guardrail | UPI payments that fail or aren't marked as settled correctly | Below 2% |
| Guardrail | Borrowers muting Splitwise notifications or uninstalling | No rise |
| Guardrail | Borrowers snoozing more than 3 times in a row | Low (a sign reminders are annoying) |

## 6. Business value

Faster settling makes Splitwise more useful, so people come back to it more often. With UPI Pay, Splitwise becomes the place where group money is both tracked and settled, and that opens payment partnerships with UPI apps or banks. It also opens a monetization option: a basic weekly reminder for everyone, with custom intervals included in Pro.

## 7. Risks

- **Reminders feel like spam:** the borrower chooses the schedule, with quiet hours, a daily cap and snooze.
- **Borrowers don't turn it on:** prompt them right after a new expense, and show lenders a gentle "Suggest a reminder to Rahul" option.
- **Wrong reminders** (paid in cash but not marked): a "Paid outside Splitwise" option that the lender confirms in one tap.
- **Payment not confirmed back:** if the UPI app doesn't return a clear success status, ask the friend who was paid to confirm before marking the debt as settled.
- **Trust and regulation:** use the standard UPI intent so the payment happens in the user's own UPI app. Splitwise never stores PINs or holds money.

## 8. Future opportunities

- Interviewees also asked for trip budgets (P1), savings tips (P2), and simple investing suggestions (P1, P3).

## 9. Next steps

Build a clickable Figma prototype, test it with 5 interviewees, and refine.
