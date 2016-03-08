2.3. System Overview
--------------------

The automated banking system is itself in the domain of a larger banking system.
Excluding functions of the banking firm irrelevant to the automated banking system.

![2.3.1.[^fig2]](./sections/2/media/image2.jpeg){width="6.5in" height="3.688888888888889in"}

[^fig2]: System context diagram of the automated banking system. Highlights the outside forces affecting the system.

  * The management to whom the system reports. This party is responsible for system maintenance and evolution.

  * The customers to whom the system services. At a fundamental level, the users communicate with the system through a typical HTTPS connection. The user initiates the communication by sending a request to the system, to which the system responds accordingly.  
  * The physical site on which the database and/or web server is located. All system components pertaining to the:
	* Hardware and software
	* Utilities
	* Space

### 2.3.2. Web Interface Overview

![2.3.2.1.[^fig3]](./sections/2/media/image3.jpeg){width="6.5in" height="5.188888888888889in"}

[^fig3]: Clickstream diagram for the system’s front-end interface.

This is a representation of the tasks a user can complete in a given session with the banking system.
The diagram assumes the user begins on the home page, in which they may or may not be logged in.
The home page shall display different content depending on the login status of the user.

If logged in, the user shall have an option to make a transaction, view their account information in more detail, and log out of their current session.
Should the user attempt to make a transaction, they shall have the option to pay current bills or transfer funds.
A page appearing after the transaction will alert the user to whether or not the transaction was successful before redirecting them back to the home page.

