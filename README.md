# Adding Category and Reference Values for Incident Routing

## Overview
This repository demonstrates how to extend Incident categorization and routing in ServiceNow by adding dependent Category and Subcategory values, creating Service and Service Offering records, and enabling automatic assignment of Incidents based on Service configuration.

This project builds on previous configuration work by tying categorization, services, and support groups together to support accurate routing and auto-assignment of Incidents.

## Use Case
An organization needs to identify and track firmware-related Incidents for a specific hardware product line. To support this, new Subcategory values must be added, Services and Service Offerings must be defined, and Support Groups must be configured to allow automatic Incident assignment.

This walkthrough simulates how a ServiceNow administrator configures Incident data relationships to improve routing accuracy and reduce manual assignment effort.

## Features
- Dependent Category and Subcategory configuration
- Reference table record creation
- Business Service and Service Offering setup
- Support Group configuration
- Automatic Incident assignment validation

## Technologies Used
- ServiceNow Platform
- Incident Management
- Service Portfolio Management
- Configuration Management Database (CMDB)
- User and Group Management

## Implementation Walkthrough

### Objective
Enhance Incident routing accuracy by extending categorization options, defining Services and Service Offerings, associating Support Groups, and validating automatic assignment behavior.

### Step 1: Add Firmware as a Dependent Subcategory
A new Subcategory value named **Firmware** was added as a dependent option under the **Hardware** Category on the Incident table.

This change allowed firmware-related hardware issues to be classified separately from other hardware Incidents, improving reporting clarity and routing accuracy.

The new Subcategory was positioned appropriately within the Hardware list to maintain logical ordering and usability.
<br/> 
<br/>
<img width="1888" height="598" alt="Screen Shot 2026-01-29 at 8 01 49 PM" src="https://github.com/user-attachments/assets/25c3fb82-0136-4497-89a6-9b7f3ada275b" />

<img width="1888" height="598" alt="Screen Shot 2026-01-29 at 8 03 10 PM" src="https://github.com/user-attachments/assets/856b974a-1847-4da9-a341-e9302716282e" />

### Step 2: Create the Training Business Service
A new Business Service named **Training** was created to represent training-related hardware functionality used in production environments.

The Service was configured with ownership, operational status, service classification, and approval group values to support downstream Incident tracking and governance.

This Service served as the parent for HHD-related Service Offerings.

<img width="1888" height="478" alt="Screen Shot 2026-01-29 at 8 20 37 PM" src="https://github.com/user-attachments/assets/e73412b4-f06a-4494-8a82-2e64bb7760bc" />

### Step 3: Create the Infinity (HHD) Service Offering
A Service Offering named **Infinity (HHD)** was created under the Training Business Service.

The Offering was configured with production usage, operational status, business criticality, approval group, and descriptive metadata specific to the HHD product line.

This established a structured relationship between Incidents and the HHD service context.

<img width="1888" height="625" alt="Screen Shot 2026-01-29 at 8 25 13 PM" src="https://github.com/user-attachments/assets/2f740c8a-2c02-4461-b7d1-324fae804322" />

### Step 4: Create the Training Technology Support Group
A new Support Group named **Training Technology Support** was created to handle firmware-related HHD Incidents.

Team members were added to the group, and the **ITIL** role was assigned to enable Incident ownership and workflow actions.

This group was designated as the primary routing destination for HHD-related Incidents.

<img width="1888" height="765" alt="Screen Shot 2026-01-29 at 8 32 12 PM" src="https://github.com/user-attachments/assets/ce50d2e3-8138-42da-af4f-916851c9e085" />

<img width="1603" height="250" alt="Screen Shot 2026-01-29 at 8 32 37 PM" src="https://github.com/user-attachments/assets/244ce254-2cc2-46f0-b3b1-9b8d2433631d" />

### Step 5: Associate Support Groups to Services
The Training Business Service and Infinity (HHD) Service Offering were updated to reference **Training Technology Support** as both the Support Group and Change Group.

This configuration enabled baseline Service-based auto-assignment behavior without requiring custom assignment rules.

<img width="1910" height="483" alt="Screen Shot 2026-01-29 at 8 36 51 PM" src="https://github.com/user-attachments/assets/30ff5d48-3123-423e-be1f-1522e461e240" />

<img width="1910" height="551" alt="Screen Shot 2026-01-29 at 8 39 17 PM" src="https://github.com/user-attachments/assets/cbe000d6-69a9-4765-843b-762e356d090a" />

### Step 6: Validate Automatic Assignment
An Incident was created using the HHD view to validate routing behavior.

The Incident was categorized as **Hardware** with the **Firmware** Subcategory and associated with the **Training** Service and **Infinity (HHD)** Service Offering.

Upon saving the record, the Assignment Group was automatically populated with **Training Technology Support**, confirming that Service-based auto-assignment was functioning as expected.

<img width="1910" height="520" alt="Screen Shot 2026-01-29 at 8 43 06 PM" src="https://github.com/user-attachments/assets/93ba1e72-44a2-455e-b050-4e79eb8a5b90" />

<img width="1910" height="292" alt="Screen Shot 2026-01-29 at 8 44 27 PM" src="https://github.com/user-attachments/assets/16144308-b904-4fef-880c-02f959998780" />

## Lessons Learned
- Dependent Subcategories improve Incident classification and reporting
- Services and Service Offerings enable structured Incident routing
- Support Group associations directly influence automatic assignment
- Proper reference data configuration reduces manual routing effort
- Validating configuration through Incident creation confirms real-world behavior
