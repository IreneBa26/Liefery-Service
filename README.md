# Liefery-Service
Delivery services based on microservices

### About the project:
The company **ACMEat** offers its customers a service that allows them to select a menu from a set of affiliated restaurants and have it delivered to their door.

To use the service, the customer must initially select a city from those in which the service is active. After this selection, ACMEat presents a list of participating restaurants operating in that area and the menus they offer. The customer can then **specify the venue** and menu of his or her interest and a **time slot** for delivery (these are 15-minute slots between 12 noon and 2 p.m. and between 7 p.m. and 9 p.m.).

There then follows a payment phase that is handled through a **third-party banking institution** to which the customer is referred. Upon payment, the institution issues a token to the customer, who communicates it to ACMEat, which in turn uses it to verify with the bank that the payment has actually been completed. At this point, the order becomes operational. Customers may still cancel the order, but no later than one hour before the delivery time. In that case ACMEat asks the bank to cancel the payment.

ACMEat knows all the contracted venues in the various municipalities in which it operates and their days and hours of operation. In the event that a venue is not available on a day on which it would normally be open, it is the responsibility of the restaurant to contact ACMEat by 10 a.m. notifying them of this unavailability.

Changes to the proposed menus must also be communicated by this time (in the absence of such communication, it is assumed that the same menus from the previous day are available). The restaurants are also contacted for each order to verify that they are actually able to meet the customer's request. If this is not the case, the acceptance of the order is interrupted before the payment phase takes place.

ACMEat relies on several **external companies** for delivery: for each delivery, all companies based within 10 kilometres of the city concerned are contacted, specifying: the address of the place where the meal is to be collected, the address of the customer to whom it is to be delivered and the estimated time of delivery. 
In response to this request, the companies must respond within 15 seconds specifying their availability and the requested price. ACMEat will choose the company with the lowest price from those available that have responded in the required time. In case no delivery company is available, the order is cancelled before proceeding to the payment step


### Built with:
  
    Camunda Platform (Tomcat)
    Camunda Modeler
    Java
    Python
    Node.js
    Jolie
    Maven
    SoapUi
    UML diagram
  
------------------------------------------------------------------------------------------------------

### Project Folder:

  - **acme-agency**: Contains logic implementation (frontend - backend) of acme agency
  - **bankService**: Contains logic implementation of the bank services and manages the payment processes
  - **db**: Contains the restaurant database
  - **deliveryService**: Contains REST API and logic implementation of the delivery companies
  - **gisService**: Distance calculator for food delivery services
  - **restaurantService**: Contains logic implementation of the restaurants and manages the ordering processes

------------------------------------------------------------------------------------------------------

### Getting started:

   Prerequisites: Docker, Maven, Camunda Platform

------------------------------------------------------------------------------------------------------

### Installation:

1) Get an API key from https://www.graphhopper.com/

2) Sobstitute API_KEY in PROJ_DIR/gisService/distance.js with the generated one from step 2

3) Go into project folder

4) Execute 'build.sh'

5) Go into PROJ_DIR/acme-agency   

6) Execute 'mvn install'

7) Copy PROJ_DIR/acme-agency/acmeat/acmeat.war, PROJ_DIR/acme-agency/acmeat-ws/acmeat-ws.war and
   PROJ_DIR/acme-agency/acmeat-frontend/acmeat-frontend.war into CamundaPlatform/server/apache-tomcat-9.0.19/webapps
   
8) Edit CamundaPlatform/server/apache-tomcat-9.0.19/conf/context.xml adding <Loader delegate="true"/> inside <Context>
 
9) Copy 'restaurant.json' into CamundaPlatform/
 
