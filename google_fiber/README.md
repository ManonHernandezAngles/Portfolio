## Google Fiber Project : Business Intelligence Project
### Introduction
This project serves as the capstone project of the Google Business Intelligence certificate. Throughout this project I will follow the steps of BI work. The final deliverables will include a reporting dashboard and an executive summary.  
### Project Background
This project is set in a scenario in which I am interviewing for a position with Google Fiber, a branch of Google that provides people and business with fiber optic internet. The Fiber customer service team has asked me to design a dashboard using fictional data, following the entire BI process. The goal is to enhance their service by reducing the call volume through increased customer satisfaction and improved operational efficiency. The dashboard should reflect an understanding of this goal and provide your stakeholders with insights about repeat caller volumes in three markets and the types of problems they represent.  
### Capture
#### Stakeholder requirements document
In this document I outline the business problem for this project: helping the customer service team to improve their service. The problem is defined as : How often does the customer service team receive repeat calls form customers?  
After identifying the stakeholders' names and positions in the services, we aim to understand their usage details. The customer team wants to understand how effectively the customer service can answer customer questions the first time and resolve problems. They need insights into the types of customer issues that seem to generate more repeat calls and explore trends in three different market cities with different problem.  
We set the primary requirements as :  
* A chart or table measuring repeat calls by their first contact date
* A chart or table exploring repeat calls by market and problem type
* Charts showcasing repeat calls by week, month, and quarter
* Explore repeat caller trends in the three different market cities
* Provide insights into the types of customer issues that seem to generate more repeat call
* Understand how often customers are calling customer support after their first inquiry
* Desing charts with view by week, month, quarter and year
#### Project requirement document
After recalling the purpose of the project and detailing its major elements, including the team and expected deliverables. Then we list the stakeholders’ requirements and prioritize them.  
*	A chart or table measuring repeat calls by their first contact date. Required  
*	A chart or table exploring repeat calls by market and problem type. Required  
*	Charts showcasing repeat calls by week, month, and quarter. Desired  
*	Explore repeat caller trends in the three different market cities. Required  
*	Provide insights into the types of customer issues that seem to generate more repeat call Desired  
*	Understand how often customers are calling customer support after their first inquiry Desired  
*	Desing charts with view by week, month, quarter and year Required  
Later we set the success criteria using the SMART method.
**Specific** : BI insight must clearly indentify the specific characteristics of repeat calls.
**Measurable** : Each call should be evaluated frequency and volume. For example, What problem types generate the most repeat calls? Whiwh market city’s ccustomer service team receives the most repeat calls? Does this vary by time?
**Action-oriented** : These outcomes must quantify the number of repat callers depend of circustancies. The the Google Fiber customer service team could use this knowledge to improve their customer service and reduce the number of calls and repeated calls.
**Relevant** : All metrics must support the primary question: How often does the customer service team receive repeat calls from customers?
**Time-Bound** : Analyze data that spans at least one year because we need to see the evolution and the stakeholders need information by year, quarter, month and weak.
Additionally, we explain the actual user journeys and the ideal future experience.
For the assumptions we set : To anonymize and fictionalize the data, the datasets the columns market_1, market_2, and market_3 to indicate three different city service areas the data represents.
The data also lists five problem types :
*	Type_1 is account management  
*	Type_2 is technician troubleshooting  
*	Type_3 is scheduling  
*	Type_4 is construction  
*	Type_5 is internet and wifi  
Additionally, the dataset also records repeat calls over seven day periods. The initial contact date is listed as contacts_n. The other call columns are then contacts_n_number of days since first call. For example, contacts_n_6 indicates six days since first contact.  Then we detail the compliance and privacy, and the accassibility contraints and the roll-out plan.
#### Strategy document
In this document we outline the strategy, starting with the identification of primary and secondary dataset and the user requirements. Next, we define the dashboard functionalities, including references, access, scope, data filters and granularity. Following this, we detail each metrics and charts needed and we create a mock-up of the final dashboard.  
### Analyze
#### Data
We begin by combining the three datasets of the three markets into one using BigQuery’s SQL queries. Next, we download the dataset in csv format to work with it in Tableau for data visualization. This fictional data represents the Google fiber’s customer service operations from the first quarter of 2022. The columns are organized as follows :  
![Table_column](https://github.com/user-attachments/assets/d444b758-e2d7-4aff-aec3-250fba83292d)  
#### Insights
*	The number of first call are stable except during the third week of March  
*	The number of repeat call are stable during the period  
![Proportion_of_repeat_call_by_week](https://github.com/user-attachments/assets/79d000ce-1639-4509-aa9a-6c968bc740fb)
*	The market 1 have lot of repeat call (11,511)  
*	The market 2 have almost no repeat call (73)  
*	The market 3 have repeat call (4,503)  
![Number_of_call_by_market](https://github.com/user-attachments/assets/981d5eef-7b66-4eae-82cf-aade2bb07842)  
*	The problem types who generate the most repeat call is WiFi and internet and technician troubleshooting  
*	It’s also the problem types who generate the most first call  
![Number_of_repeat_call_by_market_and_type](https://github.com/user-attachments/assets/a5e9fd4c-c38d-42e0-b3a8-44d33a0ee177)
### Monitor
#### Dashboard
Visualize the entire dashboard with all functionality and filters : https://public.tableau.com/views/GooglefiberDashboard/Story1?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link  
![Dashboard_part_1](https://github.com/user-attachments/assets/32a13572-d9b8-4b0b-be63-075f4916cb28)  
#### Executive summary
[Available here](https://github.com/LaRaison18/portfolio/blob/cded235f32334b997581ad38f2dd80e3b578d149/google_fiber/Google-fiber-project-executive-summary.pdf)

#### Presentation
[Available here](https://github.com/LaRaison18/Portfolio/blob/cded235f32334b997581ad38f2dd80e3b578d149/google_fiber/Google_fiber_presentation.pdf)
 
