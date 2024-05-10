# Integration Experiences  
## Salesforce Experience  

### Multi-Style Integration with IBM Cloud Pak for Integration the Salesforce Experience   

## Lab 3 - Build Salesforce Event Driven flow

[Return to main lab page](../index.md)

---

# Table of Contents 
- [1. Introduction](#introduction)
  * [Pre-Lab: Gathering your Salesforce Credentials](#pre_lab)
- [2. Setup connection to Smart connectors for this lab](#Setup_connections)
- [3. Create a Designer Event Flow in CP4I for Salesforce ](#create_a_designer_flow)
- [4. Testing the Event flow ](#test_a_designer_flow)
- [5. Deploying Your Designer Flow to App Connect Dashboard  ](#deploy_a_designer_flow)
    
---

# 1. Introduction <a name="introduction"></a>

In an event-driven flow you identify an event that can occur in your source application and actions that can be performed in one or more target applications. The flow is triggered when the event occurs.
* The purpose of this LAB is to show how to create an event-driven flow to identify when new Salesforce Account Records are created. 


# 2. Setup connection to Smart connectors for this lab<a name="Setup_connections"></a>

In this section we use App Connect Designer to create a flow that is triggered when an event occurs on Salesforce records.

First make sure you are logged into the CP4I Platform Navigator using the account the instructor provided to you. 

1\. For this lab we will be using MQ to receive the events from App Connect so we will go and create a new Queue Manager. 
Click in the upper part of you windows on IBM Cloud Pak for Integration, then on the **mq** instance.

2\. Now save the name of your QMgr (for you it will be QM01) and click on the tile to open that Qmgr dashboard.

![alt text][pic6g]

3\. Now we will create a new Queue to use in our new flow

![alt text][pic6h]

4\. We will be creating a new Local queue.  

![alt text][pic6i]

5\. Enter the name for the Queue, in this format "SALESFORCE.ACCOUNT.EVENT" then click Create.  

![alt text][pic6j]

6\. Now go back to the tab with the App Connect Designer and select the catalog on the left menu. Scroll down to IBM MQ and fill in the connection info.  
* Enter your QMgr name (QM01)
* For the QMgr host we will use the service name provided by your instructor.
* Port is 1414
* Channel SYSTEM.DEF.SVRCONN

![alt text][pic6k]

# 3. Create a Designer Event Flow in CP4I for Salesforce  <a name="create_a_designer_flow"></a>

1\. In App Connect Designer, click on the dashboard icon.

![alt text][pic7]

2\. Select from the New drop down to create a new Event-driven flow.  

![alt text][pic8]

3\. Enter a name that identifies the purpose of your flow, for example "Salesforce New Account Events". 

![alt text][pic9]

4\. Click on the first Blue + and scroll down to Salesforce connector.   Select New account under Accounts.  

![alt text][pic10]

5\. Now we show the Salesforce connector.  Click on the next Blue + and scroll down to IBM MQ.  Select the Put message action.

![alt text][pic11]


6\. Now enter the Queue Name you created for MQ.  We used SALESFORCE.ACCOUNT.EVENT
* For Message type select Text
* For the Message payload click on the insert mapping and you will have a list of Suggested mappings.  Scroll down and select the Account Name. 
**Note**: If Account Name is not in the list, click on All mapping, then you will find it under Salesforce/New Account.

![alt text][pic12]

7\. Now we are ready to start the flow.  In the upper right corner click on Start the flow.  

![alt text][pic13]

# 4 Testing the Event flow <a name="test_a_designer_flow"></a>

1\. Now let's add a new account in Salesforce. 
Click on ACE dashboard. You have been provided by an API that, if tested, create a new account in Salesforce.
Enter the API AddSalesforceAccount

![alt text][pic1ale]

2\. Click on Edit Flow

![alt text][pic2ale]

3\. Click on the Salesforce Connector and populate Account name, Account type, Billing street, Billing city with you preferred input, as the screen below.

![alt text][pic3ale]

4\. Now click on Try this action. It will test the Smart Connector creating a new account in Salesforce.

![alt text][pic4ale]

5\. Now return to the tab where you have the MQ console opened. Inside your queue manager and the local queue you just create you should see messages for your new account created in Salesforce using the API AddSalesforceAccount.
* This is where we will check when we test this flow. 


[pic0]: images/0.png
[pic1]: images/1.png
[pic2]: images/2.png
[pic3]: images/3.png
[pic4]: images/4.png
[pic5]: images/5.png
[pic6]: images/6.png
[pic6a]: images/6a.png
[pic6b]: images/6b.png
[pic6c]: images/6c.png
[pic6d]: images/6d.png
[pic6e]: images/6e.png
[pic6f]: images/6f.png
[pic6g]: images/6g.png
[pic6h]: images/6h.png
[pic6i]: images/6i.png
[pic6j]: images/6j.png
[pic6k]: images/6k.png
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
[pic1ale]: images/1ale.png
[pic2ale]: images/2ale.png
[pic3ale]: images/3ale.png
[pic4ale]: images/4ale.png



[pic22]: images/22.png
[pic22a]: images/22a.png
[pic22b]: images/22b.png
[pic23]: images/23.png
[pic24]: images/24.png
[pic25]: images/25.png
[pic25a]: images/25a.png
[pic26]: images/26.png
[pic27]: images/27.png


# 5. Deploying Your Designer Flow to App Connect Dashboard <a name="deploy_a_designer_flow"></a>

As in other labs we can export our Designer flow as a bar file and deploy to App Connect Dashboard on Cloud Pak for Integration. We will not do that in this lab.   


[Return to main lab page](../index.md)
