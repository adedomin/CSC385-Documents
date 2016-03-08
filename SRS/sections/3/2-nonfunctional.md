3.2. Nonfunctional Requirements
-------------------------------

The Application has many security and operational concerns. Users can potentially lose money through insecurities so it's critical the application is built securely and to allow for operations to assist users who may be defrauded.

### 3.2.1. General Security

Security is paramount for the application. The application must make use of cryptographically secure transportation like TLS.
To ensure our user's security, it is required that architecture, such as the database, must be password secured or behind a firewall preventing it from listening to the outside world.

The web application must make use of framework technologies.
Frameworks are built and designed around securely and easily serving content over the web.
Security concerns pertaining to the framework are also handled externally saving time.

### 3.2.2. Scalibility

The application should be designed to be capable of scaling.
The Application should be capable of being load balanced to allow for easy scalibility.
To ensure the application can be load balanced, the application should rely on external servers for storage and databases.
So The application, or applications, shall connect to remote storage pools and databases for their persistent storage needs.
This will allow all the running instances of the app to share their states with one another.

Databases, like MongoDB, generally support mechanisms like sharding to allow for scaling up database requirements.
Because of this, MongoDB was chosen for this application.
MongoDB also has the ability to serve as a general purpose filesystem using GridFS.

### 3.2.3. Operations
