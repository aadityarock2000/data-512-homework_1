# DATA512 Human Centered Data Science

## Homework 1
Author - Aaditya Parthasarathy

### Goal 

The objective of this project is to develop a Python script capable of reliably fetching and examining pageviews data from the Wikimedia API for a specified set of Wikipedia articles from July 1, 2015 through September 30, 2023. The outputs would be graphical analysis of 3 questions laid out:

1. **Maximum Average and Minimum Average** - Time series for the articles that have the highest average monthly page requests and the lowest average monthly page requests for desktop access and mobile access.
2. **Top 10 Peak Page Views** - Time series for the top 10 article pages by largest (peak) page views over the entire time by access type. [You first find the month for each article that contains the highest (peak) page views, and then order the articles by these peak values]
3. **Fewest Months of Data** - Depiction of pages that have the fewest months of available data, which would mostly contain a set of the most recent academy award winners. [Limited to the bottom 10].

### Data Sources and Licenses:

The Jupyter notebook has some parts from the example that was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 14, 2023.


#### API
The data for this project is sourced from the Wikimedia API, which provides access to a wide range of information related to Wikipedia articles and their pageviews. Here are the links to the API documentation that is used to fetch the data.
- [Pageviews API documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews)
- [Pageviews API endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)
- **License:**[Wikimedia Terms of use](https://www.mediawiki.org/wiki/API:REST_API#Terms_and_conditions)

#### Inputs

Here is the data source that is used as the base to generate the data, which consists of names and the website addresses of academy award winning movies.  [Articles about academy award winning movies](https://docs.google.com/spreadsheets/d/1A1h_7KAo7KXaVxdScJmIVPTvjb3IuY9oZhNV4ZHxrxw/edit?usp=sharing)

#### Outputs

##### JSON Files
- **academy_monthly_mobile_201507-202309.json**: This JSON file contains monthly data on pageviews for Wikipedia articles accessed via mobile devices, including both mobile web and mobile app views.
   - **Attributes:**
     - `name`: The title of the Wikipedia article.
     - `timestamp`: The timestamp indicating the month and year of the data (e.g., "202301" for January 2023).
     - `views`: The count of pageviews for the article during that specific month.

- **academy_monthly_desktop_201507-202309.json**: In this JSON file, you'll find monthly pageviews data for Wikipedia articles accessed via desktop devices.
   - **Attributes:**
     - `name`: The title of the Wikipedia article.
     - `timestamp`: The timestamp denoting the month and year of the data (e.g., "202301" for January 2023).
     - `views`: The quantity of pageviews for the article during that particular month.
     %% - Additional fields such as `project` (source), `granularity` (monthly, yearly, etc.), `access` (desktop, mobile, etc.), and `agent` (user, etc.) are also provided. %%

- **academy_monthly_cumulative_201507-202309.json**: This JSON file encompasses monthly cumulative pageviews data for Wikipedia articles, representing the combined total of mobile and desktop views.
   - **Attributes:**
     - `name`: The title of the Wikipedia article.
     - `timestamp`: The timestamp representing the month and year of the data (e.g., "202301" for January 2023).
     - `views`: The overall cumulative pageviews (including both mobile and desktop) for the article during that specific month.
##### Image files
- **Max-Min-Avg.png**: This PNG image displays a graph illustrating the monthly page views of the most and least viewed articles across both mobile and desktop platforms.

- **PeakPageViews.png**: This PNG image presents a graph depicting the monthly page views of the top 10 articles with the highest peak monthly views.

- **FewestMonths.png**: This PNG image exhibits a graph showcasing the monthly page views of the top 10 articles with the shortest available data spans.

### Issues and Special Considerations:
1. This takes a long time to run, as it has to make over 1350 \* 3 calls to collect all the data required. Rate limiting factors must be kept in mind to avoid being blocked for overuse.
2. Some of the date entries, like in the file names and in the templated code are hard coded.
