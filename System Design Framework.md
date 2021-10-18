# System Design Framework

## Gathering Requirements

### Functional Requirements
- Act as a product manager and develop user stories to solve the users problems.
- Interviewers look for solid product sense and strong [**user empathy**](https://medium.com/@henrymodis/user-empathy-f995f1fde26d).
    - Who is it for and why do we need to build it?
    - What are the features we need to solve the users' problem?
        - When defining features make sure to list out features from user perspective and then get it reviewed by interviewer
- Clarifying the terminologies present in the requirements specifications.
- Since it is a System Design interview. Focus should be on the system and not on the algorithm and model.


### Non-Functional Requirements
- You should ask questions to build **preliminary tuition** on what could break the system, and when it does, some areas that can be
compromised to scale for those bottleneck challenges.

#### Scale
- How many active users are there in the system?
    - Take information from the interviewer and build or calculate scale based on intuition.
- How are the users distributed across the world?
    - Latency for cross-globe communication may significantly impact the user experience.
    - Its crucial to figure out the distribution to discuss geo locality design.
- Scenarios that can break your system.
    - Considering a real-life scenarios highlights the worst and difficult cases for the application. By making trade-offs user can demonstrate his ability to think differently and make decision based on that.
    - **Thundering Herd prblem**
    - A design without bottlenecks isn't challening and interesting.
- Scenarios that leads to high storage and bandwidth
    - Scaling of storage system involves factors such as amount of memory being passed through a request, how frequently the servers handles the request.

#### Performance
- What is the availability and consistency requirements?
    - The goal is to discuss whether the system can tune the user product experience's consistency to meet the availbility demand better
    - [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
    - Instead of designing a whole system based on AP or CP. Components of a system can be classified into an AP or CP. Further, features present within those components can be categorised into a AP or CP which gives more clarity into the system
    - Discuss from user perspective.
- What is the accuracy requirements?
    -  Accuracy is different from consistency.
- What is Response Time and Latency Constraint?
    - Response Time = Latency + Processing time
    - Latency is the time that request has to wait before it is processed.
    - Processing is the time taken to process the request.
- What is the freshness requirements?
    - Data freshness are based upon real-time, near-real-time, batch processing
        - real-time: data transmission in ms is barely acceptable
        - near-real-time: considering seconds delay in data transmission is acceptable
        - batch processing: since real-time, near-real-time are expensive operations to build, some apps can still provide good user experience if it takes hrs/days to run.
- Durability requirement is based on SLAs defined. It is categorized into High Durability, Medium Durability, Low Durability.
    - High Durability defines the data needs to be available when the user requests it. ex: Photo sharing application
    - Medium Durability defines that losing data is allowed. ex: Chat application
    - Low Durability defines data history is ignored completely. ex: Drivers location on a delivery app as it updates itself.