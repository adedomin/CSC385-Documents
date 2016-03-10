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
This further supports load balancing the application among several machines.

This requirement also plays into high availability, since a failure in one sub system will not cause total failure.
This is because the data models and the server side logic is distributed.

### 3.2.4. Continuous Integration and Deployment

The system's source code must be managed in a way that allows for automated building tools like Jenkins to generate deployable and versioned binaries.
Binaries should be managed in a way that allows for automatic deployment to production systems.

This implies all code and configurations need to be hosted in a remote source code management system such as a git repository hosted on github.
Binaries must be sendable to a server with accompanying versioning information.
Binaries can be sourced from this binary repository by deployment tools like ansible or puppet.
From there, ansible or puppet can install and run the necessary configurations and binaries.

### 3.2.3. Operations

There should be a portal or external views and applications that allow operations teams to view and modify portions of the database.
The system should also monitor anything that can and/or will go wrong so operations should be able to quickly recover from outages.

