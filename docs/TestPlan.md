
# Test Plan: Payment Funnel API

## **1. Introduction and Objectives**

The main objective of this test plan is to ensure the stability and functionality of the End-to-End (E2E) payment flow. Through the execution of automated API tests, the goal is to verify that the system meets its functional and business requirements, ensuring a smooth and uninterrupted user experience. The plan aims to proactively detect and document any defects in service integration, data validation, and process logic, thus guaranteeing product quality before deployment to a production environment.

## **2. Scope**

This test plan focuses on validating the system's core flow. The following functionalities are explicitly included within the scope:

 - **Payment Creation:** Validation of payment order generation, verifying that request data (including amount and currency) is
   processed correctly and that the system returns a valid payment_id.
 - **User Management:** Testing of user registration and authentication processes via the API, ensuring new users can be created and login
   credentials function correctly.
 - **Credit Application Flow:** Sequential validation of each step in the application funnel, including personal data capture, CURP
   validation, payment offer selection, and digital contract signing.
 - **Third-Party Integration and Validations:** Verification of correct communication between endpoints, including coupon application and
   final payment validation with an external reference.

*The following areas are excluded from the scope of this plan:*

 - **Performance and Load Testing:** Response times under high volumes of transactions or concurrent users will not be measured.

 - **Exhaustive Security Testing:** Penetration testing, vulnerability analysis, or API-level fuzzing will not be performed.

 - **UI/UX Testing:** This plan focuses solely on the API's behavior, not on the user interface.


## **3. **Test Strategy****

The test strategy is based on API automation to allow for fast and repeatable execution of the core flow. An E2E regression testing approach will be used to ensure that future changes do not introduce defects into the payment process.

### ***Test Types:***

**Functional Tests:** Each API request and response will be validated for correctness, and data will be handled according to specifications.

**Integration Tests:** Data flow will be confirmed to be correct across the different services and endpoints (e.g., the payment_id created is correctly associated with the user and credit application).

**Negative Tests:** Controlled error scenarios will be tested (e.g., already-registered email, incorrect credentials) to verify that the API returns appropriate error codes (e.g., 400 Bad Request, 401 Unauthorized).

**Regression Tests:** The Postman collection will serve as a regression suite to be executed after each new deployment.

### ***Tools:***

**Postman:** To design and document test cases.

**Newman:** The command-line tool for automating collection execution in CI/CD (Continuous Integration and Continuous Delivery) environments.

## **4. Test Environment**

Tests will be executed in the Staging environment, a pre-production environment that faithfully replicates the live system's configuration. Environment variables (BASE_URL, API_KEY, sessionId, etc.) will be managed centrally in a Postman environment file to ensure tests are reusable and secure. The test client will be the Newman command line, simulating requests from a server environment.

## **5. Resources and Responsibilities**

The test plan will be designed, executed, and maintained by the QA Engineer, who will be responsible for ensuring the quality of the payment flow. The main resources are the mentioned tools (Postman, Newman, GitHub) and collaboration with the development and product teams for defect resolution. Proactive communication and documentation will be key.

## **6. Schedule**

The estimated schedule for the initial phase of this test plan, distributed over a three-week development cycle, is as follows:

**Week 1:**
*Monday to Wednesday:* Planning, requirements analysis, and detailed test case design.
*Thursday to Friday:* Test environment setup and Postman collection preparation.

**Week 2:**
*Monday to Thursday:* Implementation of automated tests in the Postman collection.
*Friday:* First execution of the E2E test suite to identify initial bugs and verify the happy path.

**Week 3:**
*Monday to Wednesday:* Results analysis, defect reporting, and follow-up with the development team.
*Thursday:* Re-execution of regression tests.
*Friday:* Creation of the final report and closure of the test cycle.

## **7. Entry and Exit Criteria**

**Entry Criteria:** Test execution will begin only when the following conditions are met:

 - All payment funnel endpoints are deployed in the Staging environment
   and are accessible.
 - Initial test data (payment_id) is available and validated.
 - Necessary environment variables are configured.

**Exit Criteria:** Tests will be considered complete when the following criteria are met:

 - 90% of test cases have passed successfully.
 - There are no outstanding critical or high-priority bugs in the
   system.
 - The deliverables (reports and test cases) are complete and ready for
   review.

## 8. Risk Management

The following potential risks and their mitigation strategies have been identified:

**Risk:** Last-minute API changes.
**Mitigation:** Maintain constant communication with developers to detect changes early and adapt test scripts proactively.

**Risk:** Inconsistent or stale test data.
**Mitigation:** Generate dynamic data (e.g., emails with {{$timestamp}}) and use environment variables to ensure tests are consistent and not dependent on static data.

**Risk:** Connectivity issues with external services.
**Mitigation:** In case of failures with third-party services (e.g., CURP validation services), use mocks or predefined test data to ensure the main flow is not blocked.

## 9. Deliverables

The following deliverables will be generated and kept updated in the GitHub repository:

-Test Plan (TestPlan.md): The current document detailing the strategy and scope.
-Test Case Collection: The Postman .json file containing all endpoints and test logic.
-Test Report (TestReport.md): A summary document of the latest execution results, including the number of passed/failed cases and key observations.

## 10. Communication Plan

Communication will be transparent and constant to keep all stakeholders informed about test progress. Updates will be shared as follows:

**Daily Updates:** A quick summary of progress and blockers will be shared in the daily team meeting.

**Weekly Reports:** A detailed report on execution progress and bug status will be sent to the team and project manager at the end of each week.

**Final Report:** An executive summary with the conclusion of the test cycle will be presented at the end of the project for deployment approval.
