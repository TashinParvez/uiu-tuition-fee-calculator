

<div align="center">

# UIU Tuition Fee Calculator

### A clean, fast, and mobile-friendly semester fee calculator for **United International University (UIU)** students.

<p align="center">
  <img src="https://img.shields.io/badge/HTML-Frontend-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML">
  <img src="https://img.shields.io/badge/CSS-Styling-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS">
  <img src="https://img.shields.io/badge/JavaScript-Interactive-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
</p>

<p align="center">
  <img src="https://img.shields.io/github/stars/TashinParvez/uiu-tuition-fee-calculator?style=flat-square" alt="Stars">
  <img src="https://img.shields.io/github/forks/TashinParvez/uiu-tuition-fee-calculator?style=flat-square" alt="Forks">
  <img src="https://img.shields.io/github/issues/TashinParvez/uiu-tuition-fee-calculator?style=flat-square" alt="Issues">
  <img src="https://img.shields.io/github/last-commit/TashinParvez/uiu-tuition-fee-calculator?style=flat-square" alt="Last Commit">
  <img src="https://img.shields.io/github/languages/top/TashinParvez/uiu-tuition-fee-calculator?style=flat-square" alt="Top Language">
  <img src="https://img.shields.io/github/repo-size/TashinParvez/uiu-tuition-fee-calculator?style=flat-square" alt="Repo Size">
</p>

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Visit%20Site-brightgreen?style=for-the-badge)](https://tashinparvez.github.io/uiu-tuition-fee-calculator/)
</div>


---


This project helps students estimate their semester payable amount by calculating:

- tuition based on total credits
- retake credit charges
- FYDP credit charges
- registration fee
- extra semester-specific fees
- waiver / scholarship discounts
- installment breakdowns

The calculator is designed to make UIU fee estimation easier, clearer, and quicker for students before registration or payment planning.

---

## Overview

The **UIU Tuition Fee Calculator** is a lightweight web-based tool built to simplify semester fee calculation for UIU students.

Instead of manually figuring out fresh credit fees, retake charges, FYDP costs, discounts, and installment plans, students can enter their semester details in one place and instantly view the final payable amount.

The application is especially helpful for students who want to:

- estimate their semester cost before registration
- compare different credit loads
- understand how waiver or scholarship affects tuition
- calculate the remaining amount after paying during registration
- view installment amounts in a simple format

The repository currently contains multiple HTML versions of the calculator (`3.html`, `4.html`, `5.html`, and `index.html`), with `index.html` representing the most complete version described in the project content. The repo is currently a static HTML-based project. :contentReference[oaicite:2]{index=2}

---

## Features

- **Semester fee calculation**
  - calculate total payable fee from semester input values

- **Fresh, retake, and FYDP credit support**
  - separates fresh credits from retake and FYDP credits
  - applies different rules to each category

- **Waiver and scholarship handling**
  - supports waiver percentages: `25%`, `50%`, `100%`
  - supports scholarship percentages: `25%`, `50%`, `100%`
  - applies only the **higher** of the two, not both together

- **Minimum fresh credit rule**
  - if fresh credits are below `9`, discount is not applied

- **Additional charges**
  - supports registration fee
  - supports extras such as:
    - late registration fee
    - gym membership fee
    - transportation fee
    - lab or other semester-specific charges

- **Installment calculation**
  - **Type 1:** full payable fee split into `40% · 30% · 30%`
  - **Type 2:** remaining payable amount after payment during registration, then split into `40% · 30% · 30%`

- **Responsive interface**
  - designed to be cleaner, faster, and mobile-friendly

- **Transparent calculation logic**
  - the fee rules are shown directly in the UI for clarity and trust :contentReference[oaicite:3]{index=3}

---

## How It Works

The calculator uses the following logic:

### 1. Determine the discount

```text
discount = max(scholarship percentage, waiver percentage)
```

Only the higher one is used.

Examples:

- waiver 25% + scholarship 50% → applied discount = 50%
- waiver 25% + scholarship 25% → applied discount = 25%
- none selected → applied discount = 0%

### 2. Calculate fresh credits

```text

fresh credits = total credits - retake credits - FYDP credits

```

### 3. Discount eligibility rule

If:

```text
fresh credits < 9
```

then:

```text
discount = 0
```

So even if a waiver or scholarship is selected, no discount is applied when fresh credits are below 9.

### 4. Calculate fresh credit fee

```text
fresh fee = (fresh credits × per credit fee) × (100 - discount)%
```

### 5. Calculate retake fee

```text
retake fee = (retake credits × per credit fee) / 2
```

### 6. Calculate FYDP fee

```text
FYDP fee = FYDP credits × per credit fee
```

FYDP credits do not receive waiver or scholarship discount.

### 7. Add fixed and extra fees

Registration fee and extras are added directly and do not receive discount.

### 8. Calculate final payable fee

```text
total fee = fresh fee + retake fee + FYDP fee + registration fee + extras
```

### 9. Installment plans

#### Type 1 — Without paying during registration

The full payable amount is divided as:

```text
1st installment = 40%
2nd installment = 30%
3rd installment = 30%
```

#### Type 2 — After paying during registration

```text
remaining payable = final payable fee - paid during registration
```

Then the remaining payable amount is divided as:

```text
1st installment = 40%
2nd installment = 30%
3rd installment = 30%
```

---

## Input Fields

The calculator accepts the following values:

| Field                    | Description                                        |
| ------------------------ | -------------------------------------------------- |
| Total Credits            | Total semester credits including new and retake    |
| Retake Credits           | Number of retake credits                           |
| FYDP Credits             | Number of FYDP credits                             |
| Per Credit Fee           | Cost per credit                                    |
| Registration Fee         | Semester registration fee                          |
| Extras                   | Additional semester-specific costs                 |
| Waiver Percentage        | Waiver discount percentage                         |
| Scholarship Percentage   | Scholarship discount percentage                    |
| Paid During Registration | Amount already paid before installment calculation |

These match the form and guidance text shown in the project’s main page.

---

## Use Cases

This project is useful for:

- UIU students planning their semester expenses
- students checking the effect of scholarship or waiver
- students comparing different credit combinations
- students calculating installment payments before deadlines
- anyone who wants a simpler alternative to manual fee calculations

---

## Project Structure

```text
uiu-tuition-fee-calculator/
├── index.html
├── info.html
├── uiuTFC.png
└── uiuTFC2.png
```

The repository is currently organized as a static front-end project with multiple HTML iterations and image assets. ([GitHub][1])

---

## Getting Started

Since this is a static HTML project, no package installation or build step is required.

### Run locally

1. Clone the repository:

   ```bash
   git clone https://github.com/TashinParvez/uiu-tuition-fee-calculator.git
   ```

2. Open the project folder:

   ```bash
   cd uiu-tuition-fee-calculator
   ```

3. Open `index.html` in your browser.

You can also use VS Code with the **Live Server** extension for a smoother local development experience.

---

## Why This Project

Many students struggle to estimate semester fees correctly because the calculation involves multiple conditions:

- discount eligibility depends on fresh credits
- waiver and scholarship do not stack
- retake credits use different pricing logic
- FYDP is calculated separately
- installment calculations can vary based on prior payment

This project brings those rules into one simple interface and makes the final fee easier to understand.

---

## Design Goals

This calculator was built with the following goals in mind:

- **clarity** — show the fee breakdown in a straightforward way
- **speed** — let students calculate quickly without manual math
- **accessibility** — keep the interface simple and mobile-friendly
- **transparency** — clearly show the calculation logic in the UI
- **practicality** — support real semester fee scenarios including extras and installment plans

---

## Limitations

Please note:

- this is an unofficial calculator
- actual university billing policies may change over time
- students should always verify the final amount with official UIU billing or accounts information
- calculation accuracy depends on correct user input

Adding a note like this is helpful for student-facing academic tools.

---

## Screenshots

![Main Calculator UI](./uiuTFC.png)

---

## Contribution

Contributions, ideas, and improvements are welcome.

You can contribute by:

- improving the UI
- refining calculation logic presentation
- restructuring the project files
- improving mobile responsiveness
- adding validation and edge-case handling
- writing better documentation

### To contribute

1. Fork the repository
2. Create a new branch

   ```bash
   git checkout -b feature/your-feature-name
   ```

3. Commit your changes

   ```bash
   git commit -m "Add your feature"
   ```

4. Push to your branch

   ```bash
   git push origin feature/your-feature-name
   ```

5. Open a pull request

---

## Author

**Md Tashin Parvez**
GitHub: [@TashinParvez](https://github.com/TashinParvez)

---

## Disclaimer

This project is created for educational and practical student use. It is intended to help estimate semester tuition and installment amounts, but it should not be treated as an official billing source from United International University.

Always confirm final fees with official university resources.

