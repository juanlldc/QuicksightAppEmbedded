# QuickSight Embedded Compete Hack Hours 
Resources for the QuickSight Embedded Compete Hack Hours 

Hello and welcome to the QuickSight Embedded Compete Hack Hours! In this short tutorial we will explore how to embed QuickSight Dashboards in our own web app.

## Prerequisites

Before starting this tutorial, you will need an [AWS Free Tier account](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all) 

## Setting up the web app

In this section we will set up the web app where we will embed our dashboard. Log in to your AWS portal and look up Amplify. In here click on "Getting Started" and select "Host your web app". Follow the instructions to set up Amplify.

Then proceed with creating an Amplify app. Select "Deploy without GIT Provider" and upload the SampleApp.zip file that you will find in this repo. Give your app and environment meaningful names and click on "Save and Deploy". You will see a link after succesfully deploying the app. Click on it to see what our website currently looks like.

## Exploring the QuickSight Portal

Now, return to your AWS console and look up QuickSight. If you don't have a QuickSight account it will prompt you to create a new one.

 ![image](main/Images/Screenshot%202023-04-19%20205705.png)

In here, select the Enterprise option. We won't be needing Q for this tutorial. DISCLAIMER: This will activate a 30 day free trial. Remember to cancel your QuickSight subscription from within the portal to avoid any unwanted charges!!!

Now that you have access to the QuickSight portal, explore the following sections on the left hand of your screen. Datasets is where you connect to data and set up your relational models from. 

The Analyses section is where visualizations can be created from the data, combined and arranged together to set up different views. Explore one of the example analyses to familiarize yourself with the interface. 

Next up, let's publish a dashboard from our Business Review Analysis. Click it to access the development screen. Inside here, click on the Share icon in the top right corner and click on publish dashboard. Give your dashboard a name.

Now you can explore what a 1-page dashboard looks like. Next up, click on your user menu in the top right corner and click "Manage Quicksight". 

Here we will whitelist our Amplify website URL so that we can embed our dashboard. In the left-hand side menu, click on the Domains and Embedding menu. Paste your website URL and click on save. You can select to include the sub-domains if multiple of your HTML pages are going to be using the dashboard. This won't be needed for this tutorial.
