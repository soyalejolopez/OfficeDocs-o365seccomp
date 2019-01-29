---
title: "Automate event-driven retention"
ms.author: stephow
author: stephow-MSFT
manager: laurawi
ms.date: 
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Strat_O365_IP
search.appverid: 
- MOE150
- MET150
description: "With labels in Office 365, you can base a retention period on when a specific type of event occurs. The event triggers the start of the retention period, and all content with a label applied for that type of event get the label's retention actions enforced on them. Event-driven retention is typically used as part of a records-management process."
---

# Automate event-based retention

 For most organizations, the volume and complexity of their data is increasing daily - email, documents, instant messages, and more. Effectively managing and governing this information is important because organizations need to:

  - > **Comply proactively with industry regulations and internal policies** that require you to retain content for a minimum period - for example, the Sarbanes-Oxley Act might require you to retain certain types of content for seven years.

  - > **Reduce your risk in the event of litigation or a security breach** by permanently deleting old content that you're no longer required to keep.

  - > **Help your organization to share knowledge effectively and be more agile** by ensuring that your users work only with content that's current and relevant to them.

The explosion of content in organizations and how it can become ROT (Redundant, Obsolete, Trivial) is serious business.

To continue to meet legal, business, and regulatory compliance challenges, businesses must be able to keep and protect important information and quickly find what’s relevant. Retaining only important pertinent information is key to a business’ success.

Hence organizations can take advantage of Retention solutions in Microsoft 365 (M365). Retention can be triggered in M365 via retention labels. The Microsoft 365 Security & Compliance Center is your one-stop portal for data governance solutions, including retention labels.

A retention label has the option to base the retention period on a specific event. Typically, period of retention can be known – such as create date or last modified date for the content. However organizations also have requirements to dispose off content based on the occurrence or timing of an event, such as 7 years after an employee leaves an organization.”

In order to ensure compliant disposal of content, it is imperative to know when an event takes place. With volume of content increasing rapidly, it is becoming challenging to retain and dispose content in a timely and compliant manner

Event based retention in M365 solves this problem. In this paper we will discuss how to set up and use event-based retention to ensure organizations effectively dispose their content based on their needs.

This paper will enable you to easily set up your business process flows to automate retention through events by using the Microsoft 365 REST API. 

## Introduction to event-based retention

An organization can be small, medium or large. The number of business documents, legal documents, employee files, contracts, and product documents that get created and managed on a day to day basis is increasing dramatically.

For example: Each day, tens and hundreds of employees are joining and leaving organizations. The HR department continues to create, update or delete employee-related documents as per business requirements. This process is subject to the different retention policies outlined for the business.

**The period of retention for content can be a known date** such as the date the content was created, last modified or labeled. For example, you might retain documents for seven years after they're created and then delete them.

**The period of retention of content can also be an unknown date**. For example, with Microsoft 365[labels in](https://docs.microsoft.com/en-us/office365/securitycompliance/labels) , you can also base a retention period on when a specific type of event occurs, such as an employee leaving the organization.

The event triggers the start of the retention period, and all content with a label applied for that type of event get the label's retention actions enforced on them.

**This is called Event Based Retention**

The diagram below shows the relationship between labels and event-type . Especially, how you can include multiple labels in one event type.

https://docs.microsoft.com/en-us/office365/securitycompliance/event-driven-retention

# Setup Event Based Retention in Microsoft 365

This section helps to understand what is needed to be done prior to retaining content.

1.  **Personas:** Identify the different roles in an organization that perform Record Management tasks that would be responsible for effective and efficient retention of business documents.

    | **Persona**                                      | **Role**                                                                              |
    | ------------------------------------------------ | ------------------------------------------------------------------------------------- |
    | Security and Compliance Center Admin (SCC Admin) | Creates Retention Event types, Retention labels and Record repositories in SharePoint |
    | Records Manager                                  | Provides Retention Policies and Retention Schedules guidance and compliance details   |
    | System Admin (business)                          | Sets up and manages external systems to work with Microsoft 365                       |
    | Information Worker                               | Manages the lifecycle of their business process (HR, Finance, IT etc)                 |

2.  **Security and Compliance Center Setup and Access:**
    
    1.  Set up access for a Global Admin
    
    2.  1.  1.  
            2.  
            3.  
            4.  
    3.  Security and Compliance Center Admin (SCC Admin) creates an event type – for example, Employee Termination or Contract Expiration or End of Product Manufacturing (Please refer to step by step process in [Event retention article](https://docs.microsoft.com/en-us/office365/securitycompliance/event-driven-retention)
    
    4.  SCC Admin creates a retention label based on an event and associates the label with an event type
    
    5.  2.  There are 4 types of triggers for retention label in SCC
            
            5.  Create date
            
            6.  Last modified
            
            7.  
            8.  Label date (when the content was labeled) 
            
            9.  Event-based
    
    6.  SCC Admin publishes the label

3.  **Setting up SharePoint:**
    
    7.  Admin creates a SharePoint site
        
        3.  Create a SharePoint library: Set event-based label at the library level (For more information https://docs.microsoft.com/en-us/office365/securitycompliance/labels\#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set )
        
        4.  Set up a Document set in SharePoint: (For more information on Document sets - https://support.office.com/en-us/article/Introduction-to-Document-Sets-3DBCD93E-0BED-46B7-B1BA-B31DE2BCD234)
        
        5.  Assign Asset Id (asset ID is a product name or code used by the organization, for example, Employee number can be an asset id)to each employee document set (By assigning the asset ID to the folder, every item in that folder automatically inherits the same asset ID. This means all the items can have their retention period triggered by the same event.

# Ways to trigger Event Based Retention in Microsoft 365

There are two ways in which Event Based Retention can be configured and triggered:

## Using Security & Compliance Center User Interface:

This is a process that can be used to retain less content at a time or the frequency to trigger retention is not often such as monthly or yearly.

  - Log in as SCC Admin 

  - SCC Admin creates an event type such as Employee Termination or Contract Expiration or End of Product Manufacturing 

  - SCC Admin creates an “Employee Termination” or “Contract Expiration” or “End of Product Manufacturing” retention label based on an event and associates the label with an event type 

  - SCC Admin publishes or auto-applies the label to the document set or library (**<span class="underline">Please note:</span>** <span class="underline"> </span> Event-based retention is not turned on for autoclassification) 

  - HR Manager or Contracts Manager or Manufacturing Manager works on a document and applies the retention label 

  - When an employee leaves the organization or a contract expires or a product manufacturing ends, the Admin **manually** creates the “Employee Left”, or “Contract Expired” or “End of Product Manufacturing” event of the event type “Employee Termination”, or “Contract Expiration” or “End of Product Manufacturing”. 

  - The creation of this event triggers the retention clock.

The above way to trigger retention can be time-consuming, prone to error and hence stunting scalability. Hence an automated seamless solution to trigger retention can enhance the security and compliance of data.

## Automated Process using a M365 REST API:

This is a process that can be used when large amounts of content is to be retained at a time and/or the frequency to trigger retention is often such as daily or weekly.

Below are 2 options you can use to automate your business process using event-based retention.

### Option 1: Microsoft Flow triggering M365 REST API

**Microsoft Flow or a similar application** can be used to trigger the occurrence of an event automatically. Microsoft Flow is an orchestrator for connecting to other systems. Using Microsoft Flow does not require a custom solution.

### Option 2: <span class="underline"> </span> PowerShell or an HTTP client to call M365 REST API

Using PowerShell (version 6 or higher) to call Microsoft 365 REST API to create events.

A Rest API is a service endpoint that supports sets of HTTP operations (methods), which provide create/retrieve/update/delete access to the service's resources.

In this case, using the Microsoft 365 REST API, events can be created and retrieved using operations (methods) POST and GET

Let’s consider the following scenarios:

# Example scenarios

## Scenario 1: Employees leaving the organization 

An organization creates and stores numerous employee related documents per employee. These documents are managed and retained during the employment of each employee. However, when the employee leaves the organization or the employment is terminated, the organization is obligated by legal and business requirements to retain the documents of that employee for a stipulated period.

Now if multiple employees leave the organization every day, the organization must trigger the retention clock of hundreds if not thousands of documents each day.

In addition to this, the retention period needs to be calculated for each of these employees as Employee termination date + number of days, months or years based on the type of the employee record. For example, worker’s compensation of the employee vs benefits filings of the same employee may need different retention.

The diagram below shows how there can be multiple labels that are associated with a single event. Here all the files under Worker’s compensation label and all the files under Employee benefits label are both associated with a single event which is the employee leaving the organization. Each of these different files have different retention clocks. So, when an employee leaves the organization, these files within each label experience a different retention period. To trigger all these different retention clocks for each file type or label for each employee is a very challenging task. Imagine doing this for multiple employees.

![](c:\\Users\\stephow\\GitHub\\officedocs-o365seccomp-pr\\SecurityCompliance/media/image3.png)

Hence an automated process to trigger these different retention clocks for multiple employees will be time-saving, error-free and extremely efficient .

**Configuring Automated Event Based Retention for this scenario:**

  - Admin c reates employee folders to the Document set such as Jane Doe, John Smith.

  - Admin adds employee files such as Benefits, Payroll, Worker’s Compensation to each employee folder

  - Admin assigns Asset Id to each employee folder. 

  - SCC Admin l

  - ogs into the Security & Compliance Center

  - SCC Admin creates employee related events types such as “Employee Termination”, “Employee Hire” events in Security and Compliance Center.

  - SCC Admin creates “Employee Retention” label in Security and Compliance Center.

  - This “Employee Retention” label is published and applied manually or automatically to the employee files in SharePoint

  - HR Management System like Workday can work with Microsoft Flow to run periodically to manage employee files

  - If an employee has left the organization, the Flow will trigger the M365 Event Based Retention REST API that will begin the retention clock on the specific employee’s files.

**Using Microsoft Flow:**

Step 1- Create a flow to create an event using the Microsoft 365 REST API

**URL: https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent**

![](c:\\Users\\stephow\\GitHub\\officedocs-o365seccomp-pr\\SecurityCompliance/media/image7.png)

![](c:\\Users\\stephow\\GitHub\\officedocs-o365seccomp-pr\\SecurityCompliance/media/image8.png)

**Sample code to call the M365 Event Based Retention REST API**

**<span class="underline">Create Event</span>**

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>POST</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>URL</td>
<td>https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent)</td>
<td></td>
</tr>
<tr class="even">
<td>Headers</td>
<td>Content-Type</td>
<td>application/atom+xml</td>
</tr>
<tr class="odd">
<td>Body</td>
<td><p>&lt;?xml version='1.0' encoding='utf-8' standalone='yes'?&gt;</p>
<p>&lt;entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'</p>
<p>xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'</p>
<p>xmlns='http://www.w3.org/2005/Atom'&gt;</p>
<p>&lt;category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' /&gt;</p>
<p>&lt;updated&gt;9/9/2017 10:50:00 PM&lt;/updated&gt;</p>
<p>&lt;content type='application/xml'&gt;</p>
<p>&lt;m:properties&gt;</p>
<p>&lt;d:Name&gt;Employee Termination &lt;/d:Name&gt;</p>
<p>&lt;d:EventType&gt;99e0ae64-a4b8-40bb-82ed-645895610f56&lt;/d:EventType&gt;</p>
<p>&lt;d:SharePointAssetIdQuery&gt;1234&lt;/d:SharePointAssetIdQuery&gt;</p>
<p>&lt;d:EventDateTime&gt;2018-12-01T00:00:00Z &lt;/d:EventDateTime&gt;</p>
<p>&lt;/m:properties&gt;</p>
<p>&lt;/content&gt;</p>
<p>&lt;/entry&gt;</p></td>
<td></td>
</tr>
<tr class="even">
<td>Authentication</td>
<td>Basic</td>
<td></td>
</tr>
<tr class="odd">
<td>Username</td>
<td>“Complianceuser”</td>
<td></td>
</tr>
<tr class="even">
<td>Password</td>
<td>“Compliancepassword”</td>
<td></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>Parameters</strong></th>
<th><strong>Description</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>&lt;d:Name&gt;&lt;/d:Name&gt;</td>
<td>Provide a unique name for the event,</td>
<td>Cannot contain trailing spaces, and the following characters: % * \ &amp; &lt; &gt; | # ? , : ;</td>
</tr>
<tr class="even">
<td>&lt;d:EventType&gt;&lt;/d:EventType&gt;</td>
<td>Enter event type name (or Guid),</td>
<td>Example: “Employee termination”. Event type has to be associated with a retention label.</td>
</tr>
<tr class="odd">
<td>&lt;d:SharePointAssetIdQuery&gt;&lt;/d:SharePointAssetIdQuery&gt;</td>
<td>Enter “ComplianceAssetId:” + employee Id</td>
<td>Example:&quot;ComplianceAssetId:12345&quot;</td>
</tr>
<tr class="even">
<td>&lt;d:EventDateTime&gt;&lt;/d:EventDateTime&gt;</td>
<td>Event Date and Time</td>
<td><p>Format: yyyy-MM-ddTHH:mm:ssZ, Example:</p>
<p>2018-12-01T00:00:00Z</p></td>
</tr>
</tbody>
</table>

| **Response Code** | **Description**       |
| ----------------- | --------------------- |
| 302               | Redirect              |
| 201               | Created               |
| 403               | Authorization Failed  |
| 401               | Authentication Failed |

**<span class="underline">Get Events based on time range:</span>**

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>GET</th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>URL</td>
<td><ol start="4" type="1">
<li><p>https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&amp;EndDateTime=2019-01-16</p></li>
</ol></td>
<td></td>
</tr>
<tr class="even">
<td>Headers</td>
<td>Content-Type</td>
<td>application/atom+xml</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Authentication</td>
<td>Basic</td>
<td></td>
</tr>
<tr class="odd">
<td>Username</td>
<td>“Complianceuser”</td>
<td></td>
</tr>
<tr class="even">
<td>Password</td>
<td>“Compliancepassword”</td>
<td></td>
</tr>
</tbody>
</table>

| **Response Code** | **Description**                   |
| ----------------- | --------------------------------- |
| 200               | OK, A list of events in atom+ xml |
| 404               | Not found                         |
| 302               | Redirect                          |
| 401               | Authorization Failed              |
| 403               | Authentication Failed             |

**<span class="underline">Get an Event by ID:</span>**

| Method         | GET                                                                                                                                                                                                                                                                |                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------- |
| URL            | [https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent(‘174e9a86-74ff-4450-8666-7c11f7730f66’)](https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent\('174e9a86-74ff-4450-8666-7c11f7730f66'\)) |                      |
| Header         | Content-Type                                                                                                                                                                                                                                                       | application/atom+xml |
| Authentication | Basic                                                                                                                                                                                                                                                              |                      |
| Username       | “Complianceuser”                                                                                                                                                                                                                                                   |                      |
| Password       | “Compliancepassword”                                                                                                                                                                                                                                               |                      |

| **Response Code** | **Description**                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, The response body contains the event in atom+xml |
| 404               | Not found                                            |
| 302               | Redirect                                             |
| 401               | Authorization Failed                                 |
| 403               | Authentication Failed                                |

**<span class="underline">Get an Event by Name:</span>**

| Method         | GET                                                                                                                                          |                      |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- |
| URL            | <https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('EventByRESTPost-2226bfebcc2841a8968ba71f9516b763')> |                      |
| Headers        | Content-Type                                                                                                                                 | application/atom+xml |
| Authentication | Basic                                                                                                                                        |                      |
| Username       | “Complianceuser”                                                                                                                             |                      |
| Password       | “Compliancepassword”                                                                                                                         |                      |

| **Response Code** | **Description**                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, The response body contains the event in atom+xml |
| 404               | Not found                                            |
| 302               | Redirect                                             |
| 401               | Authorization Failed                                 |
| 403               | Authentication Failed                                |

**Using PowerShell (ver.6 or higher) or any HTTP client**

Step 1: Connect to PowerShell.

Step 2: run the following script.

<table>
<tbody>
<tr class="odd">
<td><p>param([string]$baseUri)</p>
<p>$userName = &quot;admin@o365ediscoverydemo.onmicrosoft.com&quot;</p>
<p>$password = &quot;EDiscoO365Demo&quot;</p>
<p>$securePassword = ConvertTo-SecureString $password -AsPlainText -Force</p>
<p>$credentials = New-Object System.Management.Automation.PSCredential($userName, $securePassword)</p>
<p>$EventName=&quot;EventByRESTPost-$(([Guid]::NewGuid()).ToString('N'))&quot;</p>
<p>Write-Host &quot;Start to create an event with name: $EventName&quot;</p>
<p>$body = &quot;&lt;?xml version='1.0' encoding='utf-8' standalone='yes'?&gt;</p>
<p>&lt;entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'</p>
<p>xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'</p>
<p>xmlns='http://www.w3.org/2005/Atom'&gt;</p>
<p>&lt;category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' /&gt;</p>
<p>&lt;updated&gt;7/14/2017 2:03:36 PM&lt;/updated&gt;</p>
<p>&lt;content type='application/xml'&gt;</p>
<p>&lt;m:properties&gt;</p>
<p>&lt;d:Name&gt;$EventName&lt;/d:Name&gt;</p>
<p>&lt;d:EventType&gt;e823b782-9a07-4e30-8091-034fc01f9347&lt;/d:EventType&gt;</p>
<p>&lt;d:SharePointAssetIdQuery&gt;'ComplianceAssetId:123'&lt;/d:SharePointAssetIdQuery&gt;</p>
<p>&lt;/m:properties&gt;</p>
<p>&lt;/content&gt;</p>
<p>&lt;/entry&gt;&quot;</p>
<p>$event = $null</p>
<p>try</p>
<p>{</p>
<p>$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri &quot;$baseUri/ComplianceRetentionEvent&quot; -ContentType &quot;application/atom+xml&quot; -Authentication Basic -Credential $credentials -MaximumRedirection 0</p>
<p>}</p>
<p>catch</p>
<p>{</p>
<p>$response = $_.Exception.Response</p>
<p>if($response.StatusCode -eq &quot;Redirect&quot;)</p>
<p>{</p>
<p>$url = $response.Headers.Location</p>
<p>Write-Host &quot;redirected to $url&quot;</p>
<p>$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri $url -ContentType &quot;application/atom+xml&quot; -Authentication Basic -Credential $credentials -MaximumRedirection 0</p>
<p>}</p>
<p>}</p>
<p>$event | fl *</p></td>
</tr>
</tbody>
</table>

Outcome in both options:

Step 1: Go to Security & Compliance Center

Step 2: Click on Events under Data Governance

Step 3: Verify Event has been created.

![cid:image001.jpg@01D4AE51.AC4230B0](c:\\Users\\stephow\\GitHub\\officedocs-o365seccomp-pr\\SecurityCompliance/media/image9.jpeg)

Similarly, the above options to automate event based retention can be used for the following scenarios as well.

## Scenario 2: Contracts Expiring

An organization can have multiple records for a single contract with customers, vendors and partners. These documents can reside in a document library like SharePoint. The ending of a contract determines the start of the retention period of the documents associated with the contract. For example: all records related to contracts need to be retained for five years from the time the contract expires. The event that triggers the five-year retention period is the expiration of the contract.

A Customer Relationship Management (CRM) system can work with Microsoft 365 and trigger retention of Contract documents

**Configuring Automated Event Based Retention for this scenario:**

  - Admin creates a SharePoint library with various folders for each contract type.

  - Admin adds contract files such as License Contracts, Development Contracts to each contract folder

  - Admin assigns Asset Id to each contract folder

  - SCC Admin logs into the Security & Compliance Center

  - SCC Admin creates contract related events types such as “Contract Creation”, “Contract Expiration” events in Security and Compliance Center.

  - SCC Admin creates “Contract Expiration” label in Security and Compliance Center.

  - This “ Contract Expiration” label is published and applied manually or automatically to the contract files in SharePoint

  - Contract Management System can work with Microsoft Flow or a similar application to run periodically to manage contract files

  - If a contract expires, Microsoft Flow will trigger the M365 Event Based Retention REST API that will begin the retention clock on the specific contract’s files.

## Scenario 3: End of Product Manufacturing

A manufacturing company that produces different lines of products creates many manufacturing specifications and pricing documents. When the product is no longer manufactured, all specifications and documents linked to this product need to be retained for a specific period after the end of the lifetime of the product.

An Enterprise Resource Planning (ERP) system can work with Microsoft 365 and Microsoft Flow to trigger retention.

**Configuring Automated Event Based Retention for this scenario:**

  - Admin creates product folders in the Document set such as Product 1, Product 2, etc.

  - Admin adds product files such as Manufacturing Specifications, Product Pricing, Product licensing to each product folder

  - Admin assigns Asset Id to each productfolder.

  - SCC Admin logs into the Security & Compliance Center

  - SCC Admin creates employee related events types such as “Start of Product Manufacturing”, “End of Product Manufacturing” events in Security and Compliance Center.

  - SCC Admin creates “End of Product Manufacturing” label in Security and Compliance Center.

  - This “ End of Product Manufacturing” label is published and applied manually or automatically to the product files in SharePoint

  - ERP Systems can work with Microsoft Flow or similar applications to run periodically to manage product files

  - If the manufacturing of a product ends, Microsoft Flow will trigger the M365 Event Based Retention REST API that will begin the retention clock on the specific product’s files.

# Appendix

**Using Redirect 302 response results to call the REST API**

1.  Invoke a POST retention event call using the REST API URL <https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent> (Global Admin permissions are required)

2.  Check the response code. If it’s 302, then get the redirected URL from Location property of the response header

3.  Invoke the POST retention event call again using the redirected URL.

#### **What is a** [REST API](https://docs.microsoft.com/en-us/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse)**?** 

Representational State Transfer (REST) APIs are service endpoints that support sets of HTTP operations (methods), which provide create/retrieve/update/delete access to the service's resources.

#### **Components of a REST API request/response**

A REST API request/response pair can be separated into 5 components:

1.  > The **request URI**, which consists of: {URI-scheme} :// {URI-host} / {resource-path} ? {query-string}. Note that we are calling this out separately here, as most languages/frameworks require you to pass this separately from the request message, but it's actually included in the request message header.
    
      - > URI scheme: indicates the protocol used to transmit the request. For example, http or https.
    
      - > URI host: the domain name or IP address of the server where the REST service endpoint is hosted, such as graph.microsoft.com
    
      - > Resource path: specifies the resource or resource collection, which may include multiple segments used by the service in determining the selection of those resources. For example: beta/applications/00003f25-7e1f-4278-9488-efc7bac53c4a/owners could be used to query the list of owners of a specific application within the applications collection.
    
      - > Query string (optional): used to provide additional simple parameters, such as the API version, resource selection criteria, etc.

<!-- end list -->

1.  > HTTP **request message header** fields
    
      - > A required [HTTP method](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (also known as an operation or verb), which tell the service what type of operation you are requesting. Azure REST APIs support GET, HEAD, PUT, POST, and PATCH methods.
    
      - > Optional additional header fields as required by the specified URI and HTTP method. For example, an Authorization header that provides a bearer token containing client authorization information for the request.

2.  > Optional HTTP **request message body** fields, to support the URI and HTTP operation. For example, POST operations contain MIME-encoded objects passed as complex parameters. The MIME encoding type for the body should be specified in the Content-type request header as well, for POST/PUT operations. Note that some services require you to use a specific MIME type, such as application/json.

3.  > HTTP **response message header** fields
    
      - > An [HTTP status code](http://www.w3.org/Protocols/HTTP/HTRESP.html), ranging from 2xx success codes to 4xx/5xx error codes. Alternatively, a service-defined status code may be returned, as indicated in the API documentation.
    
      - > Optional additional header fields as required to support the request's response, such as a Content-type response header.

4.  > Optional HTTP **response message body** fields
    
      - > MIME-encoded response objects may be returned in the HTTP response body, such as a response from a GET method that is returning data. Typically these will be returned in a structured format as JSON or XML, as indicated by the Content-type response header. For example, when requesting an access token from Azure AD, it will be returned in the response body as the access\_token element, one of several name/value paired objects in a data collection. In this example, a response header of Content-Type: application/json will also be included.
