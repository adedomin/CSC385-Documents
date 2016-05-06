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

3.1. DAOs
---------

Data is a huge part of the application.
In order to abstract data access from the code, the Data Access Object design pattern should be used.

Below is a list of needed objects for accessing the various datas for the application.

### 3.1.1. UserDAO

The UserDAO should implement the following interface.

  * getUser(String name, function)
  * saveUser(User user, function)
  * deleteUser(String name, function)

Please see definitions for what the verbs (get, save, delete) mean in this context.

All of the above should take a callback as an argument.

The callback arguments must take the following.

  * getUser() -> function (err, user)
  * saveUser() -> function (err)
  * deleteUser() -> function (err, user)

err is null if no error, as is common in most JavaScript (Node.js) applications.
Otherwise it is an object which contains error information.

user is the User object that was retrieved or removed.

The UserDAO should include member variables that make sense for the object.

  * db -> some kind of database connector

Other variables may be required, for instance for Relational, SQL like databases, it may be necessary to create Query Factories.

in that case:

  * selectUserQueryFactory()
  * updateUserQueryFactory()
  * deleteUserQueryFactory()

These factories should return query objects that will properly handle sanitizing user inputs by using some prepared statements.

### 3.1.2. AccountDAO

This DAO should implement the following interface.

  * getAccount(String accountId, function)
  * saveAccount(Account account, function)
  * deleteAccount(String accountId, function)

Please see definitions for what the verbs (get, save, delete) mean in this context.

The callback arguments must take the following.

  * getAccount() -> function (err, account)
  * saveAccount() -> function (err)
  * deleteAccount() -> function (err, account)

err is null if no error, as is common in most JavaScript (Node.js) applications.
Otherwise it is an object which contains error information.

account is the Account object that was retrieved or removed.

The AccountDAO should include member variables that make sense for the object.

  * db -> some kind of database connector

Other variables may be required, for instance for Relational, SQL like databases, it may be necessary to create Query Factories.

in that case, these query factory objects MUST implement the following functions:

  * selectAccountQueryFactory()
  * updateAccountQueryFactory()
  * deleteAccountQueryFactory()

These factories should return query objects that will properly handle sanitizing user inputs by using some prepared statements.

### 3.1.3. HistoryDAO

This DAO shall access user's transaction and other account changes.

  * getHistory(String accountId, function)
  * saveHistory(History history, function)
  * deleteHistory(String historyId, function)

Please see definitions for what the verbs (get, save, delete) mean in this context.

The callback arguments must take the following.

  * getHistory() -> function (err, history)
  * saveHistory() -> function (err)
  * deleteHistory() -> function (err, history)

err is null if no error, as is common in most JavaScript (Node.js) applications.
Otherwise it is an object which contains error information.

History is the History object that was retrieved or removed.

The HistoryDAO should include member variables that make sense for the object.

  * db -> some kind of database connector

Other variables may be required, for instance for Relational, SQL like databases, it may be necessary to create Query Factories.

In that case, these query factory objects MUST implement the following functions:

  * selectHistoryQueryFactory()
  * updateHistoryQueryFactory()
  * deleteHistoryQueryFactory()

These factories should return query objects that will properly handle sanitizing user inputs by using some prepared statements.

### 3.1.5. TransactionsDAO

This DAO should only be used by core logic to persist pending transactions.

  * getAllTransactions(function)
  * setNewTransaction(Transaction transaction, function)
  * deleteTransaction(String transactionid, function)

This object is special, as it is intended to persist potentially interrupted transactions.

The callback arguments must take the following:

  * getAllTransactions() -> function (err, transactions)
  * saveNewTransaction() -> function (err, transaction)
  * deleteTransaction() -> function (err)

The callback for getAllTransactions should be expected to register all the transactions to be executed in the future.

