# Tell me yelp, where should I eat out?!(still looking for a cool name!)
yelp is an online platform which provides information about businesses. Here, I build a recommendation system to predict a list of certain businesses, i.e., restaurants for users to dine out. This recommendation is based on QUICK EXPLANATION OF RECSYS ALGO!.


# Introduction & Goals
The primary objective of this project is to build a recommendation engine which can be useful for platform users (service demanders) and business owners (service suppliers). The visitors can benefit from such recommendation system by learning about the potential services to select while the business owners can get an insight what yelp may suggest the visitors as their potential competitors.  <br>
general advice: assign roles and policies for each step

- Orient this section on the Table of contents
- Write this like an executive summary
  - With what data are you working
  - What tools are you using: Lambda, Kinesis, API Gateway
  - What are you doing with these tools
  - Once you are finished add the conclusion here as well

# Contents

- [The Dataset](#the-data-set)
- [Used Tools](#used-tools)
  - [Connect](#connect)
  - [Buffer](#buffer)
  - [Processing](#processing)
  - [Storage](#storage)
  - [Visualization](#visualization)
- [Pipelines](#pipelines)
  - [Stream Processing](#stream-processing)
    - [Storing Data Stream](#storing-data-stream)
    - [Processing Data Stream](#processing-data-stream)
    - [Storage Streaming](#storage-streaming)
  - [Batch Processing](#batch-processing)
  - [Visualizations](#visualizations)
- [Demo](#demo)
- [Conclusion](#conclusion)
- [Follow Me On](#follow-me-on)
- [Appendix](#appendix)


# The Dataset
The dataset I utilized in this project comes from https://www.yelp.com/dataset which provides a subsample of yelp data for educational purposes. I have accessed to the February, 2020 version of the dataset on the yelp platform.<br>
The data geographically covers some states of United States and some providences of Canada. The dataset includes different types of businesses from restaurants to beauty salons. In this project, my focus is on *restaurants* which consists one-third of the businesses.<br>
This dataset consists of different json files to cover an overview of businesses, checkin information for businesses, customer reviews, tips, and user reviews. To get insights from different json pieces, I merged the datasets and used it as the final dataset. In yelp_EDA notebook **hyperline** , you can find more details about the yelp dataset.<br>
**work in progress** I chose yelp dataset because analyzing user-behavior dataset can generate valuable analytical-based solution for business problems. This dataset includes timestamped information which can be useful for visualization purposes (which I used to do CERTAIN VISUALIZATION FOR UI). The categorical features in the dataset ease data filtering task.
### The potential roadblocks in this dataset are... 
### What do you want to do with it? Using Collaborative Filtering (probably computationally expensive, i.e. what products similar users liked) or Content-based filtering (i.e. previous likes of a user, and keywords)



# Used Tools in AWS as Platform
- Liuna: my client: **main client is python** so main after merging the data in pandas, will change it to json
- Explain which tools do you use and why
- How do they work (don't go too deep into details, but add links)
- Why did you choose them
- How did you set them up

## Connect: API gatwaway in AWS
## Buffer: Kinesis
## Processing: batch 
* batch: 1. scheduler (CouldWatch) or Apache Airflow/ 2. processing (lamda) / 3 .source / 4. processing / 5. destination
## Storage
**Storage Stream** pipeline includes all the tasks related to five json files, as my clients, to perform data storage.
Detail:
Step1: I need to connect to API Gateway and need to create a lambda function. So, on AWS Lambda, I create my lambda function and call it "writekinesis". It is useful to have execution role so I create a "new role" it while creating the lambda function. This executation role gives rights to the lambda fucntion to write kinesis. (Some other options: set the memory, set retry attemps).<br>
Step2: For Rest API, I use post method which in my python code(hyperlink here) I leveraged requests python library to access. Basically, with post, I send the data to teh API. Here are the steps: In Amazon API Gateway, 1.Create API, select REST API, name the API "helloworld".
2. Create resources and methods(Actions): First create a resources by giving the resource a name "hello", and on the resource create methods which can be post, get, delete, etc. I craeted get, post, put methods, but for now only using post method to upload the tables. For each method, i configured them to the lambda fucntion. 
For integration type, i use lambda fucntion, pick the region, and type the "writekinesis" as the name of Lambda Function. After configuration, I modified the post method further, by Mapping Templates and on Content-Type use aaplication/json which is also used in our python codes as headers = {'Content-type':'application/json', 'Accept':'application/json'}. In addition, for Generate Template, I chose Method Request Passthrough.<br>
Step3: Amazon Kinesis: create a data stream, specify number of shards.<br>
Step4: IAM (Identity and Access Management) for API which the goal is to make sure lambda function can write in Kinesis.
AWS Lambda: In the fucntion we created WriteKinesis, in configuration, the basic settings we need to set up the correct execution role which is the last line. So here there are two options to attch policies: 1. setting a new policy, 2. setting already existed default policy.
I pciked AmazonKinesisFullAccess as the default policy, and MyKinesisWriteAPIdata as set new policy. For MyKinesisWriteAPIdata, I pick Kinesis as Service, and PutRecord, and PutRecords for Actions. MAY ADD MORE LATER <br>
Step5: I prepared a python scrip (hyperlink) for the lambda function to post the json files. 
* go to cloudwatch to see the logs
What does writeKinesis include? explaing how the psot method sends the data to API (hyperlink) via lambda function to kinesis<br>

Step6: starting with a small sample, i.e. a few lines of real data, check the python code (hyperlink the API URL code). In the code I need to specify the url. The url address comes from creating a stage in Amazon API Gateway and the address is shown on top of page as Invoke URL which accomadates sending data to the API.<br>
Step7: To test the pipeline, we run the python script, we can check the cloudwatch and also kinesis check monitoring "incoming data" and "put record" <br>

docker: fargate: do i need this?! 
https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html
also, https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html (not sure i did everything)

Getting Started with Amazon Elastic Container Service (Amazon ECS) using Fargate



# Stream To Raw Storage S3 Pipeline
use s3 as data lake or storage
Step1: create a bucket: I created a bucket called yelp-project-bucket, and kept all default opions for the setting. Eventually, all my 5 json files will be streamed in yelp-project-bucket.<br>
Step2: Config IAM:create a role for aws service called Lambda-Kinesis-S3-Writer and add default policy of AmazonS3FullAccess, AWSLambdaBasicExecutionRole
Step3: lambda function for yelp-project-bucket: create a function, use blueprint kinesis-process-record-python: use existing role Lambda-Kinesis-S3-Writer, choose kineses trigger as kinesis stream of APIData


## Visualization


# Pipelines
- Explain the pipelines for processing that you are building
- Go through your development and add your source code

## Stream Processing
### Storing Data Stream
### Processing Data Stream
## Batch Processing
## Visualizations

# Demo
- You could add a demo video here
- Or link to your presentation video of the project

# Conclusion
Write a comprehensive conclusion.
- How did this project turn out
- What major things have you learned
- What were the biggest challenges? the down sides of each filtering method

# Follow Me On
https://www.linkedin.com/in/liuna-issagholian/

# Appendix

