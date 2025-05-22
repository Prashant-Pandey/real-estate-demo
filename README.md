# Project Title: PropTrading - Real Estate Investment Platform

**Live Demo Link:**
`[Live Demo Not Yet Deployed]`

**Project Description:**
PropTrading is a web application designed to simulate a real estate investment platform. It allows users to browse properties (conceptually), subscribe for updates, and manage their accounts. This project demonstrates a full-stack web application built with Node.js, Express, and Handlebars, connected to a MySQL database.

**Key Features:**
- **User Authentication:** Secure user registration and login functionality (Note: User creation part in `create_database.js` is commented out, implying manual setup or a different process for user table creation).
- **Subscription Service:** Users can subscribe to receive updates via their contact number. The `proptrading_subscription_list` table supports this.
- **Property Viewing:** (Conceptual based on project theme and screenshots; no direct routes for property data interaction are visible in the provided route files).
- **Static Content Pages:** Informational pages such as 'About Us', 'How It Works', 'Projects', and 'Contact'.
- **Responsive Design:** (Assumed based on typical web development practices using Bootstrap, which is present).

**Technologies Used:**
- **Backend:** Node.js, Express.js
- **Frontend:** HTML, CSS (Bootstrap), JavaScript, Handlebars (hbs) for templating.
- **Database:** MySQL
- **Templating Tools:** Handlebars (Ember.js is listed in `package.json` scripts, likely for Handlebars precompilation, not as a core framework for the app itself).
- **Version Control:** Git & GitHub

**Technical Highlights:**
- **MVC-like Architecture:** Leveraged Express.js for routing and controllers, with Handlebars for views, organizing code in a structured manner.
- **Database Integration:** Implemented MySQL database connectivity. The application is configured to connect to both local and remote MySQL instances.
- **Templating Engine:** Utilized Handlebars (hbs) for dynamic server-side rendering of HTML pages.

**Screenshots:**
*These screenshots provide a glimpse into the application's UI and intended functionality.*

![Application Hero Section](./project-images/site-hero.png)
*Caption: The main landing page showcasing the platform's value proposition and encouraging user engagement.*

![Platform Workflow](./project-images/how-it-works.png)
*Caption: A visual explanation detailing the operational flow of the PropTrading platform for prospective users and investors.*

![Property Listings Page](./project-images/prop-listing.png)
*Caption: An example of the property listings interface, where users would theoretically browse and select investment opportunities.*

**Setup and Installation:**
1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/your-repository-name.git
    cd your-repository-name
    ```
    *(Replace `your-username/your-repository-name` with the actual repository URL if different)*
2.  **Install dependencies:**
    ```bash
    npm install
    ```
3.  **Set up the database:**
    - Ensure you have MySQL installed and running.
    - **Database Configuration:** The application uses `routes/database.js` for database connection settings. It provides configurations for both a remote MySQL instance (`remotemysql.com`) and a local setup.
        - **Remote Setup (as per `database.js`):**
            - Host: `remotemysql.com`
            - User: `KSL0ItJfdv`
            - Password: `nsvaAxdXpm`
            - Database: `KSL0ItJfdv`
            - Port: `3306`
        - **Local Setup (example from `database.js`):**
            - Host: `localhost`
            - User: `prashant` (or your local MySQL username)
            - Password: `root` (or your local MySQL password)
            - Database: `proptrading`
            - Port: `3306`
    - **Table Creation:**
        - The script `routes/create_database.js` is intended to set up tables.
        - It attempts to connect using the `dbconfig.connection` (which points to the remote DB by default in the provided code).
        - It explicitly creates the `proptrading_subscription_list` table.
        - The creation of `proptrading_users` table is commented out in `routes/create_database.js`. You might need to uncomment it or use an external SQL script to create it:
          ```sql
          CREATE TABLE `proptrading_users` (
              `UserID` INT UNSIGNED NOT NULL AUTO_INCREMENT,
              `email` VARCHAR(225) NOT NULL,
              `password` VARCHAR(60) NOT NULL,
              `proj` VARCHAR(225),
              `contact` VARCHAR(225),
              `comment` VARCHAR(225),
              PRIMARY KEY (`UserID`)
          );
          ```
        - The `proptrading_contact_me` table is defined in `dbconfig.tables` but not created by `create_database.js`. You may need to create it manually:
          ```sql
          CREATE TABLE `proptrading_contact_me` (
              `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
              `name` VARCHAR(255),
              `email` VARCHAR(255),
              `message` TEXT,
              PRIMARY KEY (`id`)
          );
          -- Note: Schema for proptrading_contact_me is assumed, adjust as necessary.
          ```
    - To run the database creation script (after configuring `routes/database.js` to point to your desired MySQL instance, likely local for initial setup):
        ```bash
        node routes/create_database.js
        ```
        *(Ensure `routes/database.js` is correctly pointing to your local or desired remote database before running this.)*
4.  **Run the application:**
    ```bash
    npm start
    ```
    The application will start, and by default, it listens on `http://localhost:3000` (as configured in `bin/www`).

**Usage:**
- Navigate to `http://localhost:3000` in your web browser.
- Sign up for a new account or log in. (Note: User table creation might require manual steps as outlined above).
- Explore the static pages: About, How it Works, Projects, Contact.
- Use the subscription feature (e.g., on the homepage) to provide a contact number.

**API Endpoints (Main Routes from `app.js` and `routes/index.js`):**
- `GET /`: Renders the home page (`views/index.hbs`).
- `GET /about`: Renders the about page (`views/about.hbs`).
- `GET /working`: Renders the 'How it Works' page (`views/howitworks.hbs`).
- `GET /projects`: Renders the projects page (`views/projects.hbs`).
- `GET /contact`: Renders the contact page (`views/contact.hbs`).
- `GET /login`: Renders the login/signup page (`views/login.hbs`).
- `POST /subscribe`: Handles user subscription requests (saves contact number to `proptrading_subscription_list`).
- `POST /auth`: Handles user login and registration (interacts with `proptrading_users` table).
- `GET /users`: (Defined in `app.js` to use `routes/users.js`) Currently, `routes/users.js` responds with a simple string 'respond with a resource' and is not fully implemented for user management.

**Future Enhancements (Optional):**
- Fully implement property listings with dynamic data (e.g., detailed views, search filters, adding new properties).
- Develop the `/users` section for comprehensive user profile management (e.g., view past activity, update details).
- Create an admin panel for managing properties, users, and subscriptions.
- Integrate a payment gateway for simulating real investment transactions.
- Add more robust error handling and input validation throughout the application.

**Author/Contact:**
*(Please update with your details)*
- **Name:** [Your Name/Team Name]
- **LinkedIn:** `[Your LinkedIn Profile URL (Optional)]`
- **GitHub:** `[Your GitHub Profile URL (Optional)]`
- **Project Repository:** `[Link to this GitHub Repository]`

This README provides a comprehensive overview for understanding, setting up, and running the PropTrading application.