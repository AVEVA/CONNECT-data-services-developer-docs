---
uid: gsConnections
---

# Get started with connections

There are two types of connections you can use to transfer data from external sources into AVEVA Data Hub:

- The PI to Data Hub Agent sends PI point data from an on-premises PI Data Archive server to a namespace. See [Get started with PI to Data Hub connections](xref:gsPItoOCS).

- Open Message Format (OMF) enables OMF applications to send data to a namespace. See [Get started with OMF connections](xref:gsOMF).

## PI System counterpart

<!-- I renamed this section PI System rather than PI Server because the second paragraph referred to "PI System connections." Please verify  --> <!-- VT: In response to previous comment, the change to "PI System" is correct.-->

Connections do not have a direct equivalent in the PI System, but they are similar to PI trusts used with PI Data Archive, because both are required for an application that writes data to the PI System.

PI to Data Hub Agent uses PI System connections that behave much like a PI-to-PI interface, in that they send PI data from one system to another.
