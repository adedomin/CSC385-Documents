---
title: 
	- Design Section 3
author:
	- Anthony DeDominic
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

3.3. Controllers and Middlewares
--------------------------------

### 3.3.1 Helper Controller

This controller shall offer helpful middlewares that are shared among all the controller.
This section shall discuss the necessary design and functions that should be in this object.

  * generateToken(next)
    * This function shall make use of the node.js crypto primitives to generate a 48 bytes of random data. The next() shall be a callback which takes the parameters of err and token. If err is not null, assume that something went wrong. For ease of use, the function will convert the random bytes into a hexadecimal string.
  * getUser: function (username, next) {
    * Refer to the DAO's in section 3.1.1. This function is more for abstracting dependencies.
  * updateUser: function (username, changes, next)
    * Refer to DAO 3.1.1. This function gets the user using the DAO and then saves changes passed in as a parameter.
  * addAccountToUser: function (username, accountid, next)
    * Refer to DAO 3.1.1. This function does similar to above but it adds an account specifically.
  * removeUser: function (username, next)
    * Refer to DAO 3.1.1.
  * getSession: function (sessionid, next)
    * This function is used to verify session information the user passed in. Specifically it will make a database call to the session db. If a value is returned, the session is determined to be accurate.
  * setUser: function (user, next) 
    * Refer to DAO 3.1.1. This is just a saveUser() abstraction for dependency reasons.
  * setSession: function (session, next)
    * Creates a new session by storing the user's name in association with a randomly generated token.
  * removeSession: function (sessionid, next)
    * Remove a session by Id.
  * getAccount: function (accountid, next)
    * Abstraction of DAO 3.1.2. Fetches an account by its id.
  * checkAccountAccess: function (username, account)
    * This function will read the ACL and return if the user has access or not.  
  * transferAccountBalance: function (to, from, change, next)
    * Transfers amount by manipulating the two accounts and saving them using the account DAO (3.1.2).  It also creates two new histories to save using the History DAO (3.1.3).
  * createAccount: function (account, next)
  * updateAccount: function (account, next)
  * getTransactions: function (owner, next)
  * addTransaction: function (transaction, next)
  * removeTransaction: function (transactionId, owner, next)
  * checkPass: function (password, hash, next)
  * hashPass: function (password, next)
  * getHistory: function(accountId, next)
