## Customer API

Customer API is designed for seamless integration of the service's features into customer projects.

The API includes the following methods:

- **Risk Assessment**: Retrieve a wallet's risk level and risk score.  
- **Graph Analysis**: Build graphs for convenient analysis of wallets and their neighbors.  
- **Address Management**: Add addresses to whitelists and blacklists.  
- **Monitoring**: Track and monitor wallet activity.  
- **Manual Labeling**: Manually label complaints related to wallets.  


### Set up parameters 

> Version 2.0.0

Provides risk score and risk level estimation for TON blockchain addresses and etc  🚀


API URL ```https://api.tonguard.org/```

Requests are made using the POST, GET, PATCH and DELETE methods.

### User packages
Each user is provided with a **personalized package**, functioning like a subscription plan, designed to meet 
their unique needs. These packages come with specific usage limits tailored for various services, ensuring a fair and predictable experience for all users.

Within their package, users are granted access to the following:

- **Risk Scoring Requests**: A default of **200 requests** for analyzing and evaluating risks, enabling informed 
decision-making.
- **Data Visualizer**: Access to up to **5 visualizations**, providing clear and intuitive graphical 
representations of data for actionable insights.
- **Wallet Monitoring**: The ability to monitor up to **5 wallets**, allowing users to track activity and 
analyze transactions effectively.

These default values apply unless a customized package is selected. This model provides both transparency and 
flexibility, empowering users to select a service level that aligns with their specific requirements. It also 
ensures a balanced allocation of resources, promoting efficient usage across the platform.

Authorization methods, claims submission, as well as white and blacklisting features, do not affect the user's package. 
These functionalities are available independently of the chosen plan and can be used without limitations, 
ensuring seamless and consistent access to essential tools and features.

### User limits
To ensure platform stability and optimal performance, the system enforces the following limits on simultaneous requests:
- **20 requests per second**  
- **1,000 requests per minute**  
- **10,000 requests per hour**

These limitations are carefully designed to maintain the reliability of the platform while ensuring fair resource allocation 
among all users. Exceeding these limits may result in temporary rate limiting or delays in processing.

### Contacts
If you have any questions, feel free to reach out to us:  
- **Email:** [info@tonguard.com](mailto:info@tonguard.com)  
- **Telegram Bot:** [@tonguard_bot](https://t.me/tonguard_bot)  

Our team is always here to assist you!

---

### Documentation Updates

- 2024-12-10: Updated documentation
- 2025-05-07: Added Source of Funds and Token Analysis
- 2025-06-06: Updated documentation in general
