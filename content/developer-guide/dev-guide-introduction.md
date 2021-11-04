---
uid: lp-dev-guide
--- 

# Developer guide

Aveva&trade; Data Hub is a database platform as a service (dbPaaS) designed for storing, retrieving, and analyzing real-time operations data. With Aveva&trade; Data Hub, people in and out of your organization have flexible and secure access operations data. Operations data can be collected from within a primary control network to the edge of the industrial network. Use OCS to add context to time-based operations data, to enable process engineers and systems operators to make decisions and take corrective or preemptive actions. From data collection to data access to data delivery, Aveva&trade; Data Hub provides flexibility and control with its REST API. 

Use the information in this section to programmatically access Aveva&trade; Data Hub.

**Note:** Aveva&trade; Data Hub strives to align with security best practices. Aveva&trade; Data Hub Cross-site Scripting (XSS) protections align with the [Open Web Application Security Project (OWASP) XSS Cheatsheet rule 3.1](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html#rule-31-html-encode-json-values-in-an-html-context-and-read-the-data-with-jsonparse) to ensure returned `Content-type` header is `application/json`, not `text/html`, for defense against XSS attacks in JSON responses.

## Access to Aveva&trade; Data Hub

You must have an account to use Aveva&trade; Data Hub. Go to the [Aveva&trade; Data Hub page at ](https://www.osisoft.com/pi-system/pi-cloud/osisoft-cloud-services), click [Contact Us](https://www.osisoft.com/contact) and request an account.
