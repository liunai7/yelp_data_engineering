# Tell me yelp, where should I eat out?!(still looking for a cool name!)
yelp is an online platform which provides information about businesses. Here, I build a recommendation system to predict a list of certain businesses, i.e., restaurants for users to dine out. This recommendation is based on QUICK EXPLANATION OF RECSYS ALGO!.


# Introduction & Goals
The primary objective of this project is to build a recommendation engine which can be useful for platform visitors (service demanders, any better term?) and business owners (service suppliers). The visitors can benefit from such recommendation system by learning about the potential services to select while the business owners can get an insight what yelp may suggest the visitors as their potential competitors.  

# random:<br>
To avoid cold start maybe: setting a only users with at leas 5 interactions? or just keep them<br>
collabrative : recommendations of existing users.<br>

content-base: location, type, name, hours?!<br>
Expects item information.
Item information should be in a text document.<br>

Non-probabilistic algorithm:
User-based nearest neighbor... computationally expensive/ trade-off: better performance by use reducing dim but quality of rec system is sacrifizing
Item-based nearest neighbor.
Reducing dimensionality.

* Motivation for Baseline
Imputation of missing values with baseline values.


Probabilistic algorithm:
Bayesian-network model.
EM algorithm.


Matrix factorization is a class of collaborative filtering algorithms used in recommender systems. Matrix factorization algorithms work by decomposing the user-item interaction matrix into the product of two lower dimensionality rectangular matrices.


good sources:
https://medium.com/towards-artificial-intelligence/recommendation-system-in-depth-tutorial-with-python-for-netflix-using-collaborative-filtering-533ff8a0e444

####
- Orient this section on the Table of contents
- Write this like an executive summary
  - With what data are you working
  - What tools are you using
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
  - [Batch Processing](#batch-processing)
  - [Visualizations](#visualizations)
- [Demo](#demo)
- [Conclusion](#conclusion)
- [Follow Me On](#follow-me-on)
- [Appendix](#appendix)


# The Dataset
The dataset I utilized in this project comes from https://www.yelp.com/dataset which provides a subsample of yelp data for educational purposes. I have accessed to the Feburary, 2020 updated version of the dataset on the yelp platform. <br>
This dataset consists of different json files to cover an overview of businesses, checkin information for businesses, customer reviews, tips, and visitors reviews. To get insights from different json pieces, I merged the datasets and used it as the final dataset.<br>
I chose yelp dataset because analyzing such great example of user-behavior dataset can generate valuable analytical-based solution for business problems. This dataset includes timestamped information which can be useful for visualization purposes (which I used to do CERTAIN VISUALIZATION FOR UI). The categorical features in the dataset ease data filtering task.
### The potential roadblocks in this dataset are... 
### What do you want to do with it? Using Collaborative Filtering (probably computationally expensive, i.e. what products similar users liked) or Content-based filtering (i.e. previous likes of a user, and keywords)



# Used Tools
- Explain which tools do you use and why
- How do they work (don't go too deep into details, but add links)
- Why did you choose them
- How did you set them up

## Connect
## Buffer
## Processing
## Storage
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

