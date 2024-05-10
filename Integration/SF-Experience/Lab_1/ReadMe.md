# Integration Experiences  
## Salesforce Experience
## Lab 1: Build Salesforce API in minutes  
Multi-Style Integration with IBM Cloud Pak for Integration the Salesforce Experience.


[Return to main lab page](../index.md)

---

# Table of Contents 
- [1. Introduction](#introduction)
  * [Pre-Lab: Gathering your Salesforce Credentials](#pre_lab)
- [2. Create a Designer Flow in CP4I to Call Salesforce](#create_a_designer_flow_in_cp4i_to_call_salesforce)
  * [2a Testing the API flow](#testing_the_API_flow)
  * [2b Add an Additional Operation for our Salesforce API](#add_an_additional_operation_for_our_salesforce_API)
  * [2c Testing the New API Operation](#testing_the_new_API)
- [3. Deploying Your Designer Flow to App Connect Dashboard](deploying_your_designer_flow_to_app_connect_dashboard)
    
---

# 1. Introduction <a name="introduction"></a>

The purpose of this LAB is to show how to retrieve Salesforce Account Records using IBM App Connect Designer on IBM Cloud Pak for Integration (CP4I). When prompted to log in to CP4I use the username and password provided to you for this lab.  

**Gathering your own SalesForce Credentials**
- For this lab, a Salesforce Smart Connector is already connected with shared credentials.

# 2. Create a Designer Flow in CP4I to Call Salesforce  <a name="create_a_designer_flow_in_cp4i_to_call_salesforce"></a>

In this section we use App Connect Designer to create a flow that will be exposed as an API to connect and call Salesforce records.

1\. Access Cloud Pak for Integration Platform UI as described in Access Environment section [here](access-env.md).
If you are alredy logged in IBM Cloud Pak for integration Platform UI, continue to step 2.

2\.  Navigate to the App Connect Designer, designer-authoring instance.

![alt text][pic4a]

3\. Select the tab on the left to open the Catalog screen.  The App Connect catalog provides a list of applications and APIs that are available.

![alt text][pic3]

4\. To setup the Salesforce account connection, click on the Connect button.
* **Note:** **If you already have the Salesforce smart connect account setup skip to step 9**.

![alt text][pic4]

5\. Fill in the Salesforce connection info that you were provided from the instructor.    
**Note:**
You should have received the credentials and it will look similar to this.

![alt text][pic5a]

Use this info to fill in the following fields for the Smart connector.
* For the password field, enter your account password for your Salesforce account and suffix it with your Salesforce security token.  If your password is ABC and your token is 123, you would enter ABC123 into the password field
* The Client ID field in the Designer is the Consumer Key field in your Salesforce Connected App
* The Client secret field in the Designer is the Consumer Secret field in your Salesforce Connected App

![alt text][pic5]

6\. You will see the events and actions available with this connector. Also you can change the Account Name to something more meaningful to you by clicking on the 3 dots next to the Account name. 

![alt text][pic6]

7\. Click on the App Connect Designer dashboard icon:

![alt text][pic7]

8\. Select from the New drop down to create a new API flow:  

![alt text][pic8]

9\. First thing we will do is create the model for this.  We will call the model **SalesforceRetrieve**, then click on **Create Model**

![alt text][pic9]

10\. For this example, we will map the following properties which are all data type String. You can also set the data type to Number for properties containing numerical integer values. 

1. AccountID
2. AccountName
3. Website

![alt text][pic10]


11\. Now that we have defined the properties in our API model definition, we can implement a flow by clicking on the Operations tab. The Operations tab is located next to the Properties tab.
From the Operations drop-down menu, select Add a Custom Operation. Here we will customize the operation that we want our API to perform. 

12\. Customize the details of your API operation. 
* **Note**: You can optionally set a description for your individual API operation. 
    * Display Name: **Retrieve Accounts**
    * HTTP Verb: **GET** 
    * Operation Name: **accounts**
        * Note: The operation name will be a part of your API Endpoint URL and is therefore consumer-facing.
    * Response body: **SalesforceRetrieve**

13\. After customizing your API operation, the details should match the image below.

![alt text][pic11]

Now click the **Get /SalesforceRetrieve/accounts** tab can click the **Implement Flow** button next to our API operation definition. This will take us to the App Connect Designer flow. This is where we can insert Smart Connectors to communicate with a variety of external applications as well as implement conditional logic and callable flows. 

14\. After clicking the blue plus icon on our flow designer interface, we will be able to see the variety of Smart Connectors offered by IBM App Connect Designer. You will also see an option for callable flows which allows you to integrate more complex logic into your Designer flows by building them in App Connect Enterprise Toolkit and calling them via REST API protocols. 

![alt text][pic12]

15\. For our lab, we will be using the **Salesforce smart connector**, so scroll down to the Salesforce connector and select it.

16\. There is a vast catalog of different Salesforce objects you can interact with from App Connect Designer. In this lab we are retrieving Account information so go ahead and drop down the Accounts option and click Retrieve accounts.

![alt text][pic13]

17\. The next interface that populates under our Designer flow allows us to add conditionals to our integration flow. For example, if we want to retrieve all account records for a particular account, we can specify this condition by setting the AccountName key to the respective account.   

In our example, we will retrieve the first 4 Salesforce account records. In order to do this, we can set the Maximum number of items to retrieve field to 4.  And then select, Process 4 items from the collection in the radio button options. As you can see there is also some error handling options provided by App Connect Designer below.

A helpful feature offered by the Smart Connectors is the **“Try this action”** button on the right side of the canvas. Clicking this button will allow you to test your Salesforce connection. If your credentials and operations are configured correctly you should be able to pull records from Salesforce. 

![alt text][pic14]

18\. You can now click on the View details to see the results. This is done even before your API is complete and allows you to see info that is returned from Salesforce to be mapped. 

![alt text][pic15]

19\. This shows the Test Results details.

![alt text][pic16]

20\. Now we can configurate our API Response body to populate a successful response message with the data fields we are interested in returning to our consumer. Go ahead and click the **Response** button on the integration flow (outlined in the blue box below).

![alt text][pic17]

21\. Now we will map our API Response keys to the respective values we want our consumer to obtain from Salesforce. Let us start with the **AccountID** field. 

* Click on the blank Account ID field
* You will see the list of **Available mappings**, listed by relevance.

Click on **Account ID** under the **Salesforce / Retrieve accounts / Accounts** mapping. Repeat the process for the other two data fields.

![alt text][pic19]

22\. After populating all the fields your mapping should match the image attached below.

![alt text][pic20]

23\. We are now ready to start and Test the API but first need to give it a meaningful name.  This will automatically be saved.  Click the Done button to close the flow

![alt text][pic21]


[pic0]: images/0.png
[pic1]: images/1.png
[pic2]: images/2.png
[pic3]: images/3.png
[pic4]: images/4.png
[pic5]: images/5.png
[pic5a]: images/5a.png
[pic6]: images/6.png
[pic7]: images/7.png
[pic8]: images/8.png
[pic9]: images/9.png
[pic10]: images/10.png
[pic11]: images/11.png
[pic12]: images/12.png
[pic13]: images/13.png
[pic14]: images/14.png
[pic15]: images/15.png
[pic16]: images/16.png
[pic17]: images/17.png
[pic18]: images/18.png
[pic19]: images/19.png
[pic20]: images/20.png
[pic21]: images/21.png
[pic1a]: images/1a.png
[pic2a]: images/2a.png
[pic3a]: images/3a.png
[pic4a]: images/4a.png

# 2A Testing the API flow <a name="testing_the_API_flow"></a>

 In the previous steps we have tested the Salesforce Connector only. Now we are going to test the entire API flow.  

1\. Click on **Try this flow** icon on the upper part of the page.   

![alt text][pic8a]

2\. Click continue to confirm that you want to test the flow designed.

![alt text][pic9a]

3\. The flow is test and a "200 OK" result was shown on the page.
You can see the response of the API flow clicking on **View Details**

![alt text][pic10a]


4\. The Test Results Output is shown. You can see, as for the defined response mappping done in the previous steps, the API flow retrieves Account ID, Account Name and Website from Salesforce.

![alt text][pic11a]

[pic22]: images/22.png
[pic23]: images/23.png
[pic24]: images/24.png
[pic25]: images/25.png
[pic25a]: images/25a.png
[pic8a]: images/8a.png
[pic9a]: images/9a.png
[pic10a]: images/10a.png
[pic11a]: images/11a.png


# 2B Add an Additional Operation for our Salesforce API <a name="add_an_additional_operation_for_our_salesforce_API"></a>
In this section we will add an additional operation to get Account by ID.  
1\. Click on **Done**. 

![alt text][pic12a]

2\. Click on the Operations item. Now select to add another operation and select the Retrieve SalesforceRetrieve by ID. 

![alt text][pic26]

3\. Select “Implement flow” for the new operation and that will get us to the flow editor where we will select the “+” sign and scroll down to SaleForce connector and select Retrieve accounts.

![alt text][pic28]

4\. Add Salesforce connector to the flow, as done in the previous steps, selecting Account>Retrieve Accounts.
Now we will map our API Response keys to the respective values we want our consumer to obtain from Salesforce. Let us start with the **AccountID** field
* Click on the hamburger icon next to AccountID field. ![alt text][pic30]
* Now you will see the list of **Available mappings.**

Click on the **Salesforce / Retrieve accounts / Accounts** mapping and select Account ID. Repeat the process for the other two data fields. After populating all the fields your mapping should match the image attached below.

![alt text][pic31]

5\. We are now ready to start the API and test the new operation. 

[pic26a]: images/26a.png
[pic26]: images/26.png
[pic27]: images/27.png
[pic28]: images/28.png
[pic29]: images/29.png
[pic30]: images/30.png
[pic31]: images/31.png
[pic12a]: images/12a.png

# 2c Testing the New API Operation <a name="testing_the_new_API"></a> 

1\. Click on Salesforce Connector.
In our example, we will retrieve the first 4 Salesforce account records. In order to do this, we can set the Maximum number of items to retrieve field to 4. And then select, Process 4 items from the collection in the radio button options. As you can see there is also some error handling options provided by App Connect Designer below.
Then click **Try this Action** icon. 

![alt text][pic13a]

2\. Click Continue that you want to confirm.

![alt text][pic14a]

3\. Test shows result:200. You can click  on **View Details** to see Test Result.

![alt text][pic15a]

4\. Pick one of the AccountID from the Response to use in the other Operation.

![alt text][pic16a]

5\. Now go to the Request. Click on **View available mappings and edit sample data.**
Under Request URL Parameter> Object> AccountID paste the AccountID you pick previously.

![alt text][pic17a]

6\. We will now add a condition to retrieve the Account for the Account ID that is passed to the API. 
Come back to the Salesforce Connector and click on **Add condition**.

![alt text][pic18a]

7\. Let's add a condition that the Account retrieve will be the one passed as request.
Select Account ID from the drop down menu. Then click on the blanck field, then on the burger button. 
Under Request URL Parameter> Object select AccountID.

![alt text][pic19a]

8\. Click on **Try this action**

![alt text][pic20a]

9\. Click Continue that you want to confirm.

![alt text][pic21a]

10\. Test shows result:200. You can click  on **View Details** to see Test Result.
Test results show the retrieve account with Account ID that you passed into the Request Sample Input.

![alt text][pic23a]

11\. Now let's the the entire flow. Click on **Try this flow**

![alt text][pic24a]

12\. Test results show the retrieve account as set into the response.

![alt text][pic25aa]



[pic32]: images/32.png
[pic33]: images/33.png
[pic34]: images/34.png
[pic35]: images/35.png
[pic36]: images/36.png
[pic13a]: images/13a.png
[pic14a]: images/14a.png
[pic15a]: images/15a.png
[pic16a]: images/16a.png
[pic17a]: images/17a.png
[pic18a]: images/18a.png
[pic19a]: images/19a.png
[pic20a]: images/20a.png
[pic21a]: images/21a.png
[pic30aa]: images/30aa.png
[pic23a]: images/23a.png
[pic24a]: images/24a.png
[pic25aa]: images/25aa.png


# 3. Deploying Your Designer Flow to App Connect Dashboard <a name="deploying_your_designer_flow_to_app_connect_dashboard"></a>

Now we can export our Designer flow as a bar file to be deployed in the App Connect Dashboard on Cloud Pak for Integration. Navigate to your App Connect Designer Dashboard so we can export our flow as a BAR file. 

1\. Click on Dashboard to get back to the main designer page where you will see your API.

![alt text][pic37]

2\. You will see that your API and you then will click on the triple-dot icon on your Designer flow.  Select Export.

![alt text][pic38]

3\. We will export this API as a runtime flow asset.

![alt text][pic29aa]

4\. You will save the SalesforceDemo.bar file locally on your machine and will use that to deploy to the AppConnect runtime.


5\. Now we will go back to the Integration home page. Click on the IBM Cloud Pak for Integration on the top menu

![alt text][pic40]

6\. From CP4I Platform Navigator (access it by clicking IBM Cloud Pak for Integration button in the upper part of the page), select your App Connect Dashboard instance.

![alt text][pic6a]

7\. Now select the **Deploy Integration** option from your App Connect Dashboard capability

![alt text][pic26aa]

8\. We will now select the Designer Integration that we will deploy then click next.

![alt text][pic43]

9\. Now we will either drag and drop the BAR file we just exported or we can click to upload it. Then click next.

![alt text][pic44]

10\. The next section is for configuration you can look at all the options that are available. We will just be using the Designer Accounts which will include your Salesforce credentials.

![alt text][pic45]

11\. The final section is the server details. We will give it a name is-salesforce-accounts, then switch-on Advanced Setting.

![alt text][pic27aa]

12\. Scroll down and switch on **Designer event-driven flows** and **Designer API flows** to enable the runtime for event-driven flows and api flows built in App Connect Designer. Go ahead and click Create.

![alt text][pic28aa]

13\. This will take you back to the Servers Dashboard where you will see your new server. To start with, it will be showing Unavailable while it is starting up the pods for it.  Refresh the screen till it shows running.

![alt text][pic47]

14\. Once it is up and running it will show the following:

![alt text][pic48]

15\. We can also quickly test the API call running in the Integration server. First click on the tile and it will show the API. Click once more and you will be at the SalesforceDemo API test page. Select the Get accounts and you will see the API details. Click on Try it and then click the Send button. 

![alt text][pic49]

16\. You will see the following results. After reviewing this click on the Overview on the left menu. 

![alt text][pic50]

17\. On the overview page near the bottom you can click on the **Download OpenAPI Document** . We will use the OpenAPI Swagger document to import your API into IBM API Connect.
![alt text][pic51]

[Return to main lab page](../index.md)

[pic37]: images/37.png
[pic38]: images/38.png
[pic39]: images/39.png
[pic40]: images/40.png
[pic41]: images/41.png
[pic42]: images/42.png
[pic43]: images/43.png
[pic44]: images/44.png
[pic45]: images/45.png
[pic46]: images/46.png
[pic47]: images/47.png
[pic48]: images/48.png
[pic49]: images/49.png
[pic50]: images/50.png
[pic51]: images/51.png
[pic6a]: images/6a.png
[pic26aa]: images/26aa.png
[pic27aa]: images/27aa.png
[pic28aa]: images/28aa.png
[pic29aa]: images/29aa.png