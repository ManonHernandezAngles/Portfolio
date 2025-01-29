## Quantium Job Simulation - Data Analytics and Commercial Insights
### Project overview
In this job simulation, I was part of Quantium’s retail analytics team, working closely with the Category Manager for Chips. The goal was to better understand customer purchasing behavior and assess the impact of a new trial store layout. You can find the complete job simulation and datasets [here](https://www.theforage.com/simulations/quantium/data-analytics-rqkb).
### Objectives
The insights from the analysis will contribute to the supermarket’s strategic plan for the chip category over the next six months.
### Methodology
For this analysis, I utilized RStudio for coding and data visualization. The data was already collected. I used PowerPoint for constructing the final presentation.
### Dataset
I worked with two CSV datasets:
* **Transaction Dataset**: This included card number, date, store number, product number, product name, quantity, and total sales.
* **Purchase Behavior Dataset**: This included card number, lifestage (customer attribute identifying family status and life stage), and premium customer status (segmentation based on price sensitivity and product preferences).
### Data Preparation
[The code of the data preparation and the first part of data analysis is available here](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Task%202%20code.pdf)

I began by cleaning the datasets:
* Checked data formats and corrected them.
* Identified and removed outliers.
* Managed missing data, finding that missing entries were only on days when the store was closed.
* Cleaned the data related to snack brands.
* Merged the two files using card number data.
### Analysis
#### Initial Insights
* **Seasonal Trends**: Purchases increased in December, peaking just before Christmas.
  ![Transaction over time](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Image/Transaction%20over%20time.png)
* **Customer Segments**: Sales were mainly driven by Budget - older families, Mainstream - young singles/couples, and Mainstream - retirees.
* **Purchasing Behavior**: Older families and young families purchased more chips per customer. Mainstream mid-age and young singles/couples were willing to pay more per packet of chips compared to their Budget and Premium counterparts.
  ![Number of customer by lifestage and premium status](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Image/Number%20of%20customer.png)
* **Statistical Analysis**: A t-test confirmed that the unit price for mainstream young and mid-age singles and couples was significantly higher than for budget or premium singles and couples.
  ![Average price per unit](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Image/Average%20price%20per%20unit.png)
#### Deep Dive into Specific Customer Segments
I analyzed trends in the mainstream young singles/couples segment and found:
* 23% more likely to purchase Tyrells chips compared to the rest of the population.
* 22% more likely to purchase Twisties chips.
* 56% less likely to purchase Burger Rings.
* 27% more likely to purchase 270g packs of chips (notably, Twisties offers 270g packs).
#### Impact of the New Trial
[The code of this part of the analysis is available here](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Task%201%20code%20portfolio.pdf)

The trial was implemented in stores 77, 86, and 88 during February 2019 to April 2019. I selected control stores based on similarities in monthly total sales and number of customers.
![Control store by total sales by mont](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Image/Control%20store%2077.png)
* **Store 77**: Control store 233. T-tests indicated a significant increase in sales during the trial period.
  ![Evolution on the trial store 77](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Image/Sales%20evolution%20during%20trial%20period.png)
* **Store 86**: Control store 155. Number of customers increased significantly, but sales did not show a significant difference.
* **Store 88**: Control store 237. Both sales and customer numbers showed significant increases.
### Presentation for the Category Manager
[Presentation available here](https://github.com/ManonHernandezAngles/Portfolio/blob/main/Quantium_Job_Simulation/Quantium%20presentation.pdf)
### Conclusions
Sales were driven mainly by Budget - older families, Mainstream - young singles/couples, and Mainstream - retirees. Mainstream young singles/couples were more likely to make impulse purchases and pay more per packet. The Category Manager could increase performance by strategically placing Tyrrells and smaller packs of chips in areas frequented by young singles and couples.
Control stores 233, 155, and 237 were identified for trial stores 77, 86, and 88, respectively. Results indicated significant sales increases in stores 77 and 88, with store 86 showing increased customer numbers but not sales. Further investigation into the implementation differences in store 86 is suggested.
