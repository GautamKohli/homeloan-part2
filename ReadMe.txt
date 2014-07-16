Home Loan Project on Blueprint (OSGi)
=========================================

This is a follow up demo from previous demo, 
https://github.com/weimeilin79/homeloan-part1

The story behind the home loan demo is we have a system, that takes in XML files from different vendor's home loan application, they will place their customer input into 2 different XML files, one with it's customer data, the other with their housing details. Both files will be place into same folder either by FTP or Batch generated overnight.

First demo was to take in and process the information, first we need to separate the 2 kinds of files, because they are handled differently. And appraised the value of the house before sending it to a messaging broker.

And for this demo,  we are going to concentrate on processing the customer data, by reading the xml file and store it into a Postgres Database. There are many components in JBoss Fuse that you can choose to interact with DB. This demo uses the most simple and straight forward sql component, just like a normal sql insert in your java program, but less coding needed, isn't it fun!   

And then  we are going to do a bit more, with house data, we are going to add value to the house by the surrounding schools of the house. To do that we will need to reference Google App Engine (Google Geocoding API to get the co-ordinate from Address, then use Google Places API to get number of surrounding schools) and then update the new appraised value. Then store it into a table in Postgres Database.
With Google App Engine, just apply an developer account and then create an Application for it! 
Turn on both GeoCoding and Placr API.  

To build this project use

    mvn install

To run the project you can execute the following Maven goal

    mvn camel:run

To deploy the project in OSGi. For example using Apache ServiceMix
or Apache Karaf. You can run the following command from its shell:

    osgi:install -s mvn:org.blogdemo/homeloan/1.0.0-SNAPSHOT

For more help see the Apache Camel documentation

    http://camel.apache.org/
