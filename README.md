# Template Retail Omnichannel Experience API

+ [License Agreement](#licenseagreement)
+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [APIs security considerations](#apissecurityconsiderations)
+ [Run it!](#runit)
	* [Running on premise](#runonopremise)
	* [Running on Studio](#runonstudio)
	* [Running on Mule ESB stand alone](#runonmuleesbstandalone)
	* [Running on CloudHub](#runoncloudhub)
	* [Deploying your Anypoint Template on CloudHub](#deployingyouranypointtemplateoncloudhub)
	* [Properties to be configured (With examples)](#propertiestobeconfigured)

# License Agreement <a name="licenseagreement"/>
Note that using this template is subject to the conditions of this [License Agreement](AnypointTemplateLicense.pdf).
Please review the terms of the license before downloading and using this template. In short, you are allowed to use the template for free with Mule ESB Enterprise Edition, CloudHub, or as a trial in Anypoint Studio.

# Use Case <a name="usecase"/>

As a Customer I want a service to request information about me (personal information, my billing and shipping address, my payment methods), information about provided products, shopping carts and orders. 

### GET/customers/{customerId}
This endpoint will trigger flow getCustomerFromSFDC which obtains a customer information by customerId. 

### PUT/customers/{customerId}
This endpoint will trigger flow putCustomerFromSFDC which updates a customer information by customerId. 

### GET/channels
This endpoint will trigger flow getChannels which obtains mocked information about supported channels. 
The main point is to support the most common channels to cover use-cases with WEB, mobile and brick-and-mortar(store) based application delivering the Omnichannel user experience.

### GET/channels/{channelId}
This endpoint will trigger flow getChannel which obtains mocked information about particular channel by channelId.

### GET/channels/{channelId}/paymentMethods
This endpoint will trigger flow getChannel's payment methods by channelId. 
Channels basically could have different payment methods according to channel type like VISA card, bank transfer, cash. 

### GET/products
This endpoint will trigger flow getProducts which obtains mocked information about products from Product System API. 

### GET/products/{productId}
This endpoint will trigger flow getProducts which obtains mocked information about product from Product System API by productId. 

### GET/products/{productId}/variants
This endpoint will trigger flow getVariantsByProduct which obtains mocked information about variants of product from Product System API by productId.

### GET/products/{productId}/variants/{variantId}
This endpoint will trigger flow getVariantByProduct which obtains mocked information about variant of product by productId and variantId.

### GET/products/{productId}/variants/{variantId}/availability
This endpoint will trigger flow getAvailability which obtains mocked information about availability of variant by productId and variantId.

### GET/categories/{categoryId}/products
This endpoint will trigger flow getProductsByCategory which obtains mocked information about products from same category by categoryId.

### GET/shoppingCarts/{shoppingCartId}
This endpoint will trigger flow getShoppingCart which obtains information about products in shopping cart by shoppingCartId.

### PUT/shoppingCarts/{shoppingCartId}
This endpoint will trigger flow putShoppingCart which updates information about products in shopping cart by shoppingCartId.

### POST/shoppingCarts/
This endpoint will trigger flow get which saved new shopping cart to the object store.

### DELETE/shoppingCarts/{shoppingCartId}
This endpoint will trigger flow deleteShoppingCart which removes shopping cart from object store by shoppingCartId.

### GET/customers/{customerId}/shoppingCarts/
This endpoint will trigger flow getShoppingCartsForCustomer which obtains list of shopping cart for customer by the customerId. If customer does not exist, response is empty field.  

### POST/orders/
This endpoint will trigger flow createOrder which creates new order by customer.

### GET/customers/{customerId}/orders/
This endpoint will trigger flow getOrdersByCustomer which obtains list of orders for customer by customerId.

### GET/stores
This endpoint will trigger flow getStores which obtains list of stores.

### GET/stores/{storeId}
This endpoint will trigger flow getStore which obtains store by the storeId.

### GET/partners
This endpoint will trigger flow getPartners which obtains list of partner stores.

### GET/partners/{partnerId}
This endpoint will trigger flow getPartner which obtains partner store by the partnerId.

# Considerations <a name="considerations"/>

To make this Anypoint Template run, there are certain preconditions that must be considered. **Failling to do so could lead to unexpected behavior of the template.**

## APIs security considerations <a name="apissecurityconsiderations"/>
This Experience API is meant to be deployed to CloudHub and managed using the API Platform Manager.
   

# Run it! <a name="runit"/>
Simple steps to get Retail Omnichannel Experience API running.
See below.

## Running on premise <a name="runonopremise"/>
In this section we detail the way you should run your Anypoint Template on your computer.


### Where to Download Mule Studio and Mule ESB
First thing to know if you are a newcomer to Mule is where to get the tools.

+ You can download Mule Studio from this [Location](http://www.mulesoft.com/platform/mule-studio)
+ You can download Mule ESB from this [Location](http://www.mulesoft.com/platform/soa/mule-esb-open-source-esb)

### Importing an Anypoint Template into Studio
Mule Studio offers several ways to import a project into the workspace, for instance: 

+ Anypoint Studio generated Deployable Archive (.zip)
+ Anypoint Studio Project from External Location
+ Maven-based Mule Project from pom.xml
+ Mule ESB Configuration XML from External Location

You can find a detailed description on how to do so in this [Documentation Page](http://www.mulesoft.org/documentation/display/current/Importing+and+Exporting+in+Studio).

### Running on Studio <a name="runonstudio"/>
Once you have imported you Anypoint Template into Anypoint Studio you need to follow these steps to run it:

+ Generate keystore and truststore (You can find a detailed description on how to do so in this [Documentation Page](https://docs.mulesoft.com/mule-user-guide/v/3.7/tls-configuration#generating-keystores-and-truststores))
+ Locate the properties file `mule-<env>.properties`, in src/main/app/resources
+ Complete all the properties required as per the examples in the section [Properties to be configured](#propertiestobeconfigured)
+ Once that is done, right click on you Anypoint Template project folder 
+ Hover you mouse over `"Run as"`
+ Click on  `"Mule Application"`

### Running on Mule ESB stand alone <a name="runonmuleesbstandalone"/>
Complete all properties in one of the property files, for example in [mule.prod.properties](../master/src/main/resources/mule.prod.properties) and run your app with the corresponding environment variable to use it. To follow the example, this will be `mule.env=prod`. 

## Running on CloudHub <a name="runoncloudhub"/>
While [creating your application on CloudHub](http://www.mulesoft.org/documentation/display/current/Hello+World+on+CloudHub) (Or you can do it later as a next step), you need to go to `"Manage Application"` > `"Properties"` to set all environment variables detailed in **Properties to be configured**.
Follow other steps defined [here](#runonpremise) and once your app is all set and started, there is no need to do anything else.

### Deploying your Anypoint Template on CloudHub <a name="deployingyouranypointtemplateoncloudhub"/>
Mule Studio provides you with really easy way to deploy your Template directly to CloudHub, for the specific steps to do so please check this [link](http://www.mulesoft.org/documentation/display/current/Deploying+Mule+Applications#DeployingMuleApplications-DeploytoCloudHub)

## Properties to be configured (With examples) <a name="propertiestobeconfigured"/>
In order to use this Mule Anypoint Template you need to configure properties (Credentials, configurations, etc.) either in properties file or in CloudHub as Environment Variables.
Detailed list with examples:
### Application properties
+ http.port=`8081`

####Customer system API
+ customer-system-api.host=`customer.example.com`
+ customer-system-api.port=`443`
+ customer-system-api.baseUrl=`/api`

####Product system API
+ product-system-api.host=`product.example.com`
+ product-system-api.port=`80`
+ product-system-api.baseUrl=`/api`

####Orders system API
+ orders-system-api.host=`order.example.com`
+ orders-system-api.port=`80`
+ orders-system-api.baseUrl=`/api`

####Order fulfillment proces API
+ order-fulfillment-api.host=`order-fulfillment.example.com`
+ order-fulfillment-api.port=`80`
+ order-fulfillment-api.baseUrl=`/api`

####Shopping Cart proces API
+ shopping-cart-proces-api.host=`shopping-cart.example.com`
+ shopping-cart-proces-api.port=`80`
+ shopping-cart-proces-api.baseUrl=`/api`

####Locations system API
+ locations-system-api.host=`locations.example.com`
+ locations-system-api.port=`80`
+ locations-system-api.baseUrl=`/api`

####Partners system API
+ partners-system-api.host=`partners.example.com`
+ partners-system-api.port=`80`
+ partners-system-api.baseUrl=`/api`