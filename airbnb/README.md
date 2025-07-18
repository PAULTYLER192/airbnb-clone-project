    Airbnb Clone
Overview:
This project is a web application inspired by Airbnb, built to connect hosts offering short-term accommodations with guests seeking unique stays. 
Developed using Python (Django) and PostgreSQL, it provides core functionalities such as user authentication, property listings, search with filters, booking management, and a review system. 
The platform aims to deliver a seamless, secure, and user-friendly experience, mimicking Airbnb’s peer-to-peer marketplace for rentals and experiences.


Team Roles and Responsibilities
1. Project Manager: Oversees project planning, task allocation, and timeline management to ensure timely delivery of the application’s core features while coordinating team efforts and communication.
2. Backend Developer: Builds the server-side logic, database models, and APIs using Django and PostgreSQL, implementing features like listing creation, booking processing, and search functionality.
3. Frontend Developer: Designs and develops the user interface using HTML, CSS, JavaScript, and Bootstrap, ensuring a responsive and intuitive experience for browsing listings and making bookings.
4. Database Administrator: Manages the PostgreSQL database, designing schemas, optimizing queries, and ensuring data integrity for efficient storage of users, listings, and bookings.
5. DevOps Engineer: Configures development and production environments, deploys the application (e.g., on Heroku), and sets up CI/CD pipelines for automated testing and deployment.
6. QA Engineer: Develops and executes tests to ensure the application is reliable, testing features like search filters, booking logic, and UI responsiveness to deliver a bug-free product.


  Technology Stack
1. Python: The core programming language used to build the backend logic and integrate libraries for features like geolocation and image processing.
2. Django: A Python web framework for developing the backend, handling routing, user authentication, database interactions, and rendering dynamic templates.
3. PostgreSQL: A relational database for storing user profiles, property listings, bookings, and reviews, supporting complex queries and scalability.
4. HTML/CSS/JavaScript: Frontend technologies for structuring, styling, and adding interactivity to web pages, such as listing displays and booking forms.
5. Bootstrap: A CSS framework for creating responsive, user-friendly interfaces with pre-built components like cards and forms.
6. Git and GitHub: Version control system and hosting platform for tracking code changes and collaborating on the project.
7. Stripe: A payment processing API for simulating booking transactions securely in test mode.
8. geopy: A Python library for geocoding addresses and enabling location-based search for listings.
9. Django REST Framework : A Django extension for building RESTful APIs to support dynamic frontends or mobile apps.
10. Cloudinary : A cloud service for storing and serving property images uploaded by hosts.


    Database Design
The database is structured to support the core functionalities of the Airbnb clone, including user management, property listings, bookings, reviews, and payments.
The following key entities are defined, with their important fields and relationships:

1. Users:
   Fields:
   - username: Unique identifier for the user (e.g., “john_doe”).
   - email: User’s email for login and notifications.
   - first_name: User’s first name.
   - last_name: User’s last name.
   - is_host: Boolean indicating if the user is a host.
Relationships: A user can host multiple properties (one-to-many) and make multiple bookings or reviews as a guest (one-to-many).

2. Properties:
   Fields:
   - title: Name of the property (e.g., “Cozy Nairobi Apartment”).
   - description: Detailed description of the property.
   - price: Nightly price (e.g., 5000.00 KES).
   - city: Location city (e.g., “Nairobi”).
   - host: The user who owns the property (foreign key to User).
Relationships: A property belongs to one host (many-to-one), can have multiple bookings (one-to-many), multiple reviews (one-to-many), and multiple amenities (many-to-many).

3. Bookings:
   Fields:
   - property: The booked property (foreign key to Property).
   - guest: The user making the booking (foreign key to User).
   - check_in: Start date of the stay.
   - check_out: End date of the stay.
   - total_price: Total cost of the booking.
Relationships: A booking belongs to one property and one guest (many-to-one) and has one payment (one-to-one).

4. Reviews:
   Fields:
   - property: The reviewed property (foreign key to Property).
   - guest: The user leaving the review (foreign key to User).
   - rating: Rating from 1 to 5 stars.
   - comment: Written feedback.
Relationships: A review belongs to one property and one guest (many-to-one).

5. Payments:
   Fields:
   - booking: The associated booking (foreign key to Booking).
   - amount: Payment amount.
   - stripe_payment_id: Stripe’s transaction ID.
   - status: Payment status (e.g., “succeeded”, “pending”).
Relationships: A payment belongs to one booking (many-to-one).

6. Amenities :
   Fields:
   - name: Name of the amenity (e.g., “Wi-Fi”).
Relationships: An amenity can be associated with multiple properties, and a property can have multiple amenities (many-to-many).



Feature Breakdown
- User Management:
Enables users to register, log in, and manage profiles with host or guest roles.
Supports secure authentication and profile customization, ensuring personalized experiences for booking or hosting properties.
Provides a foundation for restricting actions (e.g., only hosts can create listings).

- Property Management:
Allows hosts to create, edit, and delete property listings with details like title, price, and city.
Enables guests to browse listings, forming the core of the platform’s rental marketplace.
Supports image uploads for visually appealing property displays.

- Search with Filters:
Lets users search properties by criteria like location, price, and availability dates.
Enhances user experience by providing relevant, filtered results for quick property discovery.
Supports dynamic filtering for a seamless search interface.

- Booking System:
Facilitates reserving properties by specifying check-in and check-out dates with availability validation.
Calculates total costs and links bookings to users and properties, enabling secure transactions.
Provides confirmation for successful bookings, mimicking Airbnb’s reservation flow.

- Review System:
Allows guests to leave ratings and comments for properties after their stay.
Displays reviews on property pages to build trust and inform user decisions.
Enhances credibility through user-generated feedback.

- Payment Processing:
Integrates Stripe for secure, test-mode payment processing for bookings.
Records transaction details and status, ensuring a reliable payment workflow.
Simulates Airbnb’s payment system for a realistic user experience.

- Messaging System (Optional):
Enables hosts and guests to communicate about bookings or inquiries.
Supports direct messaging linked to properties, improving coordination and user engagement.



CI/CD Pipeline
Continuous Integration/Continuous Deployment (CI/CD) pipelines automate the process of building, testing, and deploying code changes, ensuring a reliable and efficient development cycle for the Airbnb clone. They enhance code quality by running tests and linters on every change and streamline deployments to production, enabling rapid iteration and collaboration.
Tools Used:
- GitHub Actions: Automates CI/CD workflows, running tests and linters on code pushes and deploying to production if tests pass.
- Docker: Packages the application with dependencies for consistent testing and deployment environments.
- Heroku: Hosts the production application, integrating with GitHub Actions for automatic deployments.
- Pytest: Runs unit and integration tests to validate features like bookings and property management.
- Flake8: Lints Python code to ensure style consistency and quality in the CI pipeline.
- Bandit : Scans for security vulnerabilities in Python code, enhancing API security.
