MED-01 : 
Profiles: Medical Domestic Approvals , Medical Domestic Claims
Roles: 
Domestic Medical Claim
Medical Domestic Approval
Medical Team Supervisor

MED-02 : 
Sharing Settings of Medical Request is Public Read Only for default internal access and Private for default external access.
Sharing Rules: approval_team , claims_team . allowing red/write access to respective teams based on their roles

MED-03 : 
Medical Request Record Types:
- Domestic Approvals
- Domestic Claims
- Domestic Miscellaneous
Each record type has different process, layout , record page and Picklists values.

MED-04 :
Added medical request related list on insured entity record page.

MED-06 : 
ownership of medical request is always a queue.
validation rule : Restrict_Ownership_to_Queue
Queues : 
Medical_Domestic_Approvals
Medical_Domestic_Claims
Medical_Domestic_Miscellaneous
flow: 
Assign_Medical_Request_to_Queue : record triggered flow that assigns medical requests to queue on creation based on record type.
custom field on medical request : Working_By__c , shows the user currently handling the request during the active shift. It has a lookup filter to ensure that profile of the user handling the request is either from Medical Domestic Approvals or Medical Domestic Claims (or system administrator).

MED-07 :
configured search setup and search layout of insured entity object 

MED-08 :
record triggered flow on medical request creation to link it to contact using Insured Entity : Request_Auto_Link_Contact
added medical request related list on contact record page 

MED-09 & 10 & 11 : 
configured status picklist values for each record type and created 3 paths(Approval_Status, Claim_Status, Miscellaneous_Status) , one for each record type and added it to its respective record page.

MED-12 :
created custom fields (Chronic_Medication_Reminder__c  , Days_Remaining__c , Reminder_Sent__c) on medical request object , appears on approvals record type only when service type is chronic medications
created scheduled flow (chronic_medication_reminder)  that when reminder is needed:
      - creates a new Approval Request with description that shows that this is related to original request "Req-1234.
      - flow sends notification to approvals queue. targetid: new request created
      

MED-16 : 
Made Reports in folder (Medical Requests Reports): 
   Medical Requests by Insurance Provider
   Medical Requests Claim Amounts
   Open Medical Requests
   Closed/Open Requests by Users
   Closed/Open Requests by Month
   SLA Report
   Medical Requests by Contract
   Claim Amounts by Contract
Made Dashboard in folder (Medical Requests Dashboards): Medical Requests Dashboard

MED-17 : 
screen flow : New_Bank_Account , custom button on bank account object : New , custom lookup field on bank account object : Medical_Request__c

MED-18 :
created custom fields : claim amount,  refunded amount (both for claims record type only)