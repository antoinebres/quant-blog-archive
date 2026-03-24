# 10-rules-machine-learning-stack-production
Wayback Machine URL: https://web.archive.org/web/20230129145123/https://www.quantmetry.com/blog/10-rules-machine-learning-stack-production/
Archive date: 2023-01-29

Data Gouvernance 

16/03/2021 

#  10+ tips to deliver machine learning in production 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2F10-rules-machine-learning-stack-production%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=10%2B%20tips%20to%20deliver%20machine%20learning%20in%20production&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2F10-rules-machine-learning-stack-production%2F "Twitter")

* * *

Auteur : [ Gaultier LE MEUR ](https://www.linkedin.com/in/gaultierlemeur/)

Temps de lecture : 11 minutes 

![Quantmetry.com : 10+ tips to deliver machine learning in production](https://quantmetry.b-cdn.net/wp-content/uploads/2021/03/gle2.png)

This short and straightforward blogpost aims at sharing several best practices for delivering machine learning projects into production. It’s based on Quantmetry experience of developing, deploying and monitoring a product recommendation API on AWS following MLOps standards. Processes and technological best practices will be discussed below, the motto being “going live, staying calm”. Of course, this article is not meant to be exhaustive but rather a quick reminder of several aspects based on Quantmetry’s delivery experience. 

#####  TL;DR 

  * All stakeholders should agree on: 
    * the inputs, features and outputs of each model, how each selected model works, how it will be used on a day to day basis, and the performances of the models that will be served ; 
    * a live performance evaluation process before the deployment in production ; 
    * a release management process as it has been the norm with continuous delivery and DevOps ; 
    * service or interface contracts for communication with other Tiers. 
  * Log, monitor and alert. Often. Always… 
  * Test, test and test again. 
  * When relevant, use a containerized stack and rely on an infrastructure as code with continuous deployment strategies. 
  * Manage your configurations wisely, storing settings values in as few places as possible. 
  * Fix all packages versions, including dependencies. 
  * All this, keeping in mind: the simpler, the better. 



####  Processes 

Machine Learning (ML) can be tricky to apprehend and subject to misunderstandings despite high hopes in automation and performance capabilities… This is especially the case when stakeholders manage many projects concurrently with little time granted to the ML project or lack technical background to understand (by themselves) the data science concepts at stake. So, before d-day, all stakeholders should **agree on the inputs, features and outputs of each model, how each selected model works, how it will be used on a day to day basis and the performances of the model(s) that will be served** to avoid any disappointment (or worse) weeks after the “go live”. 

For instance, let’s consider a client scoring model, designed for marketing activities purposes. Months after the first score-based mailing campaign, it’s still possible that stakeholders ask about precision, recall and overall performance of the model. In this case, it would be a waste of time to re-explain the whole performance calculation process, maybe reaching the tipping point of “that’s not achieving what it was supposed to be, we shut down the project.” 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/12/machine-learning-2x.png) _You’d rather avoid this for your_ [ _machine learning_ ](https://xkcd.com/1838/) _stack._

If the project reaches the GO/NOGO step to push the model into production (or not), it must have been assessed as valuable in previous evaluations and it’ll be necessary to be able to assess the true return on investment later. Hence, all stakeholders should **agree on a live performance evaluation process before the deployment in production.** Otherwise, any decision based on whether the project is performing as expected will not be made in due form. 

Let’s consider a marketing use case for any company selling high price products (cars, luxury goods, etc.) which consists in scoring clients and pushing emails to top scored customers. The relevant performance KPIs are highly likely to be email opening or click rates rather than _n_ days conversion rate (mainly due to the high price of the products). Then, it’s better for the project that all stakeholders have agreed beforehand that the objective of the campaign was click rate and not the conversation rate otherwise, when campaign results will be shared, there will be discrepancies. 

We can also illustrate this need for **live performance evaluation** with our product recommendation use case. The process of building a recommendation engine is known for not having trivial and sometimes not relevant offline evaluation strategies. Hence, to decide whether model A is better than model B, a solution is to implement in production an **A/B testing strategy** where a percentage of users will receive recommendations from model A and the rest from model B. For the purpose of choosing which model is the best, it’s obviously necessary to be able to assess the performance of each methodology. In this case, one should **make sure that A/B(/C) model performances are compared against control group(s) performances** to decide whether those models are even performing better than no marketing action at all or standard business-driven recommendations (ex. pushing the most purchased hoodie for every one). 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/12/efficiency-2x.png) _Poor[ Efficiency ](https://xkcd.com/1445/) ? But you still have a performance evaluation process. _

Last but not least regarding the processes, all the people in the development team — data scientists, data engineers, software developers, etc. — should **agree on a release management process** as it has been the norm with continuous delivery and DevOps standards. As stated in Martin’s Fowler article [ Continuous Delivery ](https://martinfowler.com/bliki/ContinuousDelivery.html) : “Continuous Delivery just means that you are able to do frequent deployments but may choose not to do it, usually due to businesses preferring a slower rate of deployment [than with continuous development resulting in many production deployments every day]”. Hence, it seems essential to set up clear merge request processes, recurrent tests that must pass before a new release and, especially within markets with strong and specific expertise, it’s even possible to have the new pipeline outcomes verified by humans (visually checking the modeling outcomes for example). 

As an example, in a product recommendations project with high brand image constraints, business people satisfaction has been the most relevant performance metrics and the final validation step before serving the model API to end users. We had to set scenarios for the business team to apprehend what would be recommended if the client has bought such and such products and be able to give the go for a new release. For this very iterative approach, building relevant scenarios and showcasing product images have been key drivers for success. 

####  Tech 

The first of the tech tips is: **the simpler, the better** … and this is true for every step in the pipeline: from the data ingestion, to the refinement and storage; from model selection to training and serving; for the selection of 10 insightful and maintainable features rather than 100 obscure ones; for the API design and implementation; for the logging and monitoring stack management, etc… Of course, this is especially the case, if it’s your first time going into production. 

As an example, for the development of the API discussed above, we stuck to **Flask and PostgreSQL database** to retrieve, serve and store the predictions. Why? Because they are two reliable technologies, largely used within the community, easy to integrate to a containerized stack and they meet most of the requirements of such projects. This choice has proven to be a very practical approach for the development of the API and we strongly recommend to go simple before using complex services with loads of (unused) features. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2020/12/simpler.jpg)

This being said, a **containerized machine learning stack** is a very efficient way to put the whole system into production **using continuous deployment strategies** . Indeed, if one has two separated environments, replicating the exact same processes in both staging and production environments will be facilitated by dockerization and it’s even more powerful with cloud using multiple accounts and IaC (Infrastructure as Code)… the main difficulty being the simultaneous management of two or three environments. For additional reading on this topic, I would recommend the paragraph “Deployment Pipeline” of the blogpost: [ How to Build an End to End Production Grade Architecture on AWS Part 2 ](https://blog.gruntwork.io/how-to-build-an-end-to-end-production-grade-architecture-on-aws-part-2-4f6e5dc30100) . 

For the purpose of the recommendation API, the data engineering team used **Infrastructure as Code (IaC) to create and manage the services on both Dev and Prod accounts** . Building all the pipelines in the Dev account while making sure that all the services (model and API containers, databases, Jenkins and Prometheus services, etc.) have been automatically created by script without any manual change, has been a true accelerator when we have had to go into production. An example could be the quick adaptation of [ task definitions ](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html) for the containers when we had just to update several parameters to replicate the container deployment process from Dev to Prod. 

A third tech tip would be: **agree on and follow service or interface contracts for communication with other Tiers** . Indeed, when reaching agreement on precise communication rules might be a burden, it simplifies processes, prevents failures and makes error management easier because one knows what to expect from others (a clear logging will be key). Doing so, one might prefer to keep the interface contract easily accessible and accessible since it’ll drive further developments and discussions with tech partners. Eventually, one would rather test and validate as soon as possible the communication between Tiers to make sure everyone complies with the interface rules, preventing any waste of time few days before pushing everything into production. 

Illustrating this point with a project exposing a ML model through a classic REST API. The “key-value” body of the requests included required information for the recovery of a prediction and during QA tests we were not able to communicate… Digging to understand why, we found out that, when on the interface contract the client identification was supposed to be “client_id”, our counterpart went for “client” in their developments… so we could not catch the upcoming messages in the Kafka queue. **Testing the interface contract beforehand** would have saved us some precious time during QA tests. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2021/03/misinterpretation.png)

_[ Communication ](https://xkcd.com/1445/) involves at least two persons _

**Log, monitor and alert. Often. Always…** Logs are the only qualitative feedback one has on the automated processes that run in the background, metrics allow fast quantitative insights on the whole stack and alerts push notifications when necessary. For example, one can set up metrics to store and retrieve easily the number of API calls, additional rows in the client database after the data ingestion process — convenient for automated client scoring projects, or the number of errors in the model (re)training process which is useful to set up alerts if the training has failed. Regarding the implementation, using the [ ELK ](https://www.elastic.co/what-is/elk-stack) or [ EFK ](https://medium.com/faun/logging-architectures-efk-stack-and-kubernetes-6c3f4d940775) stack to manage logs has been really helpful and convenient to store and retrieve logs with Elasticsearch or visualize logs and create search queries in Kibana. 

As time goes by, while logging is important but one might get used to seeing “logging.info” and even “logging.warning” for a recurrent wroing import (it’s working though, no problem) in the daily ETL pipeline. Worse, developers might no more read DAG logs every morning (that’s pretty expected) and even **not pay attention to lost in the crowd true warning logs** … That’s when you need an alerting stack. 

Let’s illustrate **alerting capabilities** . Tech wise, we used a Prometheus server to manage the monitoring and alerting stack. If any metric would exceed a defined threshold, it would trigger an alert 
