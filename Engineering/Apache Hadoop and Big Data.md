# Apache Hadoop and Big Data

## What is Big Data?

### 3 V's: Volume, Velocity and Variety

#### Volume

"Big" is a relative term. We put Shaq next to almost everyone, but especially gymnast Simone Biles, and he looks enormous.
But if he stands with Yao Ming ... suddenly he doesn't look so big.

<p float="left">
    <img src="https://pbs.twimg.com/media/C37lYkiVMAAiFwu?format=jpg&name=medium" width="300"> 
    <img src="https://i.insider.com/5437f6b6ecad04cc2be71697?width=1000&format=jpeg&auto=webp#right" width="300">
</p>

The same applies to data. What is considered as "Big"? 10GB? 100GB? Or 100TB? There is no straight number that define big data.
There is two reasons why there is no straightforward answer to this question:
- What is considered as big today, in term of data size/volume, need to be considered as big a year from now. This is a moving target.
- It's all relative, shown in Shaq's photos. What we consider to be big may not be the case for companies like Google and Facebook.

Hence, For these two reasons, it's very hard to put a number to define Big Data volume.

Let's say if we are defining big data problems in terms of pure Volume alone. In our opinion, 100GB is not big data since we have hard disk greater 100GB. How about 1TB? It is still no because a well-defined traditional database can handle 1TB or even more without any issue. 
Then, 100TB? Some would claim that 100TB to be a big data problem and others might disagree, it is relative! So, 1000TB? Now, this is in scale of Petabytes, it definitely Big Data.

#### Velocity

We have to undertand that Volume of data is not the only factor to classify our data to be big data or not.
Let's say we work at a start-up and we recently launch a very successful email service where user can log in to send and receive emails.
Our email service is so good and even better than Gmail. In three months, we have 100 thousands active users signed up on using our service.

Hypothetically, we currently using a traditional database to store messages and its attachments and also our current size of the databse is 1TB. 
So, do we have a big data problem? The straightforward answer is NO because 1TB is not that big to classify as a big data problem. 
Another question: in this growth rate, will we have a big data problem in the near future? To answer this, we need to consider three factors.

The first one is Volume. In 3 months, our start-up has 100 thousands active users and our volume is 1TB. 
If we have positive growth as the same rate, we will have 400 thousands active users at the end of the year and our volume will be 4TB.
What if we doubled or tripled our user base every 3 months, so the bottom line is that we should not just look at the volume when we think of Big Data.
We should look at the rate in which our data grows. In other words, we should watch the velocity or speed of our data growth. 

Velocity is the next important factor to consider, it tells us how fast our data is growing. 
If your data volume stays at 1TB for a year, all we need is a good database. 
If your growth rate is 1TB/week then you have to think about a scalable Big Data solution.
Most of the time, Volume and Velocity are all you need to decide whether you have a Big Data problem or not. 

#### Variety

This is the next factor we need to consider, it adds one more dimension.
Our data and traditional database are highly structred that is rows and columns.
Back to our hypothetically start-up email service, it receives data in various formats: texts for the actual messages, images and videos as attachments. 
When we have data coming to our system in different formats and have to process or analyze the data in different formats, tradiational database systems are sure to fit.
When combined with high volume and velocity, you are for sure have a big data problem.

Therfore, whenever we are asked whether it is a big data problem or not, please take the 3 V's: Volume, Velocity and Variety into consideration.
This happends to Big Data consultants all the time, they will be called in by clients about data storage which has performace issues and hope that a Big Data solution like Hadoop is going to solve their problem.
Most of the time, their answer will fail in the volume and velocity tests, the volume will be in the higher gigabytes or lower gigabytes and their growth rate is relatively low for the past six months and in the foreseable future. Hence, the Volume does not qualify as big data and their data growth rate will be very low. It fails the velocity test as well.
What the client's needs is to optimize the existing process and not a sophisticated Big Data solution.

### Usecases

When we say Big Data, we are potentially talking about hundreds to thousands of Terabytes. Let's consider the following domains' usecases:

#### Science

Large Hadron Collider at SUN produces about 1TB of data every second, mostly sensor data from their equipments. 
Their volume is so big, they don't even retain or store all the data they produce.

NASA gathers about 1.73 GB of data every hour about whether geolocation data from satelites, etc. 

#### Goverment

NSA (National Security Agency) is known for its controversial data collection programs. A NSA data center at Utah can house 1 Yottabytes (1 trillion terabytes) of data in terms of Volume.

In March 2012, Obama's adminitration announced about 200 millions dollars in Big Data initiatives. We can understand the signification behind Big Data and its analysis even through we cannot technically classify the next one under a goverment. And Obama's 2nd term election campaign used Big Data analytics which gave them a Competitive Edge to actually win the election.

#### Private

In the advent of social media like Facebook, Twitter, LinkedIn, etc., there is no scarcity of data: eBay is known to have a 40 Petabyte cluster and Facebook a 30 Petabyte cluster. These numbers are old now since the stats are a little old big data. 

Data is not only produced and analyzed in social media companies but also retail space. It is most common in several major retail websites to capture click-stream data. For example, you shop at amazon.com. 
Amazon is not only capturing data when you click checkout but also every click on their website which is tracked to bring a personalized shopping experience. When Amazon shows you recommendations, Big Data analytics are at work behind the scenes.

### Big Data Challenges

Big Data comes with big problems:

- Since data sets are huge, we need to find a way to store them as efficent as possible. It is not just about efficiency in terms of **__storage__** space but also efficiciency in storing the data set that is suitable for **__computation__**. The main purpose of storing data is to analyze them, right? How much time does it take to analyze and provide a solution to a problem using our big data? What's good in storing the data when you cannot analyze or process the data in reasonable time? With big data set, computation with reasonable execution times is a challenge

- Another problem when we deal with big data set is about **__data loss__** due to corruption and data or due to hardware failure. You need to have a proper recover strategies in place.

- Finally, the **__cost__** and the most important challenge you're going to need a lot of storage space and a lot of computational power. Therefore, the solution that you plan to use should be cost effective.

### Traditional Solutions

#### RDBMS

Traditional RDBMS will have scalability issues when moving up in data volume in term of Terabytes. 
We will be forced to demormalize and pre-aggregate the data for faster query execution time.
As the data get bigger, we will be forced to make changes to the process in terms of changing the indexes, optimizing the queries, etc.
Asuming that your database is running with enough hardware resources, when you see a performance issue, you still have to make  changes to the query itself or the way in which your data is accessed. 
There is no working arround it. You cannot add more hardware resources or more computer nodes and distribute the problem to bring the computation time down. 
In other words, database is not horizontally scalable, i.e. you cannot add more resources or more computation nodes and hope the execution time or the performance will improve. 

Databases are designed to process structured data. When our data does not have a proper structure, the database will struggle. Furthermore, a database is not a good choice when you have variaty of data which is data in serveral formats like texts, images, videos, etc. 

A good enterprise grade database solution can be quite expensive for relatively low volume of data. When you add hardware costs and platium grade storage costs.
It's going to be quite expensive

#### Grid Computing - A distributed computation solution

Grid computing are essentially many nodes operating on data paralelly and then does faster computation. However, there are two challenges:

- Grid or high performance computing is good for computing intensive tasks with relatively low volume of data but does not perform well when the data volume is huge.
- Grid computing requires a good experience with lower level programming to implement and then it is not suitable for mainstream. 

### Hadoop - A good solution

 A good solution should, of course, handle huge volume of data. It should provide efficient storeage that is the ability to store data efficiently.
 Data loss is unavoidable, so the proposed solution should implement good recovery strategy. And the solution should horizontally scalable as your data grows. Most importantly, it should be cost effective. Finally, minimizing the learning curve, it should be easy for programmers, data analysts and non-programmers to work with the framework or the system. This is exactly what Hadoop offers.

 #### Is Hadoop a replacement for RDBMS?

 NO!

| Hadoop      | RDBMS |
| ----------- | ----------- |
| Hadoop has the volume in term of petabytes       | RDBMS work exceptional well with volume in low terabytes   |
| Hadoop can work with Dynamic Schema and supports files in many different formats   | The schema is very strict and not so flexible and cannot handle multiple formats     |
| Hadoop solution can scale horizontally  | RDBMS's solution can scale vertically, meaning we can add more resources to the existing solution and to make any improvements to the process itself like tuning the queries and adding more indexes, etc.|
| Hadoop offers cost-effective solution  | It gets expensive very quickly when we increase the volume of data  |
| Hadoop is a batch processing system, so we cannot expect millisecond response time like an interactive system | RDBMS is an interactive and batch system |
| We can write the file or data once and then operate or analyze data multiple times| we can read and write multiple times |

The gaps between Hadoop and RDBMS are closing in. Hadoop offers a cost-effective solution to big data problem but Hadoop is not the only solution that is available in the market now. NoSQL databases like HBase and Cassandra bring a great deal of value in analyzing huge volume of data and it is a great alternative for RDBMS. Now, when we metion about huge volume of data, we are talking about milions of columns and bilions of rows.

## Understanding Big Data Problem

## History of Hadoop