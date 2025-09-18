The following document contains a detailed list of test cases for validating the end-to-end functionality of the payment flow. Each case specifies its purpose, test type, data input, and expected outcome for a thorough system validation.

ID	Case	Type	Input	Expected Result
TC01	Create MXN Payment	Functional	Valid request data to generate a payment	System returns a valid payment_id with a 200 status code
TC02	Create USD Payment	Functional	Valid request data to generate a payment in USD	System returns a valid payment_id with a 200 status code
TC03	User Registration	Functional	Unique email and password	User is created successfully, system returns 201 Created and a valid sessionId
TC04	Login	Functional	Valid credentials	System returns a valid sessionId with a 200 status code
TC05	Create Application	Integration	Request associating the payment_id with the user's sessionId	System returns a valid application_process_id with a 200 status code
TC06	Validate CURP	Functional	Valid personal data and birthdate	System returns a valid curp with a 200 status code
TC07	Personal Data	Functional	Complete personal information	System returns a 200 OK, advancing the funnel
TC08	Address	Functional	Valid address data	System returns a 200 OK, updating the user's information
TC09	Apply Valid Coupon	Functional	Valid promotion_code	System applies the discount, reflected in the response with a 200 status code
TC10	Apply Invalid Coupon	Negative	Incorrect or expired coupon code	System returns a controlled error (e.g., 400 Bad Request) with a clear error message
TC11	Get Offers	Functional	Valid sessionId	System returns a list of available payment offers with a 200 status code
TC12	Select Offer	Functional	Valid offer from the list	System confirms the selected offer with a 200 status code
TC13	Sign Contract	Functional	Request to confirm the application	Application status changes to "Confirmed" with a 200 status code
TC14	Pay Loan	Integration/E2E	Payment request with correct reference and amount	Payment is successfully processed and a 200 status code is returned
TC15	Negative Flows	Negative	Invalid data (e.g., incorrect password, expired token)	System returns an appropriate authentication error (e.g., 401 Unauthorized)
