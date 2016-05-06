---
title: 
	- Architecture Section 
author:
	- Jeremy Drexler
date: \today{}
geometry: 
	- margin=3cm
fontsize: 
	- 12pt
fontfamily: 
	- mathpazo
header-includes:
	- \usepackage{fancyhdr}
	- \pagestyle{fancy}
	- \fancyfoot[L]{eBanking Webapp}
	- \fancyfoot[R]{\thepage}
---

5. Architecture
===============

5.1 Architecture Overview
-------------------------

The architecture of the e-banking system needs to allow a user to communicate through a web interface, authenticate and
manage customer data, and allow transactions in real time (while putting a stop to any transaction in which an error 
occurs such as insufficient funds, or a hold being placed on the account). For those reasons we decided to use a 
three tier online transaction processing architecture, which is often used for online banking architecture. By using this
model we allow ourselves to avoid potential bottlenecks that may arise if we were instead using a client-server 
architecture. [^1]

[^1]: See Figure 1:2.1.1 in the SRS

5.2 Presentation layer
----------------------

The front end presentation layer (the e-banking website) is detailed in section 4, and describes the functionality and 
various actions that the customer can take while interacting with the e-banking system, highlighting the usability of 
the service. It also shows what the interface may end up looking like.

5.3 Domain Layer
-----------------

This is where authentication of user information will take place as well as data processing/management. 

5.4 Technical Services Layer
----------------------------

A back-end MongoDB database which will store user and transaction data. This will be accessed by the user when a request
has been made and their information verified. The entities and their relationships are detailed in section 3.
