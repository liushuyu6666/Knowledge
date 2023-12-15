- [Concepts](#concepts)
  - [Vertical Scaling vs Horizontal Scaling](#vertical-scaling-vs-horizontal-scaling)
    - [Advantages:](#advantages)
    - [Disadvantages](#disadvantages)
    - [Advantages](#advantages-1)
    - [Disadvantages](#disadvantages-1)
- [Network infrastructure components](#network-infrastructure-components)
  - [Reverse Proxy](#reverse-proxy)
    - [Features](#features)
  - [Load Balancer](#load-balancer)
    - [Features](#features-1)
  - [API Gateway](#api-gateway)
  - [Content Delivery Server (CDS)](#content-delivery-server-cds)
- [Application layer protocol:](#application-layer-protocol)
  - [HTTP](#http)
  - [HTTPS](#https)
  - [websocket](#websocket)
- [API pattern:](#api-pattern)
- [ACID of relational database](#acid-of-relational-database)
  - [Atomicity](#atomicity)
  - [Consistency](#consistency)
  - [Isolation](#isolation)
  - [Durability](#durability)
- [Sharding and Replication](#sharding-and-replication)
  - [Sharding](#sharding)
  - [Replication](#replication)
  - [Leader and Follower Replication](#leader-and-follower-replication)
- [Scalability](#scalability)
- [Bugs](#bugs)
  - [Sentry and Logger with AWS cloudwatch](#sentry-and-logger-with-aws-cloudwatch)
- [How website works](#how-website-works)
- [SQL vs noSQL](#sql-vs-nosql)
  - [SQL](#sql)
- [Reactjs](#reactjs)
  - [Virtual DOM](#virtual-dom)
- [SPA vs MPA](#spa-vs-mpa)
  - [SPA](#spa)
  - [MPA](#mpa)
- [Static application vs dynamic application](#static-application-vs-dynamic-application)
- [HTTP method](#http-method)
  - [POST vs PUT](#post-vs-put)
- [CAP theorem](#cap-theorem)


# Concepts
## Vertical Scaling vs Horizontal Scaling
Vertical scaling: Vertical scaling involves increasing the capacity of a single machine or server by adding more resources to it. If you have a single server with 4 CPU cores and 16 GB of RAM, you might vertically scale by upgrading to a server with 8 CPU cores and 32 GB of RAM.

### Advantages:
simple

### Disadvantages
1. Limited scalability: There is a physical limit to how much a single machine can be scaled vertically.
2. Cost: The cost of high-end hardware can be expensive.
3. Downtime: Vertical scaling may require downtime during upgrades.

Horizontal Scaling:
Horizontal scaling involves adding more machines or nodes to a system.

### Advantages
1. Scalability: Easier to scale horizontally by adding more machines.
2. Cost-effective: Can often be more cost-effective than continually upgrading a single machine.
3. Redundancy: Distributed systems can provide better fault tolerance and redundancy.

### Disadvantages
1. complexity
2. potential communication cost

# Network infrastructure components
## Reverse Proxy
A reverse proxy is a server that sits between client devices and a web server, forwarding client requests to the web server and returning the server's responses to clients. 
### Features
1. load balancing:  
2. SSL termination: Handles Secure Sockets Layer (SSL) encryption and decryption
3. caching: Stores and serves static content (like images, stylesheets, and scripts)
4. health monitor
5. Web Application Firewall (WAF)
6. content rewrite

## Load Balancer
distribute incoming network traffic across multiple servers to ensure no single server bears too much load.

### Features
1. load balancing
2. SSL Termination
3. Global Server Load Balancing (GSLB)
4. Content-Based Routing
5. health monitor
5. Web Application Firewall (WAF)
6. Scalability: Content delivery systems are designed to scale horizontally, meaning that additional servers can be easily added to the network to handle increased traffic or demand.

The Algorithm the Load balancer use: Round Robin or Hashing.

## API Gateway
1. load balancing
2. Authentication & Authorization
3. Request and Response Transformation: Modifies or transforms API requests and responses to bridge differences in data formats, versions, or structures between clients and backend services.
4. caching
5. logging & monitoring
6. Web Application Firewall (WAF):

## Content Delivery Server (CDS)
1. Load Balancing
2. CDN: Geographically distributed
3. caching: Content delivery servers often implement caching mechanisms to store copies of frequently requested content closer to the end-users.
4. Security and DDoS protection
5. Scalability: Content delivery systems are designed to scale horizontally, meaning that additional servers can be easily added to the network to handle increased traffic or demand.

# Application layer protocol:
## HTTP
## HTTPS
## websocket
1. Full-Duplex Communication:
Unlike traditional web communication, which is typically request-response based, WebSocket enables bidirectional communication. Both the client and server can send messages to each other independently over the same connection.

2. Persistent Connection:
WebSocket establishes a persistent connection between the client and the server. This connection remains open, allowing for real-time data exchange without the overhead of repeatedly opening and closing connections for each interaction.


# API pattern:
1. RESTful
2. Graph QL
3. gRPC


# ACID of relational database
## Atomicity
Ensure the transaction is committed completely, if any part of the transaction fails, the entire transaction is rolled back to its original state.
## Consistency
The database should always obey constraints and business rules. If a transaction violates the consistency rules, it is rolled back.
## Isolation
Isolation ensures that multiple transactions can be executed concurrently without interfering with each other.
## Durability
Ensure that once the transaction is committed, it will be permanently stored.

# Sharding and Replication
## Sharding
A large dataset is divided into smaller, more manageable parts called shards. Each shard is an independent database that can be located on a separate server or node.

## Replication
Replication involves creating and maintaining multiple copies of the same dataset on different servers.

## Leader and Follower Replication
Leader: This server is responsible for receiving write operations (inserts, updates, deletes) and then propagating those changes to one or more follower servers.
Follower:
1. replicate the changes made by the leader.
2. handle read queries
3. synchronize their data with the leader

# Scalability
1. Horizontal Scaling
2. Vertical Scaling
3. Caching
4. Database Scaling
   1. sharding
   2. replication
5. Asynchronous Processing
   1. background processes
   2. message queues ??
6. Distributed Architecture
   1. microservices
7. Auto Scaling: like AWS Lambda

# Bugs
1. Understand the bug: Gather information and reproduce the issue.
2. pinpoint the bug: Identify the affected component or module.
3. Use debugging techniques: Employ logging, breakpoints, and debugging tools.
4. Analyze the code: Review relevant sections, dependencies, and edge cases.
5. Fix the bug: Develop a plan, make code changes, and write tests.
6. Test and verify: Conduct thorough testing and regression testing.
7. Document and communicate: Document the bug and resolution, share findings with the team.

## Sentry and Logger with AWS cloudwatch
To use Sentry and a logger (such as Winston or Bunyan) with AWS CloudWatch, you can set up a logging pipeline that sends your application logs and error events to CloudWatch Logs. Here's an overview of the steps involved:

1. Set up AWS CloudWatch:
Create an AWS account and navigate to the CloudWatch service.
Set up a new CloudWatch Logs group and log stream to receive your application logs.
Integrate Sentry for Error Monitoring:

2. Install the Sentry SDK in your Node.js application using npm or yarn.
Configure the Sentry SDK with your Sentry project's DSN (Data Source Name).
Capture and report errors using Sentry's provided functions and middleware.
Integrate a Logger Library:

3. Choose a logger library like Winston or Bunyan and install it in your Node.js application.
Configure the logger to write logs to both Sentry and CloudWatch Logs.
Set up log formatting and levels according to your requirements.
Configure the CloudWatch Logs Agent:

4. Install and configure the CloudWatch Logs Agent on your server or EC2 instance where your application is running.
Configure the agent to monitor log files and stream them to the appropriate CloudWatch Logs group.
Log Forwarding to CloudWatch Logs:

5. Configure your logger library to write logs to a log file.
Set up log forwarding from the log file to CloudWatch Logs using the CloudWatch Logs Agent.
Monitor and Analyze Logs:

6. Access the CloudWatch Logs console to view and analyze your application logs.
Utilize CloudWatch features like log search, filtering, and metric extraction for log analysis.

# How website works
1. Domain Name System (DNS) Resolution:
   * You enter the website's domain name (e.g., www.example.com) in your browser.
   * The browser sends a DNS request to a DNS server to resolve the domain name into an IP address.
   * The DNS server responds with the IP address of the website's server.


2. Establishing a Connection:
   * The browser initiates a TCP/IP connection with the website's server using the obtained IP address and a specified port (typically port 80 for HTTP or port 443 for HTTPS).
   * The server listens for incoming connections and responds to the browser's request.

3. HTTP Request and Response:
   * The browser sends an HTTP request to the server, including information such as the request method (e.g., GET, POST), requested resources (e.g., URL path, query parameters), and additional headers.
   * The server receives the request, processes it, and generates an HTTP response.
   * The response contains status codes (e.g., 200 for successful response, 404 for not found), headers (e.g., content type, caching instructions), and the requested content.
   * Even for a single-page website where the frontend and backend are isolated, the browser still needs to send an HTTP request to retrieve the HTML file that serves as the entry point for the frontend.

4. Content Generation:
   * The server may dynamically generate the content requested by executing code (e.g., server-side scripting, database queries) or retrieve pre-existing files/resources.
   * The server prepares the response by assembling the content, applying any necessary data processing, and generating the appropriate headers and metadata.

5. Content Delivery:
   * The server sends the generated HTTP response back to the browser over the established TCP/IP connection.
   * The response travels through the network infrastructure, potentially passing through multiple routers and switches.

6. Rendering in the Browser:
   * The browser receives the response and begins processing it.
   * It parses the HTML content to construct the Document Object Model (DOM) representing the webpage's structure.
   * The browser processes CSS stylesheets and applies the visual styles to the DOM elements.
   * If the response includes JavaScript, the browser executes the scripts, enabling dynamic functionality and interaction.
   * The rendered webpage is displayed in the browser, combining HTML, CSS, and JavaScript to present the visual interface and interactive elements.

# SQL vs noSQL
1. Structure: predefined schema (SQL), schema-less (noSQL)
2. Data Integrity: ACID (SQL),
3. Language: SQL vs more flexible querying (key-based lookups, document-based, graph traversal)
4. Scalability: SQL provide vertical and horizontal scalability, NoSQL are designed for horizontal scalability, they can easily scale by adding more servers.

## SQL
SQL is good at 
1. complex queries (such as calculating averages, grouping by departments and filtering based on date ranges), aggregation and join tables. 
2. Consistency
    example: Imagine a banking system where you have two related tables: `Accounts` and `Transactions`. Each account has a balance stored in the `Accounts` table, and transactions related to those accounts are stored in the `Transactions` table. To maintain consistency, the database should enforce the following constraints:
      - Balance Constraint: The sum of all transaction amounts associated with an account should equal the account's current balance.
      - Referential Integrity: The foreign key relationship between the Transactions table and the Accounts table should be maintained. Every transaction should be associated with a valid account.
    Now, let's consider a scenario where a transaction is being processed:
      1. A user initiates a withdrawal transaction from Account A with a certain amount.
      2. The database begins the transaction, ensuring that no other concurrent transactions interfere with this one by locking the row in `Account` table. (row-level lock)
      3. The system checks if Account A has sufficient balance for the withdrawal. If the balance is sufficient, the transaction proceeds; otherwise, it is rolled back.
      4. The transaction deducts the withdrawal amount from Account A's balance in the Accounts table and inserts a new record in the Transactions table.
      5. After completing the transaction, the database commits the changes, making them permanent.


# Reactjs

## Virtual DOM
Once the virtual DOM is updated, ReactJS performs a process called reconciliation, where it compares the previous virtual DOM with the updated virtual DOM. During this process, ReactJS efficiently determines the minimal set of changes needed to be made to the real DOM to reflect the changes in the virtual DOM.

After the reconciliation process, ReactJS applies only the necessary updates to the real DOM, known as "diffing." This optimized approach minimizes the number of manipulations required on the actual DOM, resulting in better performance compared to directly updating the entire DOM structure.


# SPA vs MPA
## SPA
each request -> fetch data from server and re-render the current page

## MPA
each request -> loading of a new page from the server.

SPAs are suitable for complex applications that require real-time updates, interactivity, and a more dynamic user experience. Static applications are a good fit for content-focused sites, blogs, or scenarios where simplicity, performance, and security are the primary concerns. MPAs follow a page-centric architecture, where each page represents a distinct HTML document with its own set of styles, scripts, and content. Each page typically corresponds to a specific functionality or view within the application.

# Static application vs dynamic application
static: the content, structure, and layout of the pages remain fixed and do not change dynamically.
dynamic: content, features, and functionality can change in real-time or in response to user input.


# HTTP method

## POST vs PUT
POST is not idempotent, and PUT is idempotent. An operation or request is considered idempotent if the result of performing that operation multiple times is equivalent to the result of performing it only once. In other words, making the same request repeatedly should have the same effect as making it just once.

**POST**: 
The client sends a POST request to a specific endpoint (e.g., `/images`) with the image data included in the request payload. The server processes the request and creates a new image resource on the server. The server generates a unique identifier for the image and stores the image data associated with that identifier. Each time the user sends a POST request with a new image, a new resource is created on the server with a new identifier.

**PUT**:
The client sends a PUT request to a specific endpoint (e.g., `/images/{imageId}`) with the updated image data included in the request payload. The server processes the request and replaces the existing image resource identified by `{imageId}` with the updated image data. The server updates the image resource with the new data provided in the PUT request. The image is modified in place, preserving the same identifier.

# CAP theorem
The CAP theorem, consisting of Consistency, Availability, and Network Partition (network outage) components, describes a scenario where a system cannot guarantee both consistency and availability during a network partition event (network outage). It necessitates a trade-off between the two.

For example:

Initially, the nodes (A, B, and C) are part of the distributed system, ensuring strong consistency through data replication. However, due to a network issue or failure, nodes are separating into two groups. The outage prevents data exchange and coordination between the groups.

Consequences arise: If you want the nodes in both partitions to remain available and serve requests, data consistency cannot be guaranteed as the partitions cannot exchange data. Alternatively, if you prioritize data consistency, one partition may need to be isolated and unavailable for changes.

Another way to articulate the CAP theorem is by stating that you can only choose two out of the three components simultaneously. To maintain both consistency and availability, the goal is to avoid network partitions. However, network partitions are often considered a prerequisite.
