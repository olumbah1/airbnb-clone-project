# airbnb-clone-project
Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.

# Project Goals
1.User Management: Implement a secure system for user registration, authentication, and profile management.
2.Property Management: Develop features for property listing creation, updates, and retrieval.
3.Booking System: Create a booking mechanism for users to reserve properties and manage booking details.
4.Payment Processing: Integrate a payment system to handle transactions and record payment details.
5.Review System: Allow users to leave reviews and ratings for properties.
6.Data Optimization: Ensure efficient data retrieval and storage through database optimizations.

# Technology Stack
1.Django: A high-level Python web framework used for building the RESTful API.
2.Django REST Framework: Provides tools for creating and managing RESTful APIs.
3.PostgreSQL: A powerful relational database used for data storage.
4.GraphQL: Allows for flexible and efficient querying of data.
5.Celery: For handling asynchronous tasks such as sending notifications or processing payments.
6.Redis: Used for caching and session management.
7.Docker: Containerization tool for consistent development and deployment environments.
8.CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

# Team Roles
Business analyst (BA): 
Translates customer business needs into requirements
Understands customer’s business processes

Responsibility
A business analyst dives deep into a customer’s workflows and analyzes stakeholder feedback to help a client formulate what their wants look like and align a customer’s vision with what a development team is producing. They translate an abstract product idea into a set of tangible requirements.

# Product owner (PO)
Holds responsibility for a product vision and evolution
Makes sure the final product meets customer requirements

Responsibility
Holding more responsibility for a product’s success than any other development team member, a product owner is a decision-maker. Balancing both business needs and market trends, they define a business strategy, shape up the product vision, make sure it satisfies customer needs, and manage a product backlog.

# Project manager (PM)
Makes sure a product or its part is delivered on time and within budget
Manages and motivates the software development team

Responsibility
In Agile projects where the focus is on self-management, transparency, and shared ownership, a PM sets up the vision of a product, maintains transparency, fosters communication, searches for improvements in the development process, and makes sure a team delivers more value with each iteration.

# UI/UX designer
Transforms a product vision into user-friendly designs
Creates user journeys for the best user experience and highest conversion rates

Responsibility
A UI designer devises intuitive, easy-to-use, and eye-pleasing interfaces for a product, while the UX part stands for thinking out an entire journey of a user’s interaction with a product.

# Software architect
Designs a high-level software architecture
Selects appropriate tools and platforms to implement the product vision
Sets up code quality standards and performs code reviews

Responsibility
An architect is an expert-level software engineer who makes executive software design decisions on behalf of an app development team.

# Software developer
Engineers and stabilizes the product
Solves any technical problems emerging during the development lifecycle

Responsibility
A software developer does the actual job and codes an application. And just like an app features a front end and a back end, there are front-end and back-end developers

# Quality assurance (QA) engineer
Makes sure an application performs according to requirements
Spots functional and non-functional defects

Responsibility
The job of a quality assurance engineer is to verify whether an application meets the requirements—both functional and non-functional. Functional requirements define what an application should do, while non-functional requirements specify how it should do that.

# Test automation engineer
Designs a test automation ecosystem
Writes and maintains test scripts for automated testing

Responsibility
A test automation engineer is there to help you test faster and better. To enable that, they develop test automation scripts—small programs that provide reliable and continuous feedback on application quality without any human involvement

# DevOps engineer
Facilitates cooperation between development and operations teams
Builds continuous integration and continuous delivery (CI/CD) pipelines for faster delivery

Responsibility
DevOps engineers serve as a link between the two teams, unifying and automating the software delivery process and helping strike a balance between introducing changes quickly and keeping an application stable.


# Technology Stack
Django, Django REST Framework, PostgreSQL, GraphQL, Celery, Redis, Docker, CI/CD Pipelines

Django: A high-level Python web framework used for building the RESTful API.
Django REST Framework: Provides tools for creating and managing RESTful APIs.
PostgreSQL: A powerful relational database used for data storage.
GraphQL: Allows for flexible and efficient querying of data.
Celery: For handling asynchronous tasks such as sending notifications or processing payments.
Redis: Used for caching and session management.
Docker: Containerization tool for consistent development and deployment environments.
CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

# Database Design
Users, Properties, Bookings, Reviews, and Payments

1. User

Fields:

id (unique identifier)

username

email

password (hashed)

profile_picture

is_host (boolean indicating if user can list properties)

Relationships:

A User can be a host who owns multiple Properties.

A User can book multiple Properties.

A User can write multiple Reviews.

A User can have multiple Payments (for bookings).

2. Property

Fields:

id

host (ForeignKey to User)

title

description

address

price_per_night

max_guests

amenities (e.g., wifi, kitchen)

Relationships:

Each Property belongs to one User (host).

A Property can have many Bookings.

A Property can have many Reviews.

3. Booking

Fields:

id

property (ForeignKey to Property)

guest (ForeignKey to User)

start_date

end_date

total_price

status (e.g., pending, confirmed, canceled)

Relationships:

A Booking belongs to one Property.

A Booking belongs to one User (guest).

A Booking can have one or more Payments associated.

4. Review

Fields:

id

booking (ForeignKey to Booking)

reviewer (ForeignKey to User)

rating (e.g., 1-5 stars)

comment

created_at

Relationships:

A Review belongs to one Booking.

A Review belongs to one User (reviewer).

Through Booking, the review indirectly relates to a Property.

5. Payment

Fields:

id

booking (ForeignKey to Booking)

payer (ForeignKey to User)

amount

payment_method (e.g., credit card, PayPal)

payment_status (e.g., completed, pending)

payment_date

Relationships:

A Payment is associated with one Booking.

A Payment is made by one User (payer).