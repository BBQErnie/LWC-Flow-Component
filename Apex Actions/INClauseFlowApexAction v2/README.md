
# IN Clause Flow Apex action v2
A flow apex action that allow you to do an IN clause query with an additional support of adding additional query filters which querying the records. 

## Input/Output(s) for action
|Parameter	               |Use for Input	   |Use for Output	   |Description 
|-|-|-|-|
| Object API Name | ✔ |  | Object API Name |
| Fields to query(Comma seperated) | ✔ |  | Fields(API Names) to query(Comma seperated) |
| Filter Field(API Name) | ✔ |  | Filter Field(API Name) |
| Filter Values Text collection | ✔ |  | A collection of Text type values to filter against. |
| Additional AND Filters (; Separated) | ✔ |  | A string with additional filters. For example: Name='Test';Rating='Cold' |
| Record Collection |  | ✔ | A collection of query results.  |

<br/>

## Usage Guidelines:

1\. For **Additional AND Filters** input \
If you want to use a checkbox or number field in the additional filters, you'll have to create a formula field that converts the field value to text type. For example, Formula field for Checkbox field:
```
CASE(Checkbox__c,
true, "true",
false, "false",
NULL)
```
Then the Additional AND Filters input will be:\
FormulaCheckbox__c = true

If you want to use multiple fields as additional filters, you can separate them by a semicolon(;). For example:\
Rating = Cold; FormulaCheckbox__c = true; Active__c='Yes'

NOTE: This is working as designed because checking the field type in the code would significantly impace the performance of this Apex action.

<br/>

2\. For **Filter Values Text collection** input \
If you're filtering based on the IDs collection, make sure the IDs are 18 digits and not 15 digits. 

<br/>

## Installation
Use the following link(s) to install the unmanaged(unlocked) package: 

| Version | Fixes |Package Link*	    
|-|-|-|
| 1.0 | Base Version | https://login.salesforce.com/packaging/installPackage.apexp?p0=04t6F000004PCaZQAW |

*To install the package in sandbox, replace login.salesforce.com with test.salesforce.com.