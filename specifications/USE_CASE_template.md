# Use Case Specification Template

## 1. Use Case: [Use Case Name]

*   **ID:** UC-[Number] (e.g., UC-001)
*   **Version:** [Version number]
*   **Date:** [Date created/updated]
*   **Author(s):** [Name(s)]
*   **Related Requirements:** [Link to relevant requirement IDs, e.g., FR-001, FR-005]

## 2. Brief Description

*Provide a short summary of the goal this use case achieves for the primary actor.*

## 3. Actors

*   **Primary Actor:** [The main user or system initiating the use case]
*   **Secondary Actor(s):** [Other users or systems involved in the use case (if any)]

## 4. Preconditions

*List the conditions that must be true before the use case can start.*

1.  [Condition 1, e.g., User is logged into the system]
2.  [Condition 2, e.g., System has access to the customer database]
3.  ...

## 5. Postconditions

*Describe the state of the system after the use case completes successfully.*

*   **Success Postcondition(s):**
    1.  [State 1 after successful completion, e.g., Order is created with status 'Pending']
    2.  [State 2 after successful completion, e.g., Confirmation email is sent to the user]
    3.  ...
*   **Failure Postcondition(s):**
    1.  [State 1 if the use case fails, e.g., System state remains unchanged]
    2.  [State 2 if the use case fails, e.g., An error is logged]
    3.  ...

## 6. Basic Flow (Main Success Scenario)

*Describe the step-by-step interaction between the actor(s) and the system for the most common success path.*

| Step | Actor Action                        | System Response                                    |
| :--- | :---------------------------------- | :------------------------------------------------- |
| 1    | [e.g., User clicks 'Add to Cart']   | [e.g., System displays the shopping cart page]     |
| 2    | [e.g., User navigates to checkout]  | [e.g., System presents the checkout form]          |
| 3    | [e.g., User enters shipping details] | [e.g., System validates address format]            |
| 4    | [e.g., User submits the order]      | [e.g., System processes payment, creates order]    |
| 5    |                                     | [e.g., System displays order confirmation page]    |
| ...  | ...                                 | ...                                                |

## 7. Alternative Flows (Extensions)

*Describe alternative paths or variations from the basic flow, including error handling. Reference the step in the basic flow where the alternative begins.*

*   **7.A: [Name of Alternative Flow, e.g., Invalid Address]**
    *   **Trigger:** [Condition that triggers this flow, e.g., Address validation fails at step 3]
    *   **Steps:**
        1.  [System displays an error message indicating invalid address.]
        2.  [User corrects the address.]
        3.  [Use case resumes at step 3 of the Basic Flow.]

*   **7.B: [Name of Alternative Flow, e.g., Payment Declined]**
    *   **Trigger:** [e.g., Payment processor declines transaction at step 4]
    *   **Steps:**
        1.  [System displays a payment declined message.]
        2.  [User is prompted to enter different payment details or cancel.]
        3.  **(If user provides new details):** [Use case resumes at step 4 of the Basic Flow.]
        4.  **(If user cancels):** [Use case terminates. Failure postcondition applies.]

*   **(Add more alternative flows as needed)**

## 8. Special Requirements

*List any non-functional requirements specific to this use case (e.g., performance, security, usability constraints not covered elsewhere).*

*   [e.g., The order submission (Step 4) must complete within 3 seconds.]
*   [e.g., Payment details must not be logged.]

## 9. Frequency of Use

*Estimate how often this use case will be executed (e.g., multiple times per hour, daily, rarely).*

## 10. Open Issues

*List any unresolved questions or items needing clarification related to this use case.* 