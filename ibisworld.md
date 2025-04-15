IBISWorld offers a comprehensive Web Application Programming Interface (API) designed to provide seamless access to its extensive repository of industry, company, and procurement research. This API facilitates the integration of IBISWorld’s up-to-date insights into various enterprise systems, including knowledge hubs, Customer Relationship Management (CRM) platforms, intranets, and industry portals. Such integration ensures that organizations have immediate access to critical data, enhancing informed decision-making and strategic planning. ￼ ￼

Data Offerings:

The API grants access to a wide array of data points across IBISWorld’s Industry and Procurement products for regions such as Australia, the United States, Canada, China, the United Kingdom, and New Zealand. Depending on subscription levels, users can retrieve either full reports or specific sections. The available data encompasses various attributes, including: ￼
	•	Market Size and Growth Rates: ￼
	•	Competitive Landscape and Key Players: ￼
	•	Financial Performance Metrics: ￼
	•	Supply Chain Information: ￼
	•	Regulatory Environment: ￼
	•	Industry Trends and Risk Assessments: ￼
	•	Consumer Demographics: ￼
	•	Technological Advancements and Sustainability Metrics:

This breadth of information ensures that users receive a holistic view of industry dynamics, crucial for various applications such as market analysis, investment decisions, and risk evaluations.

Interacting with the API:

To utilize the IBISWorld API, users must have an active IBISWorld account with the appropriate access permissions. It’s advisable to set up a dedicated user account specifically for API interactions. For account creation or verification, contacting your Client Relationship Manager or reaching out directly to IBISWorld is recommended.

Authentication:

The API employs token-based authentication to ensure secure data access. Users need to obtain an access token by providing their API credentials, which must be included in the header of each API request.

Endpoints and Data Retrieval:

IBISWorld’s API is structured to offer both full report access and granular data retrieval. Users can request entire Industry or Procurement reports or focus on specific sections. For example, to obtain the full industry report, the endpoint would be: ￼

https://api.ibisworld.com/industry/v3/fullreport

Detailed information on all available endpoints, including their structures and parameters, is provided in the API’s Data Dictionary. This resource outlines string values for sections, data types, and descriptions for all returned classes and fields, aiding developers in seamless integration.

Request Limits and Data Size:

The API enforces specific rate limits to ensure optimal performance:
	•	10 calls per second ￼
	•	100 calls per minute ￼
	•	5,000 calls per hour ￼

While caching of results is permitted, frequent refreshes are recommended due to regular report updates. To assist with this, the “UpdatedReports” endpoint provides a list of all reports updated within specified date ranges. ￼

Regarding data size, the initial download for all combined Industry reports is approximately 1.5GB, and all Risk reports total about 0.4GB. A single Industry report can be up to 700KB when retrieved via the full report API. ￼

Versioning:

The API is currently on version 3 (v3), with a sequential numbering system reflecting the order of releases. Minor updates increment the version by 0.1, while major releases advance to the next whole number. Including the version in the endpoint URL is mandatory to ensure compatibility and access to the correct functionalities. For instance: ￼

https://api.ibisworld.com/industry/v3/fullreport

IBISWorld continues to support previous API versions to ensure ongoing functionality for clients who have built applications using earlier versions. However, migrating to newer versions is encouraged to access the latest features and improvements. ￼

In summary, IBISWorld’s API offers a robust and flexible solution for integrating comprehensive industry research into various enterprise systems, thereby enhancing efficiency and supporting data-driven decision-making. ￼

IBISWorld's API offers the flexibility to retrieve granular data, allowing users to access specific sections or data points within industry and procurement reports. This targeted approach enables organizations to integrate precise information into their systems, enhancing various business functions.

  

Granular Data Retrieval:

  

Instead of downloading entire reports, users can request individual sections or specific data points. The API's Data Dictionary provides comprehensive details on all string values for sections that can be used as body parameters, along with data types and descriptions for all returned classes and fields.

  

Practical Applications:

1. Customer Relationship Management (CRM) Systems: Sales teams can enrich CRM platforms with up-to-date industry insights, enabling personalized interactions with clients and prospects.

2. Enterprise Resource Planning (ERP) Systems: Integrating specific industry data into ERP systems aids in strategic planning and resource allocation by providing insights into market trends and financial benchmarks.

3. Credit Risk Assessment: Financial institutions can incorporate industry risk ratings and financial ratios into their credit risk models, improving the accuracy of loan assessments.

4. Market Analysis Tools: Marketing teams can access detailed industry segmentation data to identify target markets and tailor strategies accordingly.

  

Implementation Considerations:

- Authentication: Secure access is maintained through token-based authentication, requiring valid API credentials for each request.
- Rate Limits: The API enforces limits of 10 calls per second, 100 calls per minute, and 5,000 calls per hour to ensure optimal performance.
- Data Updates: Regular updates to reports necessitate frequent data refreshes. The "UpdatedReports" endpoint assists in identifying recently modified reports.

  

By leveraging granular data retrieval through IBISWorld's API, organizations can enhance decision-making processes, streamline operations, and maintain a competitive edge in their respective industries.

IBISWorld's API allows for granular data retrieval, enabling users to access specific sections of industry and procurement reports rather than downloading entire documents. This targeted approach facilitates efficient data integration into various applications and systems.

  

Available Data Sections:

  

The API provides access to a variety of report sections, including but not limited to:

- Industry Overview: General information about the industry, its definition, and primary activities.
- Market Characteristics: Details on market size, segmentation, and customer demographics.
- Competitive Landscape: Information on major players, market shares, and competitive dynamics.
- Financial Performance: Key financial metrics and benchmarks within the industry.
- Risk Ratings: Assessments of potential risks and challenges faced by the industry.

  

For a comprehensive list of all available sections and their corresponding identifiers, users should refer to the API's Data Dictionary. This resource provides detailed information on string values for sections, data types, and descriptions of all returned classes and fields.

  

Utilizing Granular Data Retrieval:

  

To retrieve specific sections, users need to include the desired section identifiers in their API requests. This approach allows for the extraction of only pertinent data, optimizing bandwidth and processing efficiency.

  

Implementation Considerations:

- Authentication: Access requires a valid IBISWorld account with API permissions. Authentication is managed via OAuth 2.0 protocol.
- Request Limits: The API enforces limits of 10 calls per second, 100 calls per minute, and 5,000 calls per hour.
- Data Updates: Reports are updated regularly. The "UpdatedReports" endpoint can be used to identify recently modified reports.

  

By leveraging granular data retrieval, organizations can seamlessly integrate precise industry insights into their systems, enhancing decision-making processes and operational efficiency.

IBISWorld's API enables granular data retrieval, allowing users to access specific sections or data points within industry and procurement reports. This targeted approach facilitates efficient integration of relevant information into various applications and systems.

  

### Examples of Data Available by Section

  

Below are examples of the types of data that can be retrieved for each section:

  

#### 1.

#### Industry Overview

- Industry Definition: A concise description outlining the scope and activities of the industry.
- Primary Activities: A list of main functions or services provided by businesses within the industry.
- Similar Industries: References to related industries for comparative analysis.

  

#### 2.

#### Market Characteristics

- Market Size: Current and historical revenue figures, often segmented by year.
- Growth Rates: Annual percentage growth, with projections for future periods.
- Number of Businesses: Data on the total number of active businesses within the industry. 

  

#### 3.

#### Competitive Landscape

- Major Players: Profiles of leading companies, including market share percentages.
- Market Concentration: Analysis of how market share is distributed among top firms.
- Barriers to Entry: Information on factors that may impede new entrants.

  

#### 4.

#### Financial Performance

- Revenue and Profit Margins: Detailed financial metrics over a multi-year period.
- Cost Structure Benchmarks: Breakdown of expenses such as wages, rent, and utilities.
- Financial Ratios: Key ratios like current ratio, debt to equity, and return on assets.

  

#### 5.

#### Risk Ratings

- Industry Risk Score: A numerical rating indicating the level of risk associated with the industry.
- Risk Factors: Identification of elements contributing to the risk assessment, such as regulatory changes or market volatility.

  

#### 6.

#### Supply Chain Information

- Key Suppliers and Buyers: Details on upstream suppliers and downstream buyers.
- Supply Chain Dynamics: Insights into the relationships and dependencies within the supply chain.

  

#### 7.

#### Regulatory Environment

- Regulations and Policies: Overview of laws and regulations impacting the industry.
- Compliance Requirements: Information on necessary certifications or standards.

  

#### 8.

#### Industry Trends and Risk Assessments

- Emerging Trends: Analysis of new developments affecting the industry.
- Risk Assessments: Evaluations of potential threats and their implications.

  

#### 9.

#### Consumer Demographics

- Customer Segmentation: Breakdown of the customer base by demographics such as age, income, and location.
- Buying Behaviors: Insights into purchasing patterns and preferences.

  

#### 10.

#### Technological Advancements and Sustainability Metrics

- Technological Innovations: Information on new technologies being adopted within the industry.
- Sustainability Practices: Data on environmental initiatives and compliance with sustainability standards.

The IBISWorld API is a RESTful API.

  

Here's a breakdown of what that means and how it applies to IBISWorld's API specifically:

* * *

### 1. Architecture: RESTful

  

The IBISWorld API conforms to REST (Representational State Transfer) principles. This is evidenced by:

- Resource-Oriented URLs:

Example:
    
    
    https://api.ibisworld.com/industry/v3/fullreport

-   
- Stateless Requests:

Each API call is self-contained and does not rely on server-side sessions.

- Standard HTTP Methods:

    - GET: Retrieve data (e.g., industry reports or metadata)

    - POST: Used for token-based authentication to get an access token

    - No mention of PUT or DELETE, which are less commonly used in read-focused data APIs
* * *

### 2. Data Format: JSON

  

All responses are in JSON format, which is a standard for modern REST APIs. This makes integration straightforward in web, mobile, or data processing environments.

  

Example of a partial JSON response:
    
    
    {
      "industryId": "44111",
      "title": "Automobile Dealers in the US",
      "marketSize": {
        "currentRevenue": 1150000000000,
        "growthRate": 0.03
      },
      ...
    }

  

* * *

### 3. Authentication: OAuth 2.0 (Token-Based)

- You must authenticate using a token retrieved via a POST request to the /token endpoint.
- The token must be included in the Authorization header in the form:
    
    
    Authorization: Bearer YOUR_TOKEN

  

* * *

### 4. Versioned Endpoints

- Example: v3 in https://api.ibisworld.com/industry/v3/fullreport
- Indicates a REST API that uses versioning in the URI path, allowing backward compatibility and safe iteration.
* * *

### 5. Summary:

| 

Feature

 | 

Details

 | 
| ---- | ----  |
| 

API Type

 | 

RESTful

 | 
| 

Protocol

 | 

HTTPS

 | 
| 

Authentication

 | 

OAuth 2.0 (token-based)

 | 
| 

Data Format

 | 

JSON

 | 
| 

Common HTTP Methods

 | 

GET, POST

 | 
| 

Rate Limits

 | 

Yes (e.g., 10/s, 100/min, 5000/hr)

 | 
| 

Versioning

 | 

Yes (v3 as of current version)

 | 

  

* * *

If you're integrating with IBISWorld's API, you can safely treat it as a standard REST API--ideal for modern web and backend services.

* * *

Q1: How can I efficiently cache data from the IBISWorld API while ensuring updates are detected?

Q2: What are best practices for securely managing and rotating OAuth tokens in a server-based integration?

Q3: How could I use granular endpoints to auto-populate a dashboard with real-time industry insights?

IBISWorld's API offers a comprehensive suite of endpoints designed to provide access to various sections of their industry and procurement reports. These endpoints facilitate both full report retrieval and granular data access, allowing users to integrate specific information into their systems efficiently.

  

Primary API Endpoints:

1. Full Report Retrieval:

    - Endpoint: GET /industry/v3/fullreport

    - Description: Returns the complete industry report, encompassing all available sections.

2. Granular Data Access:

    - Endpoint: GET /industry/v3/section/{sectionName}

    - Description: Retrieves specific sections of an industry report, such as market size, competitive landscape, or financial performance.

3. Updated Reports:

    - Endpoint: GET /industry/v3/updatedreports

    - Description: Provides a list of reports that have been updated within a specified date range.

4. Authentication:

    - Endpoint: POST /oauth/token

    - Description: Generates an access token required for authenticated API requests.

  

Note: The exact list of available sections for granular data access can be found in the API's Data Dictionary, which details all string values for sections, data types, and descriptions for returned classes and fields.

  

Upcoming Enhancements:

  

IBISWorld has announced plans to introduce additional endpoints to provide more detailed insights. These include:

- Key Takeaways
- Product Innovation Analysis
- Product Innovation Level
- Buyer Power Analysis
- Supplier Power Analysis
- Substitutes Analysis
- Industry Structure

  

These enhancements aim to offer more customizable and impactful industry information, allowing users to retrieve specific data points across multiple reports efficiently.

  

For a comprehensive understanding of all available endpoints and their functionalities, it's recommended to consult the official [IBISWorld API Documentation](https://api.ibisworld.com/docs/).

Yes, IBISWorld provides a Data Dictionary as part of its API documentation. This resource offers comprehensive details, including:

- All string values for sections that can be used as body parameters
- Data types and descriptions for all returned classes and fields

  

You can access the Data Dictionary through the official IBISWorld API Documentation:

  

👉 [IBISWorld API Documentation](https://api.ibisworld.com/docs/)

  

This documentation is essential for developers and API users aiming to integrate IBISWorld data seamlessly into their applications. It ensures a clear understanding of how data maps to API endpoints, facilitating efficient and accurate data retrieval. 

  

If you need further assistance navigating the Data Dictionary or have specific questions about integrating IBISWorld's API into your systems, feel free to ask!

By leveraging these granular data points, organizations can enhance decision-making processes, conduct in-depth market analysis, and integrate relevant insights into their operational systems.