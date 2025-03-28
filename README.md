# content-movement-testing
Allows external organisation to test for content movement within International SNOMED CT in the current authoring cycle, via a set of ECL statements.

## Alert levels
The email that is produced will identify an alert level which is keyed to the amount of content movement detected.   This may be configured per ECL statement.

## Folder Structure
    <folder> - Entity name. For example "uk-nhs" the name of this folder will be passed to the report along with an email distribution list and (optionally) the name of a high usage list.
      <folder> - Category.  For example "procedures" - each folder at this level will appear in a separate tab in the final report.
        <filename.json> - each json file will contain an ECL statement that is designed to detect if the model has been changed in a particular section of content

## Configuration File


## ECL File
    {
        "name": "Xrays using contrast",
        "ecl" : "<< 168537006 |Plain X-ray (procedure)| : { 260686004 |Method (attribute)| = 312254007 |Plain X-ray imaging - action (qualifier value)|, 424361007 |Using substance (attribute)| = 419098001 |Radiographic imaging contrast media (substance)| }",
        "alertThreshold": { count : 3,
                            setLevel : 7 },
        "highUsageAlertThreshold": { count : 1,
                            setLevel : 7 }
    }

## Report Output

This report will send an email to the distribution list supplied.   The subject of the email will indicate the alert level and the email will contain a link to a GoogleSheet.  The GoogleSheet can be viewed by anyone who has the link, and a Google account is not required.

In addition to a tab for each , a tab will be produced that lists concepts added and removed, with an indicator if a removed concept has been identified as 'high usage'.
