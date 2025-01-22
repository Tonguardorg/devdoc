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
Each user is provided with a personalized package, similar to a subscription plan, tailored to their needs and offering 
specific usage limits for various services. Within the package, users have access to:

- **A set number of risk scoring requests** for analyzing and evaluating risks.  
- **Access to a visualizer** for generating clear and intuitive graphical representations of data.  
- **A limit on the number of wallets** available for monitoring, enabling activity tracking and transaction analysis.  

This approach ensures transparency and flexibility, allowing each user to choose the level of service that best suits 
their requirements.

Authorization methods, claims submission, as well as white and blacklisting features, do not affect the user's package. 
These functionalities are available independently of the chosen plan and can be used without limitations, 
ensuring seamless and consistent access to essential tools and features.

### User limits
The system enforces the following limits on the number of simultaneous requests to ensure stability and performance:

- **20 requests per second**  
- **1,000 requests per minute**  
- **10,000 requests per hour**

These limitations are designed to maintain the reliability of the platform and ensure fair resource distribution among all users.


### Contacts
If you have any questions, feel free to reach out to us:  
- **Email:** [info@tonguard.com](mailto:info@tonguard.com)  
- **Telegram Bot:** [@tonguard_bot](https://t.me/tonguard_bot)  

Our team is always here to assist you!
