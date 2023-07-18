# Concepts
1. Vertical Scaling
2. Horizontal Scaling:
   1. adding Replicas
3. Load Balancer - Reverse Proxy
   1. Round Robin
   2. Hashing
4. Content Delivery Server (CDS)
5. Caching
6. DNS
7. Application layer protocol:
   1. HTTP
   2. HTTPS
   3. websocket
8. API pattern:
   1. RESTful
   2. Graph QL
   3. gRPC
9. ACID of relational database
10. Sharding and Replication
    1.  Leader and Follower Replication
11. CAP theorem
    1.  Consistency
    2.  Available
    3.  Partition

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
7. Auto Scaling ??

# Bugs
1. Understand the bug: Gather information and reproduce the issue.
2. Isolate the bug: Identify the affected component or module.
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

SQL databases are typically a good fit for applications that require strong data consistency, complex queries, and transactions. NoSQL databases are often preferred for handling large-scale, rapidly changing, or unstructured data, and for applications that prioritize scalability and performance over strict data consistency.

# Reactjs

## Virtual DOM
Once the virtual DOM is updated, ReactJS performs a process called reconciliation, where it compares the previous virtual DOM with the updated virtual DOM. During this process, ReactJS efficiently determines the minimal set of changes needed to be made to the real DOM to reflect the changes in the virtual DOM.

After the reconciliation process, ReactJS applies only the necessary updates to the real DOM, known as "diffing." This optimized approach minimizes the number of manipulations required on the actual DOM, resulting in better performance compared to directly updating the entire DOM structure.


# SPA vs Static Application

SPAs are suitable for complex applications that require real-time updates, interactivity, and a more dynamic user experience. Static applications are a good fit for content-focused sites, blogs, or scenarios where simplicity, performance, and security are the primary concerns. MPAs follow a page-centric architecture, where each page represents a distinct HTML document with its own set of styles, scripts, and content. Each page typically corresponds to a specific functionality or view within the application.

# HTTP method

## POST vs PUT
POST is not idempotent, and PUT is idempotent. An operation or request is considered idempotent if the result of performing that operation multiple times is equivalent to the result of performing it only once. In other words, making the same request repeatedly should have the same effect as making it just once.

**POST**: 
The client sends a POST request to a specific endpoint (e.g., `/images`) with the image data included in the request payload. The server processes the request and creates a new image resource on the server. The server generates a unique identifier for the image and stores the image data associated with that identifier. Each time the user sends a POST request with a new image, a new resource is created on the server with a new identifier.

**PUT**:
The client sends a PUT request to a specific endpoint (e.g., `/images/{imageId}`) with the updated image data included in the request payload. The server processes the request and replaces the existing image resource identified by `{imageId}` with the updated image data. The server updates the image resource with the new data provided in the PUT request. The image is modified in place, preserving the same identifier.

# CAP theorem
The CAP theorem, consisting of Consistency, Availability, and Partition components, describes a scenario where a system cannot guarantee both consistency and availability during a network partition event. It necessitates a trade-off between the two.

Consider a distributed system with multiple nodes running instances of a Spring Boot application. These nodes communicate with each other to perform tasks or share data. In the event of a network partition, nodes become disconnected, forming isolated groups that cannot communicate.

Initially, the nodes (A, B, and C) are part of the distributed system, ensuring strong consistency through data replication. However, due to a network issue or failure, a partition occurs, separating nodes into two groups. The partition prevents data exchange and coordination between the groups.

Consequences arise: If you want the nodes in both partitions to remain available and serve requests, data consistency cannot be guaranteed as the partitions cannot exchange data. Alternatively, if you prioritize data consistency, one partition may need to be isolated and unavailable for changes.

Another way to articulate the CAP theorem is by stating that you can only choose two out of the three components simultaneously. To maintain both consistency and availability, the goal is to avoid network partitions. However, network partitions are often considered a prerequisite。