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

In this tutorial, you will create a non-responsive Visualforce page using the standard component library. 
Along the way you’ll familiarize yourself with page creation and the editor. Before you start, please create a free Force.com Developer Edition Environment, as indicated earlier in the “About the Workbook” section.

###Step 1: Navigate to the Visualforce Pages setup page###
1. Launch your browser and log into Salesforce.
2. At the top of any Salesforce page, click the down arrow next to your name. From the menu under your name, select Setup.
3. From the left pane, select Developer -> Pages

Screenshot here?

###Step 2: Create a new Visualforce Page###
1. On the resulting page, click the New button
2. Label the new page 'CaseMulti'
3. Tab out of the label input field and the platform automatically names the page 'CaseMulti'
4. Description ... todo  
5. Check the 'Available for Salesforce mobile apps' box - this is required to make the page available in the Salesrorce1 application.
6. Click the 'Quick Save' button

The platform automatically inserts some basic markup into your new Visualforce page - you can now access the page by opening a new browser tab or window and navigating to https://<salesforce_instance>/apex/MultiCase. If your Salesforce instance is
https://na1.salesforce.com for example, the new URL is https://na1.salesforce.com/apex/MultiCase

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

Your page should look as follows:

![MultiCase Page](https://lh3.googleusercontent.com/1aNd7HsZuguXzX4Zguod-9s0j3P2JC1EwV7ALpyf2do=w656-h521-no)


##Tutorial 2: Make the page available in the Salesforce1 application##

In this tutorial you will configure the page as part of the Salesforce1 application.

###Step1: Navigate to the Tab setup page##

1. Open the Setup menu, as described in Tutorial 1.
2. Select Create -> Tabs
3. Scroll down to the Visualforce Tabs section

 ![Tab Setup Page](https://lh3.googleusercontent.com/rKW6ghtSegtgEMyxsYIO6qH9_6Ml6S4JzAhKM-Qem9k=w489-h104)

###Step2: Create a Tab for the Visualforce Page##
1. Click the 'New' button
2. Choose 'CaseMulti' from the picklst of Visualforce Pages
3. Enter 'CaseMulti' for the tab label
4. Tab out of the label field - the platform will automatically populate the 'Name' field with 'Case Multi'
5. Select a tab style
6. Click the 'Next' button
7. Leave all settings on the resulting page at their default values and click the 'Next' button
8. Deselect all applications on the resulting page and click the 'Save' button

Screenshot here?

###Step3: Add the Tab to the Salesforce1 Menu##

1. Open the Setup menu, as described in Tutorial 1.
2. Select Mobile Administration -> Mobile Navigation
3. Move the 'CaseMulti' option from the 'Available' to the 'Selected' list and click the 'Save' button

Screenshot here.

The tab can now be accessed from the Salesforce1 application via the left hand menu:

Screenshot here

The page looks fine on the desktop:

and on a tablet device - an iPad in this case:

but on a mobile phone, the UI is less than ideal - the Subject field contents and Account Name label break onto multiple lines, displaying only one or two words per line:
 
##Tutorial 3: Install the Bootstrap framework##

In this tutorial you will download the Boostrap framework and install it into your Salesforce instance.  This will provide the basis for building a responsive page later in the workbook.

###Step1: Download the Bootstrap Zip File###

1. Open a new browser window 
2. Navigate to the Bootstrap site download page - http://getbootstrap.com/getting-started/#download
3. Choose the 'Download Bootstrap' option

(screenshot).

###Step2: Install the Bootstrap Zip File as a Static Resource###

1. Open the Setup page, as described in Tutorial 1
2. Select Develop -> Static Resources
3. On the resulting page click the 'New' button
4. Enter 'Bootstrap_3_2_0' in the name field
5. Enter 'Bootstrap framework version 3.2.0 in the Descripton field
6. Open the file chooser and select the file you downloaded in Step 1
7. Choose Public for Cache Control

Screentshot?

at the time of writing the version of Bootstrap is 3.2.0, if you are using a different version then rename the static resource accordingly


## Tutorial 4: Create a responsive Visualforce Page ##

In this tutorial, you will learn how to create and edit a non-responsive Visualforce page using the standard component library. 
Along the way you’ll familiarize yourself with page creation and the editor. Before you start, please create a free Force.com Developer Edition Environment, as indicated earlier in the “About the Workbook” section.

###Step 1: Create the basic Visualforce page###
1. Open the Setup page, as described in Tutorial 1
2. From the left pane, select Developer -> Pages
3. On the resulting page click the 'New' button
4. Enter 'CaseMultiRWD' for the page label
5. Tab out of the label field and the platform will automatically populate the name with 'CaseMultiRWD'.
 
###Step 2: Add the Bootstrap Resources###
1. Modify your Visualforce page to look like the following
```
<apex:page doctype="html-5.0" standardController="Case" recordsetVar="cases"
		   sidebar="false" showheader="false" standardstylesheets="false" applyHtmlTag="false">

  <html>
    <head>
  	  <title>Cases</title>
      <meta name="viewport" content="width=device-width, initial-scale=1.0"></meta>
      
      <apex:stylesheet value="{!URLFOR($Resource.Bootstrap_3_2_0, 'bootstrap-3.2.0-dist/css/bootstrap.min.css')}"/>
      <apex:stylesheet value="{!URLFOR($Resource.Bootstrap_3_2_0, 'bootstrap-3.2.0-dist/css/bootstrap-theme.min.css')}"/>
      <apex:includeScript value="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js" />
      <apex:includeScript value="{!URLFOR($Resource.Bootstrap_3_2_0, 'bootstrap-3.2.0-dist/js/bootstrap.min.js')}"/>
    </head>
    
    <body>
    </body>
  </html>
</apex:page>
```
2. Click the 'Quick Save' button to save and validate the page
The `<apex:page>` component specifies the `applyHtmlTag` attribute as false, which stops the platform automatically inserting an HTML `<head>` tag. This is required as you are specifying a meta tag to control the device viewport, which must appear inside the page header.  The meta tag contains two parameters:
* `width=device-width` makes the viewport the actual size of the device - without this parameter devices such as the iPhone will use a viewport width of 980px, which would require zooming and scrolling to be able to read the page
* `initial-scale=1.0` makes the initial scale of the viewport 100%. The user can zoom in or out of the page as they require

The Boostrap framework files are then imported from the static resource uploaded in Tutorial 3. Note that an additional JavaScript resource is included as Bootstrap relies on the JQuery JavaScript library:
`<apex:includeScript value="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js" />`
while we could have downloaded JQuery and made this available as a Static Resource, as it is available on the Google Content Delivery Network it is better to include from there, as it is likely that a user's browser has already encountered the file in this location and cached it for future use.

###Step3: Add a Bootstrap grid to the page###
Rather than using the standard Visualforce component library, we will use the Bootstrap responsive grid to layout the cases and fields.
1. Between the opening and closing `<body>` tags, add the following markup:
```
      <div class="container-fluid">
        <apex:repeat value="{!cases}" var="case">
          <div class="panel panel-primary">
	  		<div class="panel-heading">
      		  <h3 class="panel-title"><apex:outputField value="{!case.CaseNumber}"/></h3>
  		  	</div>
  		    <div class="panel-body">
              <div class="row">
                <div class="col-md-2">
                  <label>Subject</label>
                </div>
                <div class="col-md-4">
                  <apex:outputText value="{!case.Subject}" />
                </div>
                <div class="col-md-2">
                  <label>Priority</label>
                </div>
                <div class="col-md-4">
                  <apex:outputText value="{!case.Priority}" />
                </div>
              </div>

              <div class="row">
                <div class="col-md-2">
                  <label>Account</label>
                </div>
                <div class="col-md-4">
                  <apex:outputText value="{!case.Account.Name}" />
                </div>
                <div class="col-md-2">
                  <label>Contact</label>
                </div>
                <div class="col-md-4">
                  <apex:outputText value="{!case.Contact.Name}" />
                </div>
              </div>

              <div class="row">
                <div class="col-md-2">
                  <label>Status</label>
                </div>
                <div class="col-md-4">
                  <apex:outputText value="{!case.Status}" />
                </div>
              </div>
              
            </div>
          </div>
        </apex:repeat>
      </div>
```



## Tutorial 5: Enhance the page for tablet devices ##
