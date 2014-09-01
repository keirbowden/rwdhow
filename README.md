Hands-On Workshop: Responsive Design with Visualforce and Bootstrap
===================================================================

##About the Workbook##

This workbook shows you how to create a Visualforce page that utilises the Bootstrap responsive web design framework to adapt to the device it is being viewed on. No prior coding experience is necessary, however, a basic understanding of HTML and Visualforce is helpful.

Visualforce is a component-based user interface framework for the Salesforce1 platform. Using Visualforce, developers create custom user-interfaces to Salesforce applications and data.  While Visualforce is well-suited to build custom pages targetted at desktop users, it is less-suited to users who required a consistent user interface across a number of devices.

Bootstrap is a responsive web design framework ... todo - more here

The extercises in this workbook guide you through :

* Creating of a Visualforce page to display the details of a number of cases
* Adding this Visualforce page to the Salesforce1 application
* Installing the Twitter Bootstrap framework into your Salesforce instance
* Creating a second Visualforce page using the Boostrap Responsive Web Design framework
* Adding this page to the Salesforce1 application
* Enhancing to the page to improve the user experience on tablet devices

##Audience##
These tutorials are intended for developers who are new to the Salesforce1 platform or experieced Salesforce administrators who are looking to cross over to Visualforce development.

It is recommended that the exercises in the [Visualforce Workbook](http://www.salesforce.com/us/developer/docs/workbook_vf/workbook_vf.pdf) are completed prior to tackling this workbook

##Sign Up for Developer Edition##

This workbook is designed to be used with a Developer Edition organization, or DE org for short. DE orgs are multipurpose
environments with all of the features and permissions that allow you to develop, package, test, and install apps.

1. In your browser, go to https://developer.salesforce.com/signup.
2. Fill in the fields about you and your company.
3. In the Email Address field, make sure to use a public address you can easily check from a Web browser.
4. Type a unique Username. Note that this field is also in the form of an email address, but it does not have to be the same
as your email address, and in fact, it’s usually better if they aren’t the same. Your username is your login and your identity
on developer.salesforce.com, so you’re often better served by choosing a username such as
firstname@lastname.com.
5. Read and then select the checkbox for the Master Subscription Agreement and then click Submit Registration.
6. In a moment you’ll receive an email with a login link. Click the link and change your password.

## Tutorial 1: Create a non-responsive Visualforce page ##

In this tutorial, you will learn how to create and edit a non-responsive Visualforce page using the standard component library. 
Along the way you’ll familiarize yourself with page creation and the editor. Before you start, please create a free Force.com Developer Edition Environment, as indicated earlier in the “About the Workbook” section.

###Step 1: Navigate to the Visualforce Pages setup page###
1. Launch your browser and log into Salesforce.
2. At the top of any Salesforce page, click the down arrow next to your name. From the menu under your name, select Setup.
3. From the left pane, select Developer -> Pages

Screenshot here?

###Step 2: Create a new Visualforce Page###
1. On the resulting page, click the New button
2. Label the new page 'MultiCase'
3. Tab out of the label input field and the platform automatically names the page 'MultiCase'
4. Description ... todo  
5. Check the 'Available for Salesforce mobile apps' box - this is required to make the page available in the Salesrorce1 application.
6. Click the 'Quick Save' button

The platform automatically inserts some basic markup into your new Visualforce page - you can now access the page by opening a new browser tab or window and navigating to https://<salesforce_instance>/apex/MultiCase. If your Salesforce instance is
https://na1.salesforce.com for example, the new URL is https://na1.salesforce.com/apex/MultiCase

Screenshot here

###Step 3: Add the multi-case view markup###

1. In the browser tab/window containing the Visualforce page editor, paste the following markup into the Visualforce Markup area and click 'Quick Save':

```
  <apex:page standardController="Case" recordsetVar="cases" sidebar="false" showheader="false">
    <apex:sectionHeader title="Cases" />
    <apex:pageBlock mode="maindetail">
      <apex:repeat value="{!cases}" var="case">
        <apex:pageBlockSection title="{!case.CaseNumber}">
          <apex:outputField value="{!case.Subject}"/>
          <apex:outputField value="{!case.Priority}"/>
          <apex:outputField value="{!case.Account.Name}"/>
          <apex:outputField value="{!case.Contact.Name}"/>
          <apex:outputField value="{!case.Status}"/>
        </apex:pageBlockSection>
      </apex:repeat>
    </apex:pageBlock>
  </apex:page>
```

## Tutorial 2: Make the page available in the Salesforce1 application ##

## Tutorial 3: Install the Bootstrap framework ##

## Tutorial 4: Create a responsive Visualforce Page ##

## Tutorial 5: Enhance the page for tablet devices ##
