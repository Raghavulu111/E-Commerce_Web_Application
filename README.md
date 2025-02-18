# spring-boot-react-ecommerce-app

 
**FEATURES**
- Regular Username/Password authentication.
- Search bar and Search suggestions help to find products quickly.
- Stores user information in the MySQL database.
- Select filters to display products based on the selections.
- Sort products by popularity, newest, and prices.
- Pagination to display max products on a single page.
- Stores authentication details like token information in cookies.
- Store cart's product information in cookies.
- Payment service using Stripe's API to buy products.
- Responsiveness support for all devices.

**TOOLS USED**

- **ReactJS:** Front-end Javascript framework.
- **Spring Boot 2.0:** Back-end JAVA framework to build microservices using Spring Rest Controller and Spring JPA.
- **Material-UI:** Used Google's material design based on the CSS Framework for a responsive website.
- **Semantic-UI:** Used some components which Material-UI doesn't support.
- **MySQL:** Stores product and user information.
- **Stripe:** Payment service API to handle user payment requests.
- **AWS:** Deploying microservices on E.
- **Docker-Compose:** Easy way to bring up the application using containerization and behaves similarly in the production environment.
 
**MICROSERVICES**

- **React-UI Service:** Front-end client UI which displays data and makes API calls using Axios API.
- **Common Data Service:** Handles client request to provide common data such as product, filters, categories and order information, etc. 
- **Authentication Service:** Creates user account and handles username/password authentication.
- **Payment Service:** Handles payment requests from the client and makes a subsequent request to Stripe API
 for money deduction. 


1. Clone/Download the repository.

2. Set the environmental variables which will be impacted on docker-compose.yml.
   
    1. Rename the file ".env-sample" to ".env".     
    2. (Optional Step) You need to create a Stripe account and Google OAuth credentials.
       The application works even if you don't create this account, only the payment and OAuth functionality will not work.
       These accounts doesn't charge you anything and are absolutely free.<br/><br/>

       You need to set below two env variables.<br/><br/>

       REACT_APP_STRIPE_PUBLISH_KEY=<Your Stripe Publishable Key>

       Go [Here](https://dashboard.stripe.com/register) to create a Stripe account.
       <br/><br/>
       REACT_APP_GOOGLE_AUTH_CLIENT_ID=<Your Google AUTH Client ID>

       Go [Here](https://console.developers.google.com) to create Google OAuth Credentials.

3. Build all the microservices and run the app using docker-compose. This is done using ./start-all.sh script which creates the network and set the container dependencies based on the config mention in the docker-compose.yml. 
   This will build all the jar files and run all the services.
   ```
      ./start-all.sh
   ```

4. If you are making any change in the code then you need to you ./stop-all.sh to clean up the jars created by ./start-all.sh script.

**Payment Service Test Details:**

    Credit card no.: 4242 4242 4242 4242
    Expiry: Any future date
    CVV: Any 3-digit number

**Steps to deploy on EC2 using docker-compose:**

1. create heroku.yml as docker-compose.yml is not invoked on Heroku.

2. If the application contains a database then install MySQL or any other database 
   from Heroku marketplace[https://elements.heroku.com].
   <br/><br/>
   Note: Before installing you need to add credit/debit card info. Without this it 
   won't allow you to install the database.


3. Set the config vars based on the database URL.
    

4. Set the stack:container for the application in order to build with docker-compose.
   ```
      Elastic stack bean stack:set container -a <application-name>
   ```
 
5. Deploy individual service on AWS Elastic Stack Bean.


