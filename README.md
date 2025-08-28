# Please credit Mohammad Ahsan Hummayoun when using, sharing, or adapting this workflow

This n8n workflow automates the generation of a Sales Pipeline Summary for your e-commerce business. It's designed to provide sales managers with a quick and clear overview of in-progress deals.

The problem this workflow solves is the manual and time-consuming process of gathering and summarizing sales data, which can lead to delayed insights and missed opportunities.

This solution fetches all "in progress" deals from a CRM (HubSpot is used as an example), calculates key metrics, and identifies top deals. It then compiles this information into a professional HTML email, complete with a chart and a concise summary, and sends it directly to the manager. This workflow can be easily scheduled to run at regular intervals, ensuring managers always have up-to-date information.


**How it Works**


The core of this workflow is a Code node that processes the fetched deal data. Here's a breakdown of its logic:

**Data Extraction & Formatting:** Deals are retrieved from the CRM (e.g., HubSpot) and key properties like deal name, amount, close date, and pipeline are extracted. Dates are converted from milliseconds to a readable YYYY-MM-DD format.

**Filtering & Sorting:** Only deals with an amount greater than zero are considered, and they are then sorted by amount in descending order. The top 10 deals are selected for detailed reporting.

**Chart Preparation:** The processed deal names and amounts are prepared for a bar chart. Deal names longer than 20 characters are truncated to maintain readability on the chart.

**Chart Generation:** A bar chart visualizing the top deals is generated using the QuickChart API. The chartConfig object defines the chart's appearance and data.

**Summary Statistics:** Key performance indicators (KPIs) such as total deal value, deal count, and average deal size are calculated.

**HTML Email Content:** HTML table rows are dynamically generated to present the deal details in a structured format within the email.

**Output:** The workflow outputs the chart URL, processed deal data, HTML for the email table, and summary statistics, which are then used by a "Send Email" node.



**Setup and Requirements**



To run this n8n workflow, you will need the following:

**CRM Integration:** An n8n node configured to connect to your CRM (e.g., HubSpot) to fetch deal data.

**Email Sending Node:** An n8n node configured to send emails (e.g., using Gmail SMTP or another email service).

**API Keys:** While QuickChart doesn't require an API key, your CRM and email service will. These API keys are typically configured directly within the respective n8n nodes for security.
