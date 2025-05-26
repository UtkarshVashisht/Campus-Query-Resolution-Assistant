Chapter 1

1. INTRODUCTION

1.1	BACKGROUND

In the current academic landscape, information at their fingertips is not only a luxury but a need. Colleges and universities cater to thousands of students across different departments, each with their own set of questions related to admissions, studies, hostels, placements, scholarships, and so on. To simplify this interaction and give a one-point support system, educational institutions are increasingly opting for digital tools such as chatbots and automated assistants.

The Vellore Institute of Technology (VIT), a leading private university in India, receives a large number of inquiries every day from prospective and existing students. Such queries tend to be repetitive in nature and are related to similar issues. Historically, answering such queries has been the domain of administrative personnel, email desks, or physical helpdesks, which are time-consuming, inefficient, and subject to delays. To relieve this, the idea of a Campus Query Resolution System came forth and was created as a smart, scalable, and interactive chatbot solution specifically designed for VIT-related queries.

This system aims to mimic real-time conversation with users, correctly answering questions using a blend of a carefully curated dataset and sophisticated language models. It is based fundamentally on a dataset of FAQs and their answers to provide quick responses. When questions are not included in the dataset, the system seamlessly incorporates the OpenAI GPT model to provide clever fallback answers, providing full query coverage.

The main goal of this project is to provide an ever-present, easy-to-use assistant for VIT students, employees, and applicants. It obviates the necessity of manually scouring long web pages or waiting for responses through email. In addition, this chatbot enables user registration and login, which provides a touch of personalization and possible scalability for future enhancements like session tracking, feedback mechanisms, and student-specific interactions.

Implementation stack features a trendy, responsive front end developed in HTML, CSS, and JavaScript, and backend run on Python based on Flask. The chatbot provides live interaction through async communication with the backend server. Architecture is simplified yet modular supporting local deployment alongside scalability in a future cloud base.

In effect, the VIT Campus Query Resolution System seeks to fill the gap between institutional knowledge and student accessibility using technology, in tune with current trends in AI-driven educational software and digitalization in tertiary education.


1.2	MOTIVATION

The motivation behind building this system stems from multiple practical and educational perspectives.

1.2.1	Real-World Problem Solving

The campus environment is dynamic and multifaceted, with different departments taking care of different tasks. With students entering university life or moving through academic and non-academic challenges, they tend to get lost in finding correct and timely information. A lot of student and staff time is wasted on redundant questions that can be easily automated. This project fulfills that real-world requirement of digitized, autonomous assistance.

1.2.2	Improving Student Experience

For most students, particularly new and international applicants, it is overwhelming to navigate a big university's infrastructure. The presence of an available and responsive virtual assistant working 24/7 makes them feel more taken care of and lessens the cognitive burden of locating pertinent information. This goes a long way in directly reducing the onboarding process and satisfaction.

1.2.3	Reducing Administrative Workload

Administrative staff and professors too typically spend too much time addressing repeated questions—time that they might otherwise dedicate to more purposeful tasks. Making answers to frequently asked questions automatic can save an immense amount of that hassle. It also guarantees reliability and consistency of the information offered.

1.2.4	Learning Opportunity in AI and Web Development

From an academic and developer's perspective, constructing such a system provides a great way to practice and utilize various technical concepts, such as web development, RESTful API integration, frontend/backend sync, and AI prompt engineering with the OpenAI API. It also enables one to get hands-on practice with Python, JavaScript, and technologies like Flask, which are very much sought after in the current job market.

1.2.5	Scalability and Future Potential

After being built and VIT-tested, this system would be expandable or replicable to other schools or uses. The modularity of the design makes it simple to expand to add such features as voice assistance, multilingual conversations, or interface with official college databases and websites.


1.3	SCOPE OF THE PROJECT

The Vellore Institute of Technology (VIT) Campus Query Resolution System is a smart, user-friendly, and effective system that assists students and potential applicants in resolving queries about the university. The project scope summarizes both technical specifications and functional limitations under which the system should function. It combines web development, query matching based on data, and artificial intelligence to provide an integral and scalable chatbot experience.

1.3.1	User Interaction and Interface

The system has a responsive, web-based interface through which users can register, log in, and communicate with the chatbot. The interface is developed using HTML, CSS, and JavaScript to provide a clean and intuitive experience on devices. The interface is designed to resemble real-world chat applications, allowing users to use the system naturally. Users can input questions in free-text format, and get responses in real time.

1.3.2	Authentication System

A simple user authentication module is provided, where users can register and login. This is done on the frontend side using JavaScript with mock in-memory user storage for development. Although not connected to a database at the moment, this module can be extended to include secure backend authentication using services like Firebase or SQL-based databases for production.

1.3.3	Predefined Dataset Matching

At the center of the backend is a CSV-based dataset of frequently asked questions and their respective answers pertaining to VIT. When the user enters a query, the system tries to match the same against this dataset using simple text preprocessing (lowercasing, trimming) and partial string matching. This enables quick retrieval of suitable answers for frequent queries like:

•	Admission procedure
•	Hostel and mess information
•	Course structure and fees
•	Exam and result timetables
•	Placement statistics and contacts

The data can be easily added to over time, making the system more complete as more information is collected.



1.3.4	AI-Powered Fallback

If no close match is found in the dataset, the system uses OpenAI’s GPT-3.5-turbo model to generate intelligent responses. This ensures the system remains responsive and helpful, even for queries not explicitly listed in the dataset. This hybrid architecture—combining static data with dynamic AI—makes the chatbot more versatile and adaptable.

1.3.5	Backend and API

The backend is implemented in Flask, a lightweight Python web application framework. The backend processes incoming chat requests, queries the dataset, makes API calls to the OpenAI API when necessary, and sends the response of the chatbot back to the frontend. The application utilizes Flask-CORS to support cross-origin communication so that the frontend and backend can function flawlessly even if they are hosted on different domains or ports.

1.3.6	Scalability and Extensibility

Although the system now is intended for one institution—VIT—it is modularized so that it can be simply adapted to another educational campus or enhanced with extra features. Its future enhancements could include:
•	Integration with databases (MySQL, Firebase)
•	Multilingual support
•	Admin dashboards for managing FAQs
•	Voice input/output capabilities
•	Mobile responsiveness and app integration













2.PROJECT DESCRIPTION AND GOALS


2.1 LITERATURE REVIEW

The growing application of Artificial Intelligence (AI) and Natural Language Processing (NLP) technologies in academic settings has opened up the way for intelligent systems to support automating academic and administrative work. Among them, chatbots—interactive agents that can communicate with users using natural language—have emerged with great potential in resolving student inquiries and strengthening institutional support services. This review of literature delves into critical research studies, technological developments, and implementations associated with campus-based chatbot systems.

2.1.1 Chatbots in Education

Chatbots have been increasingly incorporated into educational environments to facilitate learning, administrative support, and student engagement. Educational chatbots, as identified by Winkler and Söllner (2018), are divided into three categories: informational bots, tutoring bots, and advisory bots. Informational bots, such as the one developed in this project, aim to provide rapid and accurate answers to frequently asked questions, which offloads the workload of staff and increases the satisfaction of students.

In a research conducted by Jia (2019), chatbots were reported to effectively minimize student stress during enrollment and orientation periods by answering procedural questions on time. Such systems succeed based on how well the chatbot can accurately interpret natural language questions and give responses in understandable, context-sensitive ways.

2.1.2 NLP and Dataset-Based Query Resolution

A large part of chatbot building is natural language processing. String similarity, tokenization, stemming, and fuzzy matching are applied in basic systems to compare user input with fixed questions. Mihailidis et al. (2020), for example, built a university chatbot based on dataset-driven keyword matching and achieved high success in solving campus-related questions without the usage of external APIs.

These systems are, however, limited in that they fail when questions are asked uniquely or outside the context of the dataset. Hybrid models have, therefore, been developed to counteract this by bringing together dataset-based retrieval and generative models such as GPT. The combination provides both accuracy for known questions and freedom for new ones, presenting a better user experience.


2.1.3 Generative AI in Conversational Interfaces

Recent breakthroughs in AI, particularly OpenAI’s GPT (Generative Pre-trained Transformer) models, have redefined the capabilities of chatbots. These models are trained on vast amounts of internet data and can generate coherent, contextually relevant responses based on conversational prompts. Radford et al. (2019) introduced GPT-2, demonstrating the potential of large language models to understand and generate human-like text. Its successors, GPT-3 and GPT-3.5, have proven to be even more fluent and contextually intelligent, and hence fit for purposes in real-world applications.

In educational applications, the models have found application in answering long and complex questions, condensing course work, and even providing tutoring. GPT-based chatbots have the benefit of being able to understand different wordings, slang, and open-ended questions—something rule-based bots cannot. However, as Gamage et al. (2021) warn, generative models sometimes give unaccurate or misleading responses where institution-specific data is not inputted. That makes the justification of using the hybrid approach worthwhile, as executed in this research, where the system initially seeks out a predetermined dataset before taking the AI model's advice.

2.1.4 Existing Implementations in Universities

Some institutions have introduced chatbot technologies to improve their student services. For instance, Georgia State University launched a chatbot called "Pounce" to help students with enrollment and financial aid questions. Through a study conducted by Page and Gehlbach (2017), the bot gave a major boost to response time, as well as lowering summer melt rates. Likewise, Deakin University in Australia introduced "Genie," a bespoke student aid that can control schedules, grades, and requests for academic support.

These demonstrations illustrate the increased adoption of conversational AI in education environments. Yet, most of these are enterprise-level platforms involving considerable development expense and effort. Open-source and research projects such as the VIT Campus Query Resolution System, however, seek to achieve similar functionality utilizing lightweight technologies such as Flask, pandas, and OpenAI APIs, which are more cost-effective and scalable for small teams.

2.1.5 Limitations and Future Directions

Although chatbots are quickly becoming a standard in campus life, there are several drawbacks. Rule-based bots tend to have difficulty with ambiguous or multi-intentional questions. Generative AI models, conversely, are capable of generating confident but incorrect responses if they are not well-tuned or well-constrained. As highlighted by Abd-Alrazaq et al. (2020), ongoing training of datasets, feedback loops, and ethics (such as bias and data privacy) need to be considered in the development of chatbots.


In addition, most systems are not equipped with features like multilingual capabilities, voice integration, or emotion-aware responses. Research in the future is focused on incorporating emotion recognition, context persistence, and customized learning paths to make chatbots not only informative, but empathetic and adaptive.

2.2 RESEARCH GAP

With conversational agents and chatbot systems ever more popular in the educational space, more institutions are turning to AI-powered support tools to increase student participation and automate administrative tasks. Various studies and real-world applications, like Georgia State University's "Pounce" and Deakin University's "Genie," have shown chatbot systems to be beneficial in managing student inquiries. But even after these developments, there are some significant gaps in research and implementation that exist, particularly for institution-level solutions like the one in development for Vellore Institute of Technology (VIT).

2.2.1 Lack of Institution-Specific Chatbots

Most of the currently available educational chatbots are generic or intended for universal applications and lack domain-specific contextual knowledge of the internal working of specific university campuses. Although models such as GPT-3 can easily answer general academic questions, they usually fail to be based on the specific procedures, terminology, and administrative practices unique to a given institution. There is a clear absence of chatbots specific to individual universities such as VIT that can tackle localized issues—such as VIT's Fast Track system, semester abroad program, or FFCS (Fully Flexible Credit System).

This project fills that gap by incorporating a curated dataset of VIT-specific questions and answers, with the goal of ensuring the responses are not just accurate but also institutionally applicable. Nonetheless, there is still a wider research gap in developing very highly contextualized chatbot models that can be easily incorporated into an institution's internal workflows and databases.

2.2.2 Inadequate Hybrid Models for Academic Use-Cases

Most educative bots either fall within rules alone (dataset-driven) or AI-driven ones (generative). Rule-driven systems, whilst precise, don't generalize for unseen questions. On the contrary, AI-based systems such as GPT tend to manage variant inputs but also might respond hallucinated or even factually false in the absence of context. Although models bringing together both directions are becoming increasing common, insufficient effort has yet been done properly balancing them, particularly within less resource-saturated environments such as college-sponsored sites.

The VIT Chatbot Project tries to fill this gap by using a two-layer strategy: it first tries to match queries against a dataset and resorts to calling the OpenAI API only afterwards. Though this enhances accuracy and cost-effectiveness, further research is required to streamline such hybrid approaches and make switching between retrieval and generation smooth, without confusing the user.

2.2.3 Minimal Focus on Lightweight and Cost-Effective Implementations

Most of the available research and solutions in this field are enterprise-level systems that take huge development teams, cloud infrastructures, and heavy capital investments. This poses a limitation for adoption in low-budget institutions or technically challenged organizations. There is a visible dearth of simple, open-source frameworks that can be easily developed, deployed, and managed—especially by students or research teams at academic institutions.

This project bridges that gap using open-source technologies like Flask, pandas, and vanilla JavaScript for front-end interaction. It proves that functional and scalable chatbots can be constructed without using proprietary platforms or heavy resources, and thus the approach can be replicated by other colleges.

2.2.4 Limited Evaluation on Real-World Query Variability

Another significant gap is the lack of thorough evaluation of chatbot systems against actual, noisy real-world user queries with slang, typos, or colloquial language. These prototypes usually work well in idealized settings but break when put into use due to inadequate robustness. This project can act as a starting point for doing such testing in future incarnations, particularly after deployment to the student body of VIT.

2.3 OBJECTIVE

The main goal of this project is to create and implement an intelligent, web-based Campus Query Resolution System that will be able to answer queries related to Vellore Institute of Technology (VIT) with a mix of predefined information and AI-driven answers. The system will provide students, faculty, and potential applicants with instant, precise, and relevant information in an efficient and user-friendly format.
In detail, the objectives of the project are as follows:

2.3.1 To Develop a Responsive and Interactive Chatbot Interface

One of the foremost goals of this project is to create a modern and user-friendly chat interface that mimics real-time messaging applications. This includes providing features such as:

•  An interactive message box with avatar support for user and bot identities.
•  Real-time message exchange between the user and the backend server.
•  Smooth navigation with a clean and visually appealing layout.

The interface should be intuitive and accessible, allowing users to interact with the chatbot without needing technical expertise.

2.3.2 To Implement a Basic User Authentication System

The system is intended to provide basic user registration and login functionality. The feature is intended to:

•	Enable users to create individualized accounts with email and password.
•	Enable logged-in users to use the chatbot and keep session-specific information (if to be extended in the future).
•	Prevent unauthorized access and provide a base layer for future role-based access control, e.g., admin or student roles.

Although deployed with front-end logic for the prototype, the architecture is capable of backend integration for real-world deployment.

2.3.3 To Create a Query Resolution System Based on a VIT-Specific Dataset

A central goal is to give prompt and correct responses to frequent queries using a pre-defined dataset. The dataset is prepared especially for VIT-related queries like:

•	Admission procedures
•	Academic programs and structure
•	Hostel and mess facilities
•	Fee payment and scholarship details
•	Placement support and contact information

The system must be able to search the dataset through basic string matching methods in order to answer queries without the need for an internet connection or external APIs.

2.3.4 To Integrate AI Capabilities Using OpenAI’s GPT for Unanswered Queries

Another major objective is to handle queries that are not directly matched in the dataset. For this, the system uses the GPT-3.5 model through OpenAI’s API. The goals here are:

•	To generate intelligent, context-aware responses for unexpected or novel user inputs.
•	To maintain continuity and completeness in the chatbot experience, ensuring users are never left without an answer.
•	To simulate a conversational tone that makes the bot feel more human-like and approachable.

This guarantees the system is useful and active, even as the variety of user requests changes.


2.3.5 To Design a Lightweight, Scalable, and Extensible System

The project also seeks to prove that a fully functional, hybrid chatbot system can be built using lightweight technologies like Flask, JavaScript, and pandas. By doing so, it:

•	Encourages cost-effective development suitable for small teams or academic environments.
•	Enables future enhancements like database integration, multilingual support, or voice interaction.
•	Promotes the development of scalable systems that can be adopted by other campuses or departments.

2.4 PROBLEM STATEMENT

With the vibrant and knowledge-rich academic culture in institutions of higher education, gaining access to current and precise information is indispensable to students, educators, and even prospective candidates. Organizations like Vellore Institute of Technology (VIT) with its hundreds of thousands of learners in a string of campuses must address an imperative need for coping with information flows and streamlining interactions among the administration blocks and the student populace. In spite of the availability of official websites, notice boards, and student portals, there still exists a significant gap in communication between the institution and students.

Current modes of information dissemination, such as static FAQ pages, manual inquiry counters, and student forums, prove to be insufficient in responding to actual-time questions, particularly those that are contextual, time-bound, or specific in nature. For example, a student seeking information regarding FFCS (Fully Flexible Credit System) registration timelines or hostel check-in formalities during a holiday season might not get the information readily or experience response lags. Likewise, potential students tend to ask repeated questions regarding admission requirements, entrance tests, guidance procedures, or scholarship qualifications, which clog administrative helpdesks during peak periods.

Additionally, these conventional channels tend to be human-intensive, resulting in extended waiting times, unreliable information, and redundant workloads on administrative personnel. The absence of real-time automation and interactivity translates into inefficiencies that adversely affect the user experience and institutional productivity.

In the digital age of transformation, where customers have grown to expect instant access to services and support via mobile apps and chat interfaces, schools are lagging behind in embracing user-focused communication paradigms. While some universities have begun introducing chatbots, these tend to be generic, not context-aware, and cannot respond to institution-specific queries adequately. Moreover, industrially available chatbot solutions are often resource-hungry, with high budgets, technical personnel, and infrastructure that might be unaffordable to some education institutions.

Meanwhile, the majority of chatbot deployments are either rule-based (employing hardcoded question-answer sets or keyword matching) or completely AI-powered (utilizing large language models such as GPT). Rule-based bots provide limited flexibility and break down when questions are asked differently from their storage in the dataset. Alternatively, AI-powered bots such as GPT have the ability to comprehend varied inputs but can come up with hallucinated or false responses when they are not trained on institution-based content. Also, these models have API charges and need ethics and data handling considerations.

Thus, the core problem this project addresses is the lack of a reliable, hybrid, and VIT-specific query resolution system that can intelligently respond to a wide range of user queries—both structured and unstructured—without overwhelming institutional resources.

The system should be capable of:

•	Handling real-time queries in natural language through a conversational interface.
•	Delivering accurate responses for known, frequently asked questions using a structured dataset.
•	Falling back to AI-powered responses for less common or unique queries.
•	Operating on lightweight, scalable architecture suitable for student-led or academic projects.
•	Being accessible to users via a modern, intuitive web interface without technical barriers.

Apart from resolving the information deficit, the system is also meant to lighten the working load of administrative personnel, enhance the experience of students, and provide the platform for other future AI-related upgrades like multi-language support, voice commands, and connectivity to official databases and portals.

By centering on VIT and adjusting the dataset to be campus-centric, incorporating specifics such as academic timetables, exam types, hostel policies, placement guidance, and extra-curricular activities—the system is significantly more practical and applicable than generalized educational bots. It also lays the template for other schools to create affordable, effective support mechanisms with the support of open-source technologies and cloud-based artificial intelligence models.

To summarize, the project seeks to address the following core problems:

•	The inefficiency of existing communication channels in resolving student queries.
•	The absence of an institution-specific intelligent support system for VIT.
•	The limitations of current chatbot models in handling diverse, real-world queries effectively.
•	The lack of cost-effective, scalable chatbot solutions for academic institutions.





2.5 PROJECT PLAN

A clearly articulated project plan is crucial to effectively executing any software development project. For the VIT Campus Query Resolution System, the plan has been meticulously scheduled into well-defined phases to enable systematic progress, risk reduction, and quality checks. This section describes the methodology, key milestones, and tasks involved in the development and deployment of the chatbot system.

2.5.1 Requirement Analysis and Feasibility Study

The initial project phase was collecting and analyzing the system requirements. This involved learning about the nature of queries usually made by students at Vellore Institute of Technology, e.g., admissions, academic calendars, hostel regulations, placements, and fees. A feasibility study was also done to identify appropriate technologies to be used which would fulfill the criteria of real-time interaction, cost-effectiveness, and scalability.

Key Deliverables:

•	List of frequently asked questions and categories.
•	Identification of system constraints and objectives.
•	Decision to use Flask, pandas, JavaScript, and OpenAI API for implementation.


2.5.2 Dataset Design and Curation

Once the requirements were understood, the next step involved compiling a dataset of FAQs and their corresponding answers. This dataset was formatted as a CSV file and designed to cover a broad range of VIT-specific topics.

Activities:

•	Collecting information from official VIT sources such as websites, student handbooks, and brochures.
•	Structuring data into a question-answer format for easy matching.
•	Handling null values and inconsistencies for smooth integration with the backend.

Key Tool: pandas (for reading and processing the CSV dataset in Python)

2.5.3 System Design and Architecture

In this phase, the overall structure and components of the chatbot system were defined. The architecture followed a client-server model with a Flask backend and a browser-based frontend built using HTML, CSS, and JavaScript.

Components Designed:

•	Frontend interface for user interaction.
•	RESTful API to handle chat requests and responses.
•	Dataset-matching engine for known questions.
•	Integration point for OpenAI API fallback.

Deliverable: Architecture diagram illustrating system components and data flow.


2.5.4 Frontend Development

The frontend development involved creating an engaging and responsive interface for users to interact with the chatbot. This includes:

•	Login and registration screens.
•	A chat interface styled to resemble a typical messaging app.
•	Interactive elements such as typing input, avatar images, and scrollable message history.

Technologies Used:

•	HTML, CSS (for structure and styling)
•	JavaScript (for event handling and API communication)


2.5.5 Backend Development

The backend logic was developed using Flask, a lightweight Python web framework. The backend was responsible for:

•	Handling HTTP POST requests from the chat interface.
•	Matching user input against the local dataset using text preprocessing.
•	Sending unmatched queries to the OpenAI API and receiving intelligent responses.
•	Returning the appropriate chatbot reply to the frontend.

Additional Features:

•	CORS setup for cross-origin communication.
•	Error handling and user input validation.




2.5.6 Integration and Testing

After both frontend and backend were implemented, the system was integrated and tested end-to-end. Unit tests were performed on:

•	Dataset query resolution logic.
•	Chat interface responsiveness.
•	OpenAI API response consistency.

User testing was also conducted to ensure that the chatbot could handle real queries effectively, even when phrased differently or containing minor typos.

Testing Criteria:

•	Accuracy of responses.
•	System stability and error handling.
•	Usability and user satisfaction.


2.5.7 Deployment and Maintenance Plan

For development and testing, the system was run on a local server. However, provisions have been made to deploy the system using platforms like Heroku or Render, making it accessible online. Maintenance plans include:

•	Periodic updates to the dataset with new FAQs.
•	Monitoring API usage and costs.
•	Adding features like database integration or voice support in future iterations.
















3.TECHNICAL SPECIFICATIONS

3.1 REQUIREMENTS

In order to effectively develop and deploy the VIT Campus Query Resolution System, it is important to have a clear vision of what the system needs. These requirements specify what the system should do (functional) and in what circumstances the system needs to function (non-functional). This section describes the technical and operational specifications that drive the construction of the chatbot.

3.1.1 Functional

Functional requirements describe the specific behaviors, features, and functions the system must support to meet its objectives.

a. User Registration and Login

•	The system should allow users to register with an email, username, and password.
•	The system should validate email format and ensure unique user registration.
•	Users should be able to log in using their registered credentials.

b. Interactive Chat Interface

•	The system should provide a chat interface for users to input questions in natural language.
•	The chat interface should distinguish between user messages and chatbot responses.
•	The system should allow sending messages via a button or by pressing the “Enter” key.

c. Query Handling Using Predefined Dataset

•	The system should match user queries against a curated dataset of VIT-specific FAQs.
•	If a match is found, the corresponding answer should be returned to the user.

d. Fallback to OpenAI GPT Model

•	If no dataset match is found, the system should send the query to OpenAI’s GPT-3.5 model for a response.
•	The AI-generated answer should be returned to the user through the chat interface.

e. Session and State Management

•	The system should maintain the user session during the active chat.
•	The system should reset the session and chat history upon logout.

f. Error Handling

•	The system should gracefully handle errors such as invalid inputs, failed API calls, or empty queries.
•	The chatbot should return appropriate fallback messages when it encounters issues.


g. Logout Functionality

•	Users should be able to log out from the chatbot interface at any time.
•	Upon logout, the chat should be cleared, and the user redirected to the login screen.


3.1.2 Non-Functional

Non-functional requirements specify how the system should operate, including performance, usability, and scalability expectations.

a. Usability

•	The user interface should be intuitive, clean, and responsive on various screen sizes.
•	The chatbot should provide real-time feedback and maintain a conversational tone.

b. Performance

•	The system should provide fast response times for both dataset-based and AI-generated answers (ideally under 2–3 seconds).
•	The application should remain responsive and stable under multiple concurrent user sessions.

c. Scalability

•	The architecture should allow easy expansion of the dataset without requiring code changes.
•	The system should be capable of integrating with a backend database and cloud deployment in future upgrades.

d. Maintainability

•	Code should be modular and well-documented to facilitate future improvements.
•	Dataset updates (adding/removing FAQs) should be easily manageable via a CSV file.

e. Security

•	User data such as email and password should be securely handled (note: current version uses mock authentication; secure implementation is recommended for production).
•	The system should sanitize user input to prevent injection or API misuse.

f. Portability

•	The system should be platform-independent and run on any modern web browser.
•	The backend should be deployable on cloud platforms like Heroku, Render, or AWS.

g. Reliability

•	The system should function reliably under expected load and provide fallback responses in case of external API failures.
•	System logs or error messages (in development mode) should help in debugging and issue resolution.


3.2 FEASIBILITY STUDY

A feasibility study is an important step in assessing the viability of any software project. It assists in deciding whether the project can be taken up by examining its practicability from different aspects. For the VIT Campus Query Resolution System, three areas of feasibility have been assessed—Technical, Economic, and Social. Each of these provides information on the resources needed, the value of the project, and its acceptability among stakeholders.

3.2.1 Technical Feasibility 

Technical feasibility determines if the existing technology and resources can facilitate the development and deployment of the suggested system. For the VIT Campus Query Resolution System, technical implementation is very feasible because lightweight, widely used, and open-source tools are employed.

a. Technology Stack

The system employs a straightforward yet effective technology stack:

•	Frontend: HTML, CSS, and JavaScript for building the user interface. These are universally supported by modern web browsers and require no additional installations.
•	Backend: Flask, a Python-based web framework, is used for creating RESTful APIs. It is lightweight and easy to integrate with other Python libraries.
•	Data Processing: The pandas library is used to manage and search a CSV dataset of frequently asked questions.
•	AI Integration: OpenAI’s GPT-3.5 model is used to handle complex or unknown queries, giving the system a smart fallback mechanism.

All these tools are free, open-source (except OpenAI’s API), and well-documented, making development accessible and manageable even for student teams.

b. Development Resources

No high-end computing infrastructure is required to run the application. The local machine can host the development environment using lightweight tools. Flask applications can be deployed on platforms like:

•	Heroku
•	Render
•	Vercel (for frontend)
•	AWS or GCP (for more advanced hosting needs)

These platforms support auto-scaling and provide free-tier options suitable for student or prototype deployments.

c. Scalability and Maintenance

The system is built using modular architecture, making it easy to scale and maintain. Features like:

•	CSV-based question-answer storage (easily updatable)
•	API-based communication
•	Decoupled frontend-backend design ensure that new features can be added with minimal disruption. Future upgrades could include:
•	Migrating to a relational database (MySQL or PostgreSQL)
•	Integrating authentication with Firebase or OAuth
•	Adding analytics for chatbot interactions

d. Risk Factors

While the technical implementation is largely feasible, a few risks exist:

•	API dependency: The system depends on OpenAI’s API for dynamic query handling. In case of service outages or rate limits, this functionality may be temporarily unavailable.
•	Security: The current version uses in-browser mock authentication. For production, this must be replaced with secure, encrypted authentication.
•	Dataset accuracy: Dataset answers must be regularly updated to reflect institutional changes.

3.2.2 Economic Feasibility

Economic feasibility assesses whether the project is financially viable and sustainable over time. It involves evaluating development costs, operational costs, and the potential return on investment (ROI), either in terms of money, time savings, or value added.

a. Development Cost

Since the system is developed using open-source tools, the cost of development is extremely low. Key highlights:

•	No licensing fees for HTML, CSS, JavaScript, Python, Flask, or pandas.
•	No upfront infrastructure cost as development can be done locally.
•	Hosting on platforms like Heroku or Render can initially be free for low-traffic usage.

The only significant cost in the system is the use of the OpenAI API, which charges based on usage (per token). However, this cost can be controlled by:

•	Caching frequent queries.
•	Setting a usage limit or threshold.
•	Relying primarily on the local dataset for common queries.

b. Operational Cost

Operational expenses include:

•	Hosting fees (if traffic scales beyond free-tier).
•	Periodic updates to the dataset.
•	Maintaining the backend and security patches.

Even in long-term deployment, these costs remain minimal, especially compared to the cost of employing additional support staff to manually handle repetitive queries.

c. Return on Investment

The system does not directly generate revenue, but its value is measurable in terms of time and effort saved:

•	Reduces the burden on administrative staff.
•	Improves student satisfaction through instant support.
•	Speeds up onboarding for new students.
•	Enhances the institution’s image as a digitally advanced campus.

When implemented campus-wide, the long-term time and resource savings far outweigh the modest operational expenses, resulting in a positive ROI.





3.2.3 Social Feasibility

Social feasibility evaluates how acceptable the project will be to its target users—students, faculty, and staff—and whether it aligns with user behavior, institutional goals, and broader societal trends.

a. User Acceptance

The student body at VIT is highly tech-savvy and accustomed to digital tools. A chatbot that can answer queries instantly is likely to be well-received by students, particularly:

•	Freshers navigating campus life.
•	International students unfamiliar with VIT procedures.
•	Existing students seeking quick, reliable answers.

The chatbot’s human-like tone and interactive UI make it more appealing than browsing long FAQ pages or waiting for email replies.

b. Impact on Administrative Staff

Administrative departments will benefit from a significant reduction in repetitive queries. Rather than spending hours addressing the same questions via phone or email, staff can focus on higher-level issues, leading to increased job satisfaction and efficiency.
The chatbot is not intended to replace humans but to augment them—handling the repetitive and routine tasks so humans can focus on more complex matters.

c. Alignment with Institutional Goals

The implementation of a smart, AI-assisted chatbot aligns with VIT’s mission of promoting innovation, digital transformation, and student-centered services. It reflects the institution’s commitment to improving infrastructure and adapting to modern communication paradigms.

d. Long-Term Social Impact

Over time, the system can serve as a blueprint for other campuses or institutions seeking digital solutions to improve communication. Its low-cost and open-source nature also encourages collaborative improvement, further amplifying its social value.








3.3 SYSTEM SPECIFICATION

3.3.1 Hardware Specification

The VIT Campus Query Resolution System is a light-weight web-based application that should be able to operate on standard computing equipment. It uses no high-end servers or special hardware, so it can be developed locally and deployed online in scalable fashion. The following hardware specifications outline the minimum requirements for various parts of the system: development, hosting, and client usage.

3.3.1.1 Development Environment

This refers to the hardware setup needed by developers to build and test the system locally.

Minimum Requirements

•	Processor: Intel Core i3 (or equivalent AMD Ryzen 3)
•	RAM: 4 GB
•	Storage: 10 GB free space
•	Operating System: Windows 10 / Linux Ubuntu 18+ / macOS Catalina or above
•	Display: 13-inch screen, 1366x768 resolution
•	Network: Stable internet connection (required for OpenAI API usage)

Recommended Requirements

•	Processor: Intel Core i5 or higher (or equivalent AMD Ryzen 5)
•	RAM: 8 GB or more
•	Storage: 20 GB SSD (for faster read/write and dataset access)
•	Operating System: Windows 11 / Latest Linux distro / macOS Ventura
•	Display: Full HD screen (1920x1080)
•	Network: High-speed internet (minimum 10 Mbps)

3.3.1.2 Server Hosting Environment

For deploying the backend (Flask API), a cloud-hosted or on-premises server can be used. The hardware requirements depend on expected traffic.

Minimum Hosting Requirements (for low traffic / testing)

•	Processor: 1 vCPU
•	RAM: 512 MB to 1 GB
•	Storage: 2–5 GB (for code, logs, and dataset)
•	Operating System: Ubuntu 20.04 LTS or equivalent
•	Internet Access: Required for OpenAI API calls
Recommended Hosting Requirements (for public deployment)

•	Processor: 2 vCPU or more
•	RAM: 2–4 GB
•	Storage: 10 GB SSD
•	Scalability: Optionally scalable container (e.g., Docker) or use of PaaS like Heroku, Render, or AWS Elastic Beanstalk
•	Uptime Guarantee: 99% or above for production use

3.3.1.3 Client-Side (End-User Device Requirements)

As the chatbot is web-based, end users (students or faculty) only require a browser and internet access.

Minimum Requirements

•	Device: Desktop / Laptop / Smartphone / Tablet
•	Browser: Chrome, Firefox, Safari, Edge (latest versions)
•	RAM: 2 GB
•	Internet Connection: 1 Mbps or above
•	Screen Size: Minimum 5-inch for mobile view, 11-inch for desktop

Recommended Requirements

•	Device: Laptop/Desktop with modern browser
•	Browser: Google Chrome (latest), Firefox, or Safari
•	RAM: 4 GB or more
•	Internet Connection: 5 Mbps or above
•	Screen Resolution: 1366x768 or higher


3.3.2 Software Specification

The VIT Campus Query Resolution System is developed with widely accepted, open-source, and scalable software technologies, and this renders the system not only light and efficient but also highly portable and easy to maintain. The software specification defines the platforms, frameworks, libraries, and services utilized for the development, testing, deployment, and execution.

3.3.2.1 Operating System

The system is designed to be cross-platform, meaning it can run on multiple operating systems during both development and deployment.

Supported OS:

•	Windows 10/11
•	Linux distributions (Ubuntu 18.04 or above preferred)
•	macOS Catalina or above


3.3.2.2 Development Tools and Languages

a. Frontend

•	HTML5: For structuring the chatbot interface.
•	CSS3: For styling the login/register forms and chat layout.
•	JavaScript (Vanilla JS): Handles user interactions, form submissions, and communication with the backend API.

b. Backend

•	Python 3.8+: Core language used for backend development.
•	Flask 2.0.1: A lightweight web framework for creating RESTful APIs.
•	Flask-CORS 3.0.10: Enables Cross-Origin Resource Sharing between frontend and backend during development and deployment.
•	pandas 1.3.3: Used for loading, processing, and searching the dataset of predefined FAQs.

c. API Integration

•	OpenAI API (GPT-3.5-turbo): Provides fallback responses for queries not matched in the dataset.
o	API Endpoint: https://api.openai.com/v1/chat/completions
o	Authenticated using a secret API key.
o	Requires internet connectivity.


3.3.2.3 Database / Dataset

Instead of a full database system, the prototype uses a CSV file as a lightweight dataset to store frequently asked questions and answers.

•	File format: vit_college_queries.csv
•	Columns: question, answer
•	Library Used: pandas for reading and querying data


3.3.2.4 Browsers Supported (Frontend Execution)

The frontend is browser-based and can be accessed through any modern web browser without additional plugins.
Supported browsers:

•	Google Chrome (latest versions)
•	Mozilla Firefox
•	Microsoft Edge
•	Safari
Responsive design ensures compatibility with both desktop and mobile screens.
3.3.2.5 Hosting and Deployment Environment

While local development is done using Flask's built-in development server, deployment can be done using:

•	Heroku (PaaS)
•	Render
•	Vercel (for frontend static files)
•	AWS Elastic Beanstalk or EC2
•	PythonAnywhere (for quick prototyping)

For hosting the OpenAI connection, internet access and proper API key management are required.

3.3.2.6 Security and Authentication

•	Frontend Authentication: Currently implemented using JavaScript for prototype/demo purposes.

•	Future Scope: Add backend-based session handling and hashed password storage using Flask-Login and bcrypt.


3.3.2.7 Error Handling and Logging

•	Basic error messages are returned to the frontend in case of:
o	Dataset loading failure
o	API call errors
o	Invalid user input
•	Future implementations can include proper logging using Python’s logging module or third-party tools like Sentry.



4.DESIGN APPROACH AND DETAILS


The VIT Campus Query Resolution System design is motivated by some fundamental software engineering concepts like modularity, separation of concerns, scalability, and maintainability. The system is designed with a client-server architecture in which the frontend (client) communicates with the backend (server) through API calls. The design also employs a hybrid query resolution mechanism involving a static data set along with an AI model to achieve both maximum accuracy and flexibility.

4.1 DESIGN

4.1.1 Design Approach

The chatbot system employs a layer design approach to isolate responsibilities among the different components. This modular design not only makes code easier to read and maintain but also permits the incorporation of new features and services in subsequent versions.

Key Design Principles:

•	Separation of Concerns: UI logic, business logic, and data access are separated into different layers.

•	Hybrid Query Handling: First attempt to resolve queries using a local dataset. If unresolved, escalate the query to OpenAI’s GPT model.

•	Minimalism & Portability: Use of lightweight technologies to ensure the system can run on basic hardware and be deployed with minimal infrastructure.

•	Extensibility: The system is designed to support future additions like database integration, multi-language support, and voice interaction.


4.1.2 System Components

The system consists of the following major components:

1.	Frontend (Client-Side Interface)

o	Built using HTML, CSS, and JavaScript.
o	Handles user registration, login, and chat interface.
o	Sends queries to the backend via HTTP POST requests.
o	Displays chatbot responses in a conversational UI.

2.	Backend (Server-Side Application)

o	Built using Flask (Python).
o	Handles API endpoints for receiving user queries.
o	Searches the local dataset using pandas.
o	Integrates with OpenAI API for AI-generated answers.
o	Responds with appropriate answers or fallback messages.

3.	Dataset

o	Stored as a CSV file containing common questions and their respective answers.
o	Loaded and queried using pandas.
o	Acts as the first line of resolution for common queries.

4.	OpenAI GPT Integration

o	Queries not found in the dataset are forwarded to OpenAI’s GPT-3.5 model.
o	Ensures intelligent handling of uncommon or uniquely phrased questions.
o	Adds flexibility and conversational capabilities to the system.

5.	API Communication Layer

o	The frontend communicates with the Flask backend using AJAX or fetch API in JavaScript.
o	Data is sent as JSON, and responses are rendered in the chat window.


4.2 SYSTEM ARCHITECTURE

![image](https://github.com/user-attachments/assets/9f41157c-951c-48ab-a2de-a9c334b933ce)

 
                                          Fig 4.1 Data flow Diagram



•	User Input: User types a query into the chatbot interface.

•	API Call: JavaScript sends a POST request to the Flask backend.

•	Dataset Matching: The backend preprocesses the input and searches for a match in the dataset.
•	AI Fallback: If no match is found, the query is sent to OpenAI's GPT-3.5 model.

•	Response Generation: A suitable response is generated and sent back to the frontend.

•	UI Update: The chatbot interface displays the response in real time.

![image](https://github.com/user-attachments/assets/d1ce0507-4b42-48f1-9fb7-0c23dd4997d8)

   
                                  Fig 4.2 Class Diagram

5.METHODOLOGY AND TESTING


5.1 MODULE DESCRIPTION

The creation of the VIT Campus Query Resolution System was accomplished using a structured, iterative process based on the Agile Development Model, which focuses on adaptive planning, continuous input, and flexibility. The idea was to develop a functional prototype quickly, implement it in stages, and incrementally improve on functionality and performance.

5.1.1 Requirement Gathering

The process began with identifying the specific needs of the target users—primarily students of VIT. Requirements were gathered from:

•	Student feedback
•	College websites and academic brochures
•	Frequently asked questions from helpdesks and forums

These were organized into categories (admissions, academics, hostel, placements, etc.) and helped shape the structure of the system.

5.1.2 Dataset Creation

A structured CSV file was created to store VIT-specific FAQs. Each row contained:

•	A question 
•	A corresponding answer

This dataset became the system’s first line of query resolution and was formatted for efficient searching using the pandas library.

5.1.3 Frontend Development

The frontend was developed using HTML, CSS, and JavaScript. Key tasks included:

•	Designing the login and registration forms
•	Creating a responsive chat interface
•	Handling form validation and user interactions
•	Implementing fetch API to communicate with the backend

5.1.4 Backend Development

The backend logic was built using Flask. Tasks included:

•	Setting up API routes to handle POST requests from the frontend
•	Implementing logic to match queries with the dataset
•	Integrating OpenAI GPT-3.5 for fallback responses
•	Returning chatbot responses as JSON


5.1.5 Integration

Frontend and backend components were integrated using RESTful API communication. CORS was enabled to allow interaction across different ports or domains. JSON was used as the data format for all communication.

5.1.6 AI Integration

For unmatched queries, the system invoked OpenAI’s GPT model. Integration involved:

•	Configuring the API key securely (in real use, via environment variables)
•	Sending user queries to GPT-3.5
•	Receiving and displaying AI-generated responses

5.1.7 Iterative Refinement

During each development cycle, small enhancements were added, including:

•	Better error handling
•	Chat auto-scroll behavior
•	User feedback messages for loading states or errors


5.2 TESTING

Testing was conducted throughout the development process to ensure that the system functions correctly, performs efficiently, and meets user expectations. Both manual and automated testing strategies were employed.

5.2.1 Unit Testing

Each component was tested in isolation:

•	Dataset match function tested with known and unknown queries
•	API endpoints tested using tools like Postman or cURL
•	Input validation for login and registration tested with empty and invalid data

5.2.2 Integration Testing

Once components were integrated:

•	Queries from the frontend were tested to ensure they reached the backend
•	The switch between dataset response and GPT fallback was validated
•	End-to-end query flow was tested using browser developer tools

5.2.3 Usability Testing

Several users (students) were asked to interact with the chatbot and provide feedback. Key observations:

•	The chatbot was easy to use and understand
•	Responses from the dataset were accurate and fast
•	AI fallback responses were informative, but occasionally verbose

5.2.4 Performance Testing

•	Dataset responses were returned in under 1 second
•	GPT responses took 2–5 seconds depending on network latency
•	The system handled 10+ concurrent requests locally without performance drops

5.2.5 Error Handling Tests

Deliberate errors were introduced to test system robustness:

•	Invalid inputs like blank queries or special characters
•	Network failure during GPT API call
•	Dataset not found or improperly formatted

In each case, the system responded with user-friendly error messages or fallback prompts.

5.2.6 Browser Compatibility Testing

The frontend was tested across major browsers:

•	Google Chrome
•	Mozilla Firefox
•	Microsoft Edge
•	Safari

On both desktop and mobile devices, the interface performed consistently.


6.PROJECT DEMONSTRATION


![image](https://github.com/user-attachments/assets/26abefb7-79f4-4e22-b405-de8386623ff2)
![image](https://github.com/user-attachments/assets/ec88978a-4bd4-4465-b6f9-4bbda11ca0b4)


                               Fig 6.1 Vit vellore college queries dataset



![image](https://github.com/user-attachments/assets/d1e9c2cc-b3d5-4570-8751-46cf562c2ba0)

 
                                               Fig 6.2 Login Page
                                       
 ![image](https://github.com/user-attachments/assets/b395afa8-5106-433f-aa6c-7598fe02d5db)


                                            Fig 6.3 Register Page


![image](https://github.com/user-attachments/assets/8768a9dc-dca2-40cb-a434-c1548a34d4d4)
![image](https://github.com/user-attachments/assets/352975da-11cc-4a37-b5e5-ac7620d2d3e7)


 

                            Fig 6.4 Chatbot handling  queries                                      
7.RESULTS AND DISCUSSION

The college query resolver chatbot was intended to present students with timely and correct answers to routine academic and administrative enquiries. Developed employing Flask for the backend and HTML/CSS/JavaScript for the front end, the system communicates with users through a straightforward web interface. The main knowledge base was a set of 250 frequently asked questions and their answers in CSV format.

In order to properly match user queries to appropriate responses, multiple natural language processing methods were used by the system. Early attempts at simple string matching proved not effective enough for variations in wording. Performance was enhanced through the use of RapidFuzz to perform fuzzy string matching, and Sentence Transformers to facilitate semantic awareness of user queries. With these extensions, the system could effectively identify contextually equivalent queries even where wording varied greatly from queries in the dataset.

In cases where no close match existed, the chatbot effectively fell back on the OpenAI API to produce an accurate and context-sensitive response, with high query coverage. Internally tested, the chatbot proved to have an average response accuracy of about 80%, meaning that four out of five queries were answered appropriately using the local data set and semantic match alone without the need for the fallback.

User interactions showed that the chatbot was able to handle a broad variety of college-related issues, including exam schedules, grading policies, and departmental contacts. Response times were still quick even with the additional semantic processing, and users found the interface easy to use and useful. Overall, the system successfully integrated rule-based and AI-based methods to provide a robust, scalable solution for automating college query resolution




                 8. CONCLUSION AND FUTURE WORK



8.1 CONCLUSION

The VIT Campus Query Resolution System is a significant step towards improving the manner in which students and potential candidates engage with institutional data at Vellore Institute of Technology. With the combination of a structured dataset and AI-driven conversational abilities, the system effectively overcomes the age-old issues of accessibility, responsiveness, and scalability in campus query management.

This chatbot solution offers students a user-friendly, real-time interface where they can ask questions in natural language and receive immediate responses—whether from a predefined dataset or via the intelligent fallback mechanism powered by OpenAI’s GPT-3.5 model. The hybrid approach not only ensures high accuracy for known, frequently asked questions but also offers adaptability for handling dynamic and unforeseen queries.

Technically speaking, the project is a good example of leveraging open-source technologies like Flask, pandas, HTML/CSS/JS, and third-party APIs to create a cost-efficient, scalable solution. Its structure as a mod, lean architecture, and low hardware requirement make it best suited for student projects, campus IT departments, and academic institutions looking for intelligent, digital solutions.

The chatbot improves student experience, lightens the administrative workload, and offers a scalable digital foundation consistent with VIT's vision for innovation and technology. The success of this system reaffirms the role of AI in education, and demonstrates the capability of coupling machine learning with legacy query systems to enhance institutional efficiency.

In summary, the project has achieved its core objectives:

•	Delivering a hybrid chatbot that can handle both static and dynamic queries.
•	Providing a responsive and intuitive user interface.
•	Ensuring reliability, modularity, and scope for scalability.
•	Laying a foundation for VIT-specific digital student support infrastructure.

8.2 FUTURE SCOPE

While the current version of the Campus Query Resolution System meets its initial goals, there is significant scope for enhancement and expansion. Several features can be added to make the chatbot more intelligent, integrated, and accessible:

1. Database Integration

Currently, user credentials and the FAQ dataset are stored in-memory and CSV format respectively. In future iterations:

•	A relational database (like MySQL or PostgreSQL) or NoSQL solution (like Firebase or MongoDB) can be implemented for better data management.
•	Admins can be given the ability to add/update FAQs via a dynamic dashboard rather than editing CSV files manually.

2. Voice-Based Interaction

Adding voice input/output would make the chatbot more inclusive, especially for mobile users or those with accessibility needs. This can be achieved using:

•	Web Speech API (for browsers)
•	Integration with third-party voice recognition tools (e.g., Google Dialogflow, Amazon Alexa APIs)

3. Multilingual Support

To cater to a broader audience, especially international students and regional applicants, the system can be enhanced to support:

•	Multilingual input and responses
•	Language selection features during login or initial interaction

4. Mobile App Integration

A mobile version of the chatbot could be built using frameworks like:

•	React Native or Flutter for cross-platform app development
•	Native Android/iOS development for full mobile functionality

5. Contextual Memory and Chat History

Enhancing the AI’s ability to remember context during a session would enable more human-like conversations. This includes:

•	Session-based context tracking
•	Chat history storage for returning users


6. Admin Portal

Creating an admin dashboard would enable non-technical staff to:

•	Monitor chat activity
•	Update or delete FAQs
•	View analytics and student engagement trends

7. Integration with VIT Systems

To make the chatbot more functional, it can be linked with existing VIT portals such as:

•	Student login/ERP systems
•	Hostel allocation portals
•	Examination timetables and result databases

8. Analytics and Insights

The system can be extended to collect and analyze:
•	Frequently asked questions
•	Peak query times
•	User feedback and satisfaction levels

This data can help VIT’s administrative teams make informed decisions and improve services.




 
 9.REFERENCES

1.	Adamopoulou, E., & Moussiades, L. (2020). An Overview of Chatbot Technology. Artificial Intelligence Applications and Innovations, 373–383.
2.	Dale, R. (2016). The return of the chatbots. Natural Language Engineering, 22(5), 811–817.
3.	Hussain, S., Athula, G. (2018). Extending the domain of intelligent agents: A smart chatbot for campus queries. IJACSA, 9(7).
4.	Fryer, L. K., & Carpenter, R. (2006). Bots as language learning tools. Language Learning & Technology, 10(3), 8–14.
5.	Smutny, P., & Schreiberova, P. (2020). Chatbots for learning: A review of educational chatbots for the Facebook Messenger. Computers & Education, 151.
6.	Brown, T. B., et al. (2020). Language Models are Few-Shot Learners. arXiv:2005.14165.
7.	OpenAI. (2023). GPT-3.5-turbo Technical Overview. https://platform.openai.com
8.	Devlin, J., et al. (2019). BERT: Pre-training of Deep Bidirectional Transformers. arXiv:1810.04805.
9.	Vaswani, A., et al. (2017). Attention is All You Need. NeurIPS.
10.	Touvron, H., et al. (2023). LLaMA: Open and Efficient Foundation Language Models. arXiv:2302.13971.
11.	Grinberg, M. (2018). Flask Web Development. O’Reilly Media.
12.	Mozilla Developer Network. JavaScript Guide. https://developer.mozilla.org/en-US/docs/Web/JavaScript
13.	Flask Documentation. https://flask.palletsprojects.com/
14.	pandas Documentation. https://pandas.pydata.org/
15.	JavaScript Fetch API – MDN Docs. https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
16.	Nielsen, J. (1994). Usability Engineering. Morgan Kaufmann.
17.	Sommerville, I. (2011). Software Engineering (9th ed.). Pearson.
18.	Pressman, R. S., & Maxim, B. R. (2014). Software Engineering: A Practitioner's Approach. McGraw-Hill Education.
19.	Beizer, B. (1990). Software Testing Techniques. Van Nostrand Reinhold.
20.	IEEE Std 830-1998 - IEEE Recommended Practice for Software Requirements Specifications.
21.	Georgia State University – Pounce chatbot case study.
22.	Deakin University Genie Assistant – https://www.deakin.edu.au/students/genie
23.	North Carolina State University: WolfBot implementation.
24.	Arizona State University AI assistant overview – EdTech Reports.
25.	University of Murcia’s MoBot – A Moodle chatbot for student services.
26.	RapidFuzz Documentation – https://maxbachmann.github.io/RapidFuzz/
27.	SentenceTransformers Documentation – https://www.sbert.net/
28.	Heroku Deployment Documentation – https://devcenter.heroku.com/
29.	Firebase Authentication – https://firebase.google.com/docs/auth
30.	PythonAnywhere Hosting Platform – https://www.pythonanywhere.com/
31.	OWASP Top 10 – Application Security Risks.
32.	ISO/IEC 27001 – Information Security Management.
33.	GDPR & AI Compliance in Educational Systems.
34.	Floridi, L., & Cowls, J. (2019). A unified framework of five principles for AI in society. Harvard Data Science Review.
35.	Binns, R. (2018). Fairness in Machine Learning: Lessons from Political Philosophy. Proceedings of the 2020 ACM FAT.
36.	Molich, R., & Nielsen, J. (1990). Improving a Human-Computer Dialogue. Communications of the ACM.
37.	Metrics for Evaluating Chatbot Quality – Chatbot Magazine.
38.	Bot Analytics: Key Metrics and KPIs – Chatbots Life.
39.	Google Analytics Integration for Web Apps – Official Docs.
40.	Web Speech API – https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API
41.	Dialogflow CX by Google – https://cloud.google.com/dialogflow
42.	Rasa Open Source – https://rasa.com/
43.	Flutter for Cross-Platform Development – https://flutter.dev/
44.	TensorFlow.js – AI in the browser. https://www.tensorflow.org/js
45.	Hugging Face Transformers – https://huggingface.co/transformers/
46.	Winkler, R., & Söllner, M. (2018). Unleashing the Potential of Chatbots in Education: A State-of-the-Art Analysis. Proceedings of the 19th International Conference on Wirtschaftsinformatik.
47.	Jia, J. (2019). The Use of Chatbots in Education: A Review of Empirical Research. Journal of Educational Technology Development and Exchange, 12(1).
https://doi.org/10.18785/jetde.1201.01
48.	Mihailidis, M., Kondyli, V., & Mouzakidis, S. (2020). Design and Development of an Academic Chatbot Using Rule-Based and NLP Approaches. Journal of Web Engineering, 19(8), 1207–1230.
49.	Radford, A., Wu, J., Child, R., Luan, D., Amodei, D., & Sutskever, I. (2019). Language Models are Unsupervised Multitask Learners. OpenAI Technical Report.
https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf
50.	Gamage, S. H., de Silva, E., & Gunawardhana, N. (2021). Chatbots for Online Student Support: A Review of Benefits and Challenges. International Journal of Educational Technology in Higher Education, 18(1).
https://doi.org/10.1186/s41239-021-00267-1
51.	Page, L. C., & Gehlbach, H. (2017). How Pounce the Chatbot Helped Increase College Enrollment Rates. Behavioral Science and Policy, 3(2), 53–65.
https://doi.org/10.1353/bsp.2017.0016
52.	Deakin University. (2018). Meet Genie: Your Personalized Digital Assistant.
https://www.deakin.edu.au/students/genie
53.	Abd-Alrazaq, A., Alajlani, M., Alalwan, A. A., Bewick, B. M., Gardner, P., & Househ, M. (2020). An Overview of the Features of Chatbots in Mental Health: A Scoping Review. BMC Medical Informatics and Decision Making, 20(1).
https://doi.org/10.1186/s12911-020-01239-1
54.	OpenAI. (2023). OpenAI API Documentation.
https://platform.openai.com/docs
55.	Flask Documentation. (2023). Flask: Web Development One Drop at a Time.
https://flask.palletsprojects.com/
56.	pandas Documentation. (2023). pandas: Python Data Analysis Library.
https://pandas.pydata.org/
57.	Mozilla Developer Network (MDN). (2023). Web APIs and JavaScript Documentation.
https://developer.mozilla.org/en-US/



APPENDIX A – Sample Code


![image](https://github.com/user-attachments/assets/a923a4ed-57ad-4c1f-8970-06c7c3e3cf34)
![image](https://github.com/user-attachments/assets/60be6b31-4075-4635-89ce-d03ae8c48ed8)
![image](https://github.com/user-attachments/assets/d157d42a-7117-47f4-95a0-82fd2dd77fd7)
![image](https://github.com/user-attachments/assets/efc8ba49-6238-4847-a79e-c95189f1e824)
![image](https://github.com/user-attachments/assets/6f78ebc2-2588-419d-9e13-75bb4b05b1a3)
![image](https://github.com/user-attachments/assets/c75841a8-5056-4624-a31a-9cd938fca38f)
![image](https://github.com/user-attachments/assets/9ea85c44-f7c4-498e-bac9-7309b4782bf3)
![image](https://github.com/user-attachments/assets/6d32fdfe-1fce-4d67-aa71-b282edf0f1d3)
![image](https://github.com/user-attachments/assets/ea3a74af-3817-4a7d-af8f-69751b1cee42)
![image](https://github.com/user-attachments/assets/746e41f1-3f3f-422c-a664-ac5c2818800f)
![image](https://github.com/user-attachments/assets/74fda733-9b5e-4368-9e9d-2115dcf93195)



