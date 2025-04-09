# Loan Approval System
This DAML-based loan system manages loan requests, approvals, token disbursements, and repayments. A loan limit contract enforces lending restrictions. Borrowers repay incrementally, and the bank archives the loan upon full repayment. The system demonstrates DAML workflows, validation, and token management.

## Overview

This project implements a comprehensive loan approval, disbursement, and repayment system using DAML. The solution addresses three levels of complexity as outlined in the requirements, from basic loan approval to token disbursement with limit validation, and finally to a repayment workflow.

## Approach

### 1. Basic Loan Approval
- Implemented `LoanRequest` and `Loan` templates with core functionality.
- Created a simple approval workflow where banks can approve requests.
- Designed the system to automatically archive requests and create loan contracts upon approval.

### 2. Token Disbursement with Limit Validation
- Added `Token` and `LoanLimit` templates to track available funds.
- Implemented validation to ensure loan amounts don't exceed bank limits.
- Created a disbursement mechanism with proper authorization checks.
- Added assertions to prevent over-disbursement.

### 3. Repayment Workflow
- Introduced `RepaymentRestriction` template for minimum payment rules.
- Implemented incremental repayment functionality.
- Added logic to track repaid amounts and automatically archive paid loans.
- Updated loan limit utilization upon full repayment.

## Design Decisions

- **Token Model**: Used an account-based token model for simplicity in tracking balances.
- **Authorization**: Ensured strict authorization checks for all sensitive operations.
- **State Management**: Maintained clear state transitions between request, approval, disbursement, and repayment phases.
- **Validation**: Implemented comprehensive validation at each workflow step.
- **Atomicity**: Designed choices to maintain atomic operations where appropriate.

## How to Run the Code

### Prerequisites
- DAML SDK installed
- Java Development Kit (JDK) 11 or later

### Steps
1. Clone the repository
2. Navigate to the project directory
3. Build the project:
    ```bash
    daml build
    ```
4. Run the tests to verify functionality:
    ```bash
    daml test
    ```
5. Start the sandbox environment:
    ```bash
    daml start
    ```
6. Access the Navigator at `http://localhost:7500` to interact with the application.

## Key Files
- `CarlEslabon_TakeHomeAssignment/LoanRepayment`: Main implementation containing all templates and workflows
- `CarlEslabon_TakeHomeAssignment/LoanRepayment/Test_LoanRequestApproval.daml`: Comprehensive test suite covering all requirements
- `daml.yaml`: Project configuration file

## Assumptions
- A single bank entity exists in the system (could be extended to multiple banks).
- Tokens represent fiat currency amounts (1 token = 1 currency unit).
- The system operates in a trusted environment where participants are properly authenticated.
- Interest calculations are not part of this implementation (could be added as an extension).
- Time-based repayment schedules are not implemented (could be added).

## Future Enhancements
- Support for multiple currencies
- Interest calculation and payment scheduling
- Credit scoring integration
- Collateral management
- Multi-bank support with competitive loan terms

This implementation provides a solid foundation for a DAML-based loan management system that can be extended to meet more complex financial requirements.