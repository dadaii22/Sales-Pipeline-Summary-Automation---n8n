# Please credit Mohammad Ahsan Hummayoun when using, sharing, or adapting this workflow

This n8n workflow automates the generation of a **Sales Pipeline Summary** for your e-commerce business.  
It provides sales managers with a quick and clear overview of in-progress deals, eliminating the manual, time-consuming process of gathering and summarizing sales data.  
By delivering insights automatically, it helps reduce delays and prevents missed opportunities.

The workflow fetches all "in progress" deals from a CRM (HubSpot is used as an example), calculates key metrics, and identifies top deals.  
It then compiles this information into a professional HTML email, complete with a chart and summary, and sends it directly to the manager.  
The workflow can be scheduled to run at regular intervals, ensuring managers always have up-to-date information.

# ⚙️ How it Works

**Data Extraction & Formatting**  
Deals are retrieved from the CRM (e.g., HubSpot). Key properties such as deal name, amount, close date, and pipeline are extracted, with dates converted to a readable `YYYY-MM-DD` format.  

**Filtering & Sorting**  
Only deals with an amount greater than zero are considered. These are sorted in descending order by deal size, and the top 10 deals are selected for detailed reporting.  

**Chart Preparation**  
Deal names and amounts are formatted for a bar chart. Deal names longer than 20 characters are truncated for readability.  

**Chart Generation**  
A bar chart visualizing the top deals is created using the **QuickChart API**, with chart appearance and data defined via a `chartConfig` object.  

**Summary Statistics**  
Key metrics are calculated, including:  
- Total deal value  
- Deal count  
- Average deal size  

**HTML Email Content**  
Dynamic HTML table rows are generated to present deal details in a structured format inside the email.  

**Output**  
The workflow outputs the chart URL, processed deal data, the email HTML table, and KPIs — all of which are passed to a "Send Email" node.  

# 🚀 Setup and Requirements

**CRM Integration**  
An n8n node configured to connect to your CRM (e.g., HubSpot) to fetch deal data.  

**Email Sending Node**  
An n8n node configured to send emails (e.g., Gmail SMTP or another email service).  

**API Keys**  
- QuickChart (no key required)  
- CRM (e.g., HubSpot API key)  
- Email service credentials (e.g., Gmail App Password)  

API keys and credentials should be configured securely within their respective n8n nodes.
