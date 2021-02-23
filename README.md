# invoicing
BEA invoicing codes, queries, instructions, and more.

**Notes about the main invoicing aggreation query**
POCs (Service Plans) are only necessary for P10 as far as billing. We pull 2 pieces of info for this: was the assessor able to obtain the service plan, and if they did, did they actually upload it. This is mostly because we had some instances where they indicated they obtain the POC, but just didn't upload to GoCanvas. These service plans/POCs are only relevant if the insured lives in an ALF.

CICs are only relevant for P5i and are specifically requested by the partner (shown/stored in the cic_needed field in the database). We bill for CICs on the invoice in instances where CIC_needed is TRUE and the CIC was actually completed in GoCanvas (indicated by the CIC_Included and CIC_firstname fields in the query). If both of these are not true, we do not bill for the CIC.

There are instances where assessments were submitted on a video form but were completed as telephonic (this happens for all partners/carriers) - this is where we pull in the QA fields for P10 and P5 (which applies to P11 as well since the app is a direct clone of P5i). Within those fields in the query, the user manually scans for any responses that indicate the assessment was switched to telephonic and adjusts the is_telephonic flag/boolean accordingly.
