#User Stories - Healthcare management System

# Domain Context Mapping
You need to identify the main entities and bounded contexts.

A. Patient Management
Bounded Context: Patient Management

Main entities:
•	Patient 
•	Appointment 
•	Doctor 
•	Medical Record 
•	Contact Information 

Purpose:
Manages patient information and appointments.

B. Billing & Insurance Claims

Bounded Context: Billing & Insurance Claims

Main entities:
•	Bill 
•	Payment 
•	Insurance Claim 
•	Insurance Provider 
•	Invoice 

Purpose:
Manages patient bills, payments, and insurance claims

C. Lab Test Diagnostics

Bounded Context: Lab Test Diagnostics

Main entities:
•	Lab Test 
•	Test Order 
•	Test Result 
•	Laboratory 
•	Technician 

Purpose:
Manages laboratory tests and their results

## Scenario 1
Scenario 1: Ordering a Specialized Blood Panel during an Appointment
•	As a primary care physician,
•	I want to attach a specific lab test type (e.g., "Comprehensive Metabolic Panel" or "Hemoglobin A1c") directly to a patient's appointment order,
•	So that the laboratory department knows exactly what diagnostic work needs to be performed when the patient arrives.

```gherkin
Scenario: Physician attaches a specialized blood test to an appointment
  Given the physician is viewing the patient's active consultation record
  When they select the "Add Lab Test" option and choose "Hemoglobin A1c" from the test catalog
  Then the system should link the lab test order to the current appointment ID
  And send a requisition notification to the Lab Test Diagnostics Context database
  And display the test type under the patient's upcoming appointment summary
```

## Scenario 2
Scenario 2: Patient Selecting a Lab Test Location and Pre-Appointment Instructions
As a patient with a doctor's order for a specialized test,
I want to view specific pre-test instructions (such as fasting for 12 hours) for my scheduled "Lipid Panel" lab test,
So that I can properly prepare for the procedure before arriving at the clinic.

```gherkin
Scenario: Patient views pre-test instructions for a specific diagnostic test
  Given the patient has a scheduled appointment that includes a "Lipid Panel" lab test
  When they open the appointment details view in the portal
  Then the system should display a dedicated "Preparation Instructions" card
  And explicitly show instructions such as "Fasting required for 12 hours prior to the test"
  And allow the patient to download a PDF copy of the instructions
```
