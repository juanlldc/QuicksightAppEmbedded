# QuickSight Embedded Compete Hack Hours 
Resources for the QuickSight Embedded Compete Hack Hours 

Hello and welcome to the QuickSight Embedded Compete Hack Hours! In this short tutorial we will explore how to embed QuickSight Dashboards in our own web app.

## Prerequisites

Before starting this tutorial, you will need an [AWS Free Tier account](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all) 

## Setting up the web app

In this section we will set up the web app where we will embed our dashboard. Log in to your AWS portal and look up Amplify. In here click on "Getting Started" and select "Host your web app". Follow the instructions to set up Amplify.

 ![image](Images/Screenshot%202023-04-19%20205803.png)
 
 ![image](Images/Screenshot%202023-04-19%20205826.png)

Then proceed with creating an Amplify app. Select "Deploy without GIT Provider" and upload the SampleApp.zip file that you will find in this repo. Give your app and environment meaningful names and click on "Save and Deploy". You will see a link after succesfully deploying the app. Click on it to see what our website currently looks like.

![image](Images/Web%20capture_19-4-2023_151813_us-east-1.console.aws.amazon.com.jpeg)

## Working on the QuickSight Portal

Now, return to your AWS console and look up QuickSight. If you don't have a QuickSight account it will prompt you to create a new one.

 ![image](Images/Screenshot%202023-04-19%20205705.png)

In here, select the Enterprise option. We won't be needing Q for this tutorial. DISCLAIMER: This will activate a 30 day free trial. Remember to cancel your QuickSight subscription from within the portal to avoid any unwanted charges!!!

 ![image](Images/Screenshot%202023-04-19%20205731.png)

Now that you have access to the QuickSight portal, explore the following sections on the left hand side of your screen. Datasets is where you connect to data and set up your relational models from. Here, select new dataset in the top right corner and upload the SuperStoreOrders.csv file from this repo.

 ![image](Images/Screenshot%202023-04-19%20205731.png)

Click next to continue the import and then click on visualize. This will open the Analysis page, but you will have to wait some 20 seconds until all the data is loaded. You should receive a "Succesful Import" message on the top right of your screen. You can always monitor your dataset imports from the datasets tab.

 ![image](Images/Screenshot%202023-04-19%20205731.png)

The Analyses section is where visualizations can be created from the data, combined and arranged together to set up different views. Let's build our first visualization! From your fields on the left, select Sales, Category and Segment. Then click on the stacked bar visualization icon. You should see a visualization like this.

Next up, let's publish a dashboard from our Analysis. Dashboards are views made from a single analysis, usually showing a quick glance at the data for maximum situational awarness. Dashboards cannot be edited but their data stays updated as long as the dataset is updated. Any changes to the analysis must be published to be reflected in the dashboard. Click on the share menu in the top-right corner and select "Publish Dashboard". This will bring you to the view-only dashboard page. To continue, click on your user icon in the top-right of your screen and select "Manage QuickSight".

This is the QuickSight configuration page, where you can customize all your account settings. Look for "Domains and Embedding" on the left menu. Here we will whitelist our domain URL so that we can correctly embed our dashboard. Copy the URL of the website that you just deployed on Amplify, paste it in the field and click on add. Here you can select to include the subdomains if you will be embedding on multiple pages of your website, but we will not need it in this case.  

Now that your domain name is cleared, return to your dashboard by clicking the QuickSight icon on the top left of your screen, navigating to the dashboards section and opening your dashboard. Look for the Share button again, as you did in your Analysis, and click on "Share Dashboard". From here click on "Copy Embed Code". This will generate an HTML Iframe element that we can paste on our HTML code.

## Embeding our dashboard

Now, open the index.html thatyou downloaded from this repo. It's a very simple file, so it's easily readable in the notepad app. You can embed the dashboard anywhere in the body, below the 3 boxes might be the best option. It's as easy as pasting the iframe element!

Now, compress the index.html file into a Zip folder and re-upload it to amplify as we did with the initial deployment. Reload the site and you should see your dashboard embedded in the site! 

## Adding a parameter

One of the possibilities with QuickSight static embedding is to pass a parameter through the URL to affect some of the context in the embedded dashboard. In this case, we are going to set up a filter for a specific segment, say we want to now embed this dashboard not for the whole sales team but just for the consumer area team. The first step is to return to our Analysis withing QuickSight. Here, access the Parameter section on the left menu and click on "Create one". Name your parameter "Segment" and add the 3 segments as static values. This will ensure all the data is visible when we don't specify a parameter value.

Next up, select the filters tab. Click on Add Filer and create a filter on the "segment" value. Click on the filter to edit the settings and select "custom filter". Set the condition to equals, click on use parameters (accept the warning that the scope of this filter will apply to all visuals in the analysis) and select your newly created parameter from the drop down list. Once you click on Apply Parameter nothing should change as we have set all the values as our default. At this point, you must remember to publish the analysis as a dashboard once again, or your changes will not be reflected. In the menu, choose to update your existing dashboard instead of creating a new one to ensure that your embedding code remains as it is. 

Now, to pass a parameter name through our embedding HTML file, return to your text editor. Find the iframe element and add "#p.Segment=Consumer" at the very end of the URL. the "#" indicates that we are adding information to the link, the p. means we are going to modify a parameter, followed by our parameter name and the desired value. You can pass multiple parameter values by adding "&" after the first one! To see your changes, save the HTML file, compress it into a .zip folder and re-upload it to amplify, as you previously did both times.

## Clean-up

Your AWS free tier account and Amplify shouldn't accrue any charges, but you can delete your Amplify apps from the deployment menu and close out your AWS account if you are not going to be using it any more. What you must do to avoid charges is to cancel your QuickSight trial before the 30 days expire. To do so, go back to the management menu and, from within the account settings, access the termination screen and follow the instructions.
