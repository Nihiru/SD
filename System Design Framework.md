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
- Make sure all the feature clarifications question are answered before proceeding with the **Design** phase. 

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
    - [**Thundering Herd prblem**](https://en.wikipedia.org/wiki/Thundering_herd_problem)
    - A design without bottlenecks isn't challening and interesting.
- Scenarios that leads to high storage and bandwidth
    - Scaling of storage system involves factors such as amount of memory being passed through a request, how frequently the servers handles the request.

#### Performance
- What is the availability and consistency requirements?
    - The goal is to discuss whether the system can tune the user product experience's consistency to meet the availbility demand better
    - [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
    - Instead of designing a whole system based on AP or CP. Components of a system can be classified into an AP or CP. Further, features present within those components can be categorised into a AP or CP which gives more clarity into the system.
    - Components in the system
        - Load Balancers
        - Web Servers
        - Application Servers
        - Database Servers
        - Cache
        - Queues
        - Publisher/Subscriber
        - Offline Jobs
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

## Define API
- The purpose of the API is to have a detailed agreement between the end user and backend system.
- How to define API
    - API is a broad term since it could be from a mobile client, web client, internal system, single machine inter process call etc.
    - An API is made up of 
        - API Signature
            - After identifying the **scope** of the API. Based on its definition Naming the API is the most important aspect.
        - Input Parameter
            - Justification required for the defined parameters
            - They should be important to functional requirements
            - Identify the core functionality from the requirement
            - Missing input parameter questions the interviewee carelessness while gathering requirements.
            - Input shouldn't be vague and nonsensical
        - Output Response
            - It shouldn't include extraneous details irrelevant to the functional requirement or miss important responses necessary for the functional requirement
            - Ensure the Response satisfies the requirement
            - Being explicit about the response status and its corresponding response codes if any.
            - Response data structure should also match the requirement.
            - Identifying **inefficiencies** in the response data structure is important for large data results.
            - Making sure only vague and nonsensical output is not returned.
    
## High Level Diagram Design
- Purpose
    - Setting up the foundations for the design and give clarity to the interviewer on which parts of the interview are important to satisfy requirements.
    - It could a omit a behavior of an end-to-end flow that satisfies the requirement.
- Start from the top with the API and working yourself down to the last component
    - 1: Define the client for an API
    - 2: Define the next sets of logical blocks 
    - 3: Repeat step 1 for the next API
- Make sure understanding happens around the core of the question.
- Avoiding unnecessary features to the design
- Don't prematurely optimize
    - Do not dig into sections and prematurely optimize without completing the holistic picture first
    - Coming up with important discussion points is a critical part and maintaining it on a list
- Have logical separation between services
- Take a moment to walk through the flow of the defined APIs to ensure the requirement is satisfied

