# System Design

[﻿www.tryexponent.com/blog/system-design-interview-guide](https://www.tryexponent.com/blog/system-design-interview-guide) 

## Problem Statement
- [ ] functional
- [ ] non functional
    - [ ] availability
    - [ ] maintainability
    - [ ] performance - How fast is the system
    - [ ] scalability - How will the system respond to the increased demand ?
    - [ ] reliability - What is the systems uptime ?
    - [ ] resilience - how will the system recover if it fails ?
    - [ ] security -  how are systems and the data protected ?
    - [ ] usability - how will the users interact with the system ?
    - [ ] Localizations - Will the system handle currencies and localizations ?
- [ ] Questions to be asked
    - [ ] What is the scale of the system ?
    - [ ] How many users per day ?
    - [ ] How many requests should the server handle ?
    - [ ] Are the users on mobile device ?
- [ ] assumptions
- [ ] users
## High level system design
- [ ] Define the core components
- [ ] capacity Estimation
    - [ ] 1 MB = 10^6 bytes = 1 mi
    - [ ] 1 GB = 1000 MB = 10^9 bytes = 1 bi
    - [ ] 1 TB = 1000 GB = 10^12 bytes = 1 Tri
    - [ ] 1 PB = 1000 TB = 10^15 bytes = 1 Quadrillion
- [ ] api/ contract
    - [ ] request
        - [ ] REST - Representational State Transfer
        - [ ] SOAP - Simple Object Access Protocol
            - [ ] high security
            - [ ] enables strict comliance
        - [ ] RPC - Remote Procedure Call
            - [ ] binary data for lightweight communication
            - [ ] protocol buffers (google)
        - [ ] GraphQL
            - [ ] strongly type
            - [ ] single endpoint
            - [ ] can fetch multiple resources using query language.
        - [ ] Web Sockets
            - [ ] bi-directional communication
    - [ ] response
    - [ ] Server and client communication
        - [ ] Ajax Polling
        - [ ] Long Polling
        - [ ] WebSockets
        - [ ] Server-Sent Events (Push)
- [ ] Data Modelling
    - [ ] schema
    - [ ] relational / non relational database
        - [ ] AWS
            - [ ] SQL - RDS
            - [ ] No SQL - DynamoDB
            - [ ] Bolb - S3
            - [ ] Redis - in memory cache
- [ ] non-functional requirements
    - [ ] Transaction - ACID
    - [ ] data ingestion
    - [ ] offline processing - queues
## Deep dive into the design 
## System scalability
- [ ] single point of failure
- [ ] horizontal/ vertical scaling
- [ ] performance
- [ ] CDN/ Caching/ SQL-No-sql
## Review and Wrap up


# Calculate the Storage capacity for 1.6 Billion  products:
1 Product = 50 MB (metadata + artifact) 

= 1.6 * 10^9

= 1.6 _ 10^9 _ _ 50  * _10^6 = 2 * _10^9  50 _ 10^6

= 100 * 10^15

= 100 PB of storage

# 1 Million active users / day to / sec:
 = 1 * _ 10^6 / (24   60  _ 60)

= 10^6 / (24 * 3600)

 = 10^6 / ~( 25 * 4000)

=  10^6 / ~( 100000)

= 10 active user/ sec

# Fundamental concepts
- [ ] _**Web Protocols**_
    - [ ] TCP - 
        - [ ] Reliable transmission. 
        - [ ] more data accuracy
            - [ ] HTTP - Application layer protocol
                - [ ] transfer content using request/ response
            - [ ] HTTPS
                - [ ] data encryption
            - [ ] TLS (Transport Layer security)
                - [ ] Encrypts data to secure communication
    - [ ] UDP - 
        - [ ] Faster 
        - [ ] no accuracy
        - [ ] used in live streaming
    - [ ] WebSockets
        - [ ] real time data transfer
        - [ ] bidirectional communication
- [ ] _**Design Consideration**_
    - [ ] Pagination
- [ ] _**API security and management**_
    - [ ] manage authentication
        - [ ] Session based - stateful
        - [ ] JWT - stateless
    - [ ] rate limiting
- [ ] _**Site Reliability**_ (SLA)- measures for security, error management, disaster recovery
    - [ ] system functions correctly
    - [ ] handles errors
    - [ ] secures unauthorized access
    - [ ] A reliable system incorporate strategies to manage hardware and network failures effectively. 
        - [ ] graceful recovery from failures
        - [ ] testing and monitoring
    - [ ] Retries
        - [ ] simple retires
        - [ ] delayed retries and exponential backoff
    - [ ] Circuit breakers
        - [ ] useful for avoiding cascading failures
    - [ ] Saga
        - [ ] manages distributed transactions in microservices by ensuring each component transaction completes successfully or compensatory actions are taken.
- [ ] _**Availablity**_
- [ ] _**Rate Limiting**_
    - [ ] controls the system calls within a specified time.
    - [ ] helps in managing the system load and reducing unnecessary costs
        - [ ] Token bucket - limit the no. of tokens per request
        - [ ] Leaky bucket - discard excess requests when capacity is reached.
- [ ] _**Queue based loading leveling**_
    - [ ] makes the system async
    - [ ] moderates the flow of services, preventing system overload.
- [ ] _**Gateway Aggregating**_
    - [ ] reduces multiple service requests into a single operation at gateway level, improving efficiency and reducing the load on backend services.
- [ ] _**Load Balancers**_
    - [ ] distribute the network traffic across multiple services. This mechanism enhances application scalability, increases availability and optimizes server capacity usage.
    - [ ] supports horizontal scaling
        - [ ] Round Robin - assigns the server in cyclic order.
        - [ ] Least connection - directs the request to the fewer active connections.
        - [ ] hashing
        - [ ] Advantages
            - [x] scalability - facilitates easy scaling of application servers as demand changes
            - [x] reliability - enhances system reliability by providing failover capabilities 
            - [x] performance - improves response times by evenly distributing workloads.
        - [ ] Cons
            - [ ] maintaining user sessions across different servers
            - [ ] deploying updates may be challenging
- [ ] _**SQL vs. No SQL Databases**_
    - [ ] SQL Databases
        - [ ] Relational
        - [ ] Structured
        - [ ] ACID compliance
        - [ ] `less flexible` 
        - [ ] `scaling challenges - more suitable for vertical scaling.` 
        - [ ] MySQL, PostgresSQL, CoakroachDB
    - [ ] No SQL
        - [ ] flexible
        - [ ] non structured
        - [ ] document based
        - [ ] supports horizontal scaling
        - [ ] diverse data types support
        - [ ] `can lead to stale data reads in distributed setups.` 
        - [ ] `not ideal for applications requiring complex transactional integrity` 
        - [ ] MongoDB, DynamoDB
- [ ] _**Database Sharding**_
    - [ ] dividing large database into smaller, more manageable pieces, known as shards, each hosted on separate servers.
    - [ ] connected through the shard key
    - [ ] supports scalability, performance and maintainability
        - [ ] geo based sharding 
        - [ ] hash based sharding
        - [ ] `can lead to complex query to retrieve data` 
- [ ] _**Database Replication**_
    - [ ] process of copying data from one database to one or more databases.
    - [ ] its essential in distributed systems where data is stored across multiple nodes. It ensures data availability and integrity, reduces latency, and increases system resilience against network or hardware failures.
    - [ ] **Master/ Slave patterns**
- [ ] _**CAP Therom**_
    - [ ] 
- [ ] _**Asynchronous Processing**_
    - [ ] enables parallelism
    - [ ] useful where operations might be resource-intensive or time-consuming.
    - [ ] Implemented using the framework MapReduce, where tasks are divided and processed in parallel.
        - [ ] Message Queue - Taskrabbit/ Kafka
        - [ ] Pub/Sub
- [ ] _**Caching**_
    - [ ] store data close to the usage points
    - [ ] in-memory cache
    - [ ] distributed cache
        - [ ] shares cache across servers - Memcached, Redis
    - [ ] database cache
    - [ ] file system cache
    - [ ] Cache policies
        - [ ] FIFO
        - [ ] LRU
- [ ] _**Encryption**_
    - [ ] Symmetric - Use the same key for encryption and decryption, efficient but requires secure key handling
    - [ ] Asymmetric - Use public key encryption and private key for decryption, enhancing security but slower.
- [ ] _**Authentication & Authorization**_
    - [ ] Authentication verifies user identity through username and password
        - [ ] single factor
        - [ ] multi factor
    - [ ] Authorization determines user access levels.
        - [ ] role based access
        - [ ] attribute bases access
    - [ ] Oauth 2
    - [ ] JWT
    - [ ] Cookie based
- [ ] _**Cloud Architecture**_
    - [ ] AWS
        - [ ] Cloud Front
        - [ ] S3
        - [ ] API Gateway
        - [ ] Elastic Load Balancer
        - [ ] Lambda
        - [ ] Message Queue
        - [ ] RDS
        - [ ] DynamoDB
    - [ ] Orchestration Services
        - [ ] Terraform - manages physical infra, utilizes infra as code
        - [ ] Kubernetes - manages container-based applications, automating complex, scalable deployments.
- [ ] _**CDNs**_
    - [ ] network of servers globally distributed to deliver static content like images, videos and web scripts.
    - [ ] content cached near to the users
    - [ ] popular CDNs
        - [ ] Cloudfare
        - [ ] AWS Cloudfront
# Ecommerce application


## Non-functional requirement
- [ ] Low Latency (Recommendation & Search)
- [ ] High Consistency (Placing order, order status and payments)
# Web Crawler
- [ ] Bots driven
- [ ] Build the Search Index
- [ ] Train the ML models


## functional requirement
- [ ] Crawling
- [ ] Crawl HTML
- [ ] 
## non-functional requirement
- [ ] rate limiting - should not be making too many requests
- [ ] API
```
﻿resolveDNS(url) -> IpAddress
downLoadPage(ip) -> Data
downloadPage(url) -> Data 
```
- [ ] Capacity Estimation
```
Total 1.13 Billion websites
20% are actively maintained
= 20% of 1.13 * 10^9
= 20 / 100 * 100 * 10^9 / 100
= 20 * 1 * 10^7
= 200 Million

1 website can have multiple pages
Average pages per website = 100

Total pages we need to crawl
= 100 * 200 M
= 20 Billion web pages

Size estimation

except for the images/ video, 
the size of the web page = 100KB

Total storage perquired 
= 100 * 10^3 * 20 * 10^9
= 2 PB of storage
```
![image.png](https://eraser.imgix.net/workspaces/wWBAvtKNB17aN5VNXFOi/h1gbXWDNGTTMYPk56Hw4kcyHCLL2/C9nbtAqsv9sOnuQrSP4gX.png?ixlib=js-3.7.0 "image.png")

DNS resolver to resolve the IP address from the url is a 3 step process

- [ ] We can cache the URL -> IP address
- [ ] 


# Netflix
## Functional Requirement
- [ ] Users to upload the video
- [ ] Search
- [ ] Play the video
- [ ] Recommendation
### Assumptions
- [ ] User service is provided
## non-Functional Requirement
- [ ] Low Latency
- [ ] High Availability
- [ ] Consistency can be okay to compromise
    - [ ] there could be a delay in video uploaded vs streamed.
### Capacity Estimation
```
DAU: 100M users * 2 times a day
QPS = 100M * 2 times a day (24 * 60 * 60)
 = (100 * 10^6) / (24 * 3600))
 = 100 * 10^6 / (25 * 4000)
 = 100 * 10^6 / 10^5
 = 1000 queries/ sec
 
 
 Storage
 10:1 viewres: creators
 100M viewers -> 10 M creators
 two times a week
 Each video = 5GB
 
 Storage capacity
 10 M creators * 2 times/ week * 5GB of video
 = 10 * 10^6 * 2 times * 4 weeks * 12 months * 5 GB
 = 10 * 10^6 * 100 * 5 * 10^9
 = 5000 * 10^15
 5000PB per year
```
## Database design
```
Video -> Blob storage

Video Metadata { // SQL database
  videoId: PK
  userID: FK
  DTTM: DataTime
  Visibility: 
  description
  title
  categories
}
```
video needs to be transcoding to create the HLS stream to support for adaptive bit rate streaming.

ffmeg -> video -> master playlist and sub playlist 

- [ ] Master playlist m3u8 that will support multiple redemption
- [ ] sub playlist have the info of the video segments with time stamps
- [ ] .ts file is the actual video segments
```
User {
  userId: PK
  username: String
  firstname
  lastname
  creatingData: datatime
  lastLogin: datatime
}
```
## API design
```
uploadServive(file) POST -> Success, error
recomemdedVideo(userId, pagination) GET -> [Video], Error
```




![image.png](https://eraser.imgix.net/workspaces/wWBAvtKNB17aN5VNXFOi/h1gbXWDNGTTMYPk56Hw4kcyHCLL2/LwaKKHp9jxDiD6bv3UIJS.png?ixlib=js-3.7.0 "image.png")





# Tiny URL
## Functional Requirement
- [ ] Create a short url
- [ ] redirect the url
### Capacity Estimation
```
// Scale of the application

1000 urls generated / second
= 1000 * 60 * 60 * 24 * 365
= 1000 * (3600 * 24) * ~400
= 1000 * ~(4000 * 25) * ~400
= 1000 * 10^5 * 400
= 40 * 10 ^ 9
= 40 Billion urls / year

reads to write urls per year, 10:1
400 Billion urls/ year

// What characters can we use
a - z = 26
A- Z = 26
0 - 9 = 10
total 62 characetrs

// How many unique urls can we create
for 1 character ; 1*62 = 62
for 2 characters ;  62 * 62 = 3844

for  6 characters = 62 ^6 = 56 billion
for 7 characters = 7.5 trillion

we cna go with the 7 characters

// storage capacity
1 url = 7 characters = 7 bytes
Total 500 bytes for 1 url

500 bytes * 400 B urls = 20 * 10^4 * 10*9 = .2 PB



```
## nonFunctional Requirement
- [ ] low latency


## API DEsign
```
/create-url(long-url) POST 201 OK/ Error
/{short-url} GET 301 permanent redirect
```
## Database Design
```
urlID: String
long-url: String
short-url: String
cratedAt: DateTime

```
![image.png](https://eraser.imgix.net/workspaces/wWBAvtKNB17aN5VNXFOi/h1gbXWDNGTTMYPk56Hw4kcyHCLL2/E1MLKktTB6hceKFLq75kt.png?ixlib=js-3.7.0 "image.png")

Analytics

IP address to re distibute the cache / location

Rate limiting

security consideration



# Site Reliability Engineering
## What is SRE ?
- [ ] Reliability is to keep the system running 99.99% of the time.
- [ ] 
## What is SLA ?
- [ ] Service Legal Agreement
- [ ] business and engineers defines the SLA
## Monitoring, Logging & Alerting
- [ ] Errors with the service informations on a cluster
- [ ] On-Call support
- [ ] Logs and Alert messages
- [ ] Outage happens when multiple things go wrong
- [ ]  Postmorten
    - [ ] A through analysis
    - [ ] stay blameless
    - [ ] document everything for future reference
## SRE Tools ?
- [ ] Github
- [ ] Visual Studio Code
- [ ] The cloud
- [ ] Jira/ Confluence
- [ ] draw.io
- [ ] Python
- [ ] Terraform - Infrastructure as code.
- [ ] CI/ CD
    - [ ] Jenkins
    - [ ] Github Actions
- [ ] Observability
    - [ ] Datadog
    - [ ] Grafana
    - [ ] 
## Grafana/ Prometheus/ Loki
- [ ] Central Monitoring system
    - [ ] Metrics - Promethus client for log collection
        - [ ] CPU usage
        - [ ] RAM
        - [ ] Utilization
        - [ ] /metrics - send the data collected
    - [ ] Log Collections
        - [ ] Loki


