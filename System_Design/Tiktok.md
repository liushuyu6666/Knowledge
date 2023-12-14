# Clarifications
## Questions and Answers
1. Narrow down the question scope and make suggestion about which part of the system to focus on
   1. focus on the backend distributed system that supports uploads and downloads.
   2. videos uploads into the system and then streaming the videos or consuming the videos.
   3. skip sign-in sign-out part
2. More details about the application calibers.
   1. Q: how many users, how many videos uploaded, what's the scale of this thing
   2. A: 1 billion users around 150 countries. 1 billion videos viewed per day. 10 billion uploaded in one year.
3. Get the success metrics (a.k.a KPI).
   1. number of videos uploaded per day / total duration of videos uploaded per day.
   2. total time the user consuming in this application.

## Success Metrics
Success Metrics is also known as KPI, We need to select a success metrics in the clarifications process to instruct us to design the system. We always use the success metrics to evaluate and improve our system.
For evaluation:
1. Goals: Metrics should align with goals.
2. Quantifiable: Success metrics should be **quantifiable**, For example we can numbers or percentages to measure the success metrics.
3. Timeliness: Metrics should be collected in a **real-time** or **near-real-time** pattern. This is because we can use these data to identify issues.
   1. counter-example: "Annual Customer Satisfaction Survey Results".
4. Benchmarking: it's useful to compare current performance against historical data or industry benchmarks. Benchmarking provides context for evaluating whether performance is above or below average.

For improvement:
1. Actionable: Metrics should not only inform you about how the system is performing but also suggest what actions can be taken to improve performance if needed.
2. Comprehensiveness: Metrics can provide a more comprehensive view of system performance. This may include metrics related to user experience, system reliability, scalability, security, and more.

There is one counter-example: "Total Page Views" (how many times pages on a website have been viewed) for a website without additional context or analysis is not an ideal metric because it doesn't tell you why certain pages are popular or why others aren't. To improve this metric we should:
1. Break down page views by different types of content or pages (e.g., articles, product pages, landing pages). This can help identify which types of content are most popular and where improvements might be needed.
2. Get the bounce rate (the percentage of visitors who leave the site after viewing only one page). A high bounce rate might indicate that visitors are not finding what they're looking for, prompting you to investigate and improve the content or user experience on certain pages.
3. Analyze the conversion rate alongside page views. If your goal is to drive conversions (e.g., sign-ups, purchases), this metric can tell you how well your pages are performing in terms of achieving that goal.


# Non-functional Requirements (Calculations)
## Equations
1. $1 kB = 10^3 B$
2. $1 MB = 10^3 kB$
3. $1 GB = 10^3 MB$
4. $1 TB = 10^3 GB$
5. $1 PB = 10^3 TB$

## Videos Calibers
Parameters of the video:
1. Resolution: 640p x 360p, 3 bytes per pixel for RGB color. 691200 bytes in total.
2. Duration: 10 seconds.
3. Frame Rate: 30 frames per seconds (fps).

Before compression, one video takes 207360000 bytes in total or 200 Mb approximately.

Video compression is different from text compression. After compress the text, the content will be hard to understand. But the goal of video compression is to reduce the size of a video while retaining a level of quality that remains understandable and watchable to humans.

To determine the exact video size after the compression, you would need to know the specific codec, bitrate, and compression settings applied to the video.

**Codec**: refers to the specific algorithms that are used to compress video efficiently.
**Bitrate**: refers to the size of data used to represent one second of video footage. It is typically measured in bits per second (bps), kilobits per second (kbps), megabits per second (Mbps), or gigabits per second (Gbps).

For a 640p x 360p video, let's assume a moderate bitrate of 1 Mbps to compress it:
1. bitrate = 1 Mbps;
2. duration = 10 seconds;
3. total bits = 10M bits = 1.25 MB;

So, the video will be 1.25 MB. So, you can see the size after the compress is decided by the bitrate instead of the video solution.

## High level calculations
Do some high level calculation will be helpful. It is better to priorize the factor which effects the system design, here is the storage, includes blob storage and metadata storage. And then we need to calculate the traffic, which includes: ingress and egress. The detail calculation will be provided in the diagram at the end of this page.

Don't forget the replications here. There are several reasons for having replications:
1. **Fault Tolerance**: In a distributed system, hardware failures, network issues, or other unforeseen events can lead to data loss or unavailability. By replicating data across multiple servers or data centers, the system can continue to operate and serve users even if one or more replicas become unavailable due to failures.
2. **Availability**: Users can access data from the nearest or most available replica.
3. **Load Balancing**: By distributing data across multiple replicas, the system can distribute the read and write load evenly among these replicas.
4. **Caching**: Replicated data can be used for caching frequently accessed content. Caches can be located closer to the users and can significantly reduce the load on the backend storage systems.


# High level design
1. Video blob storage (AWS S3)
   1. replications
   2. regions
   3. tier storage data: most of videos' life spans is only half a year. So for these videos which receive less access, S3 reduces storage costs of these less active blob while maintaining performance for frequently accessed data.
2. how would you think the different regions or countries could be reflected in the design: make the data near to where you are is important for a global app.
   1. partition the data base on the location or language.
      1. when you partition data in a database, you physically distribute different partitions (e.g., Partition A, Partition B, and Partition C) to different storage locations or servers, but conceptually, the original database system can still access and manage all of them as a single logical database. This means that from the perspective of the database management system (DBMS) and the application using the database, it appears as if the data is still unified, even though it's distributed.
   2. Add CDN (CloudFront) as well: cache regional popular data in the CDN.
3. User data: Users have connection to other uses. So, don't separate users data into segments which can't talk to each other.


# Drill Down to the schema
## Video metadata table

## User metadata table

## Machine Learning

# Bottlenecks and enhancements
1. Potential bottleneck arising from algorithmic ForYou generation. For mobile applications, offloading compute from your distributed system onto users' devices can be a good solution.
2. Decrease the cost: Set up our own hosting of a MySQL solution instead of using S3 solutions.

