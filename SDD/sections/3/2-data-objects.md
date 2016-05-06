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

3.2. Data Objects
------------------

### 3.2.1 User

The user object is the object that holds all the pertinent user information.

It should include all the following data:

  * String username
  * String email <- may be same as above
  * String hashedPassword <- includes salt, rounds and algorithms used.
  * [String] accountIds

The array merely points to id's of the owned account objects, this is practical since accounts can be shared and have no set owner.

### 3.2.2. Account

The account object defines an account with money and other such objects:

  * String AccountId
  * Boolean isInternal
  * String bankNumber
  * String routeNumber
  * String type
  * ACL acl <- access control list
  * DebitCard debitCard
  * Decimal balance

The "isInternal" field should determine the behavior of the object.
For instance, only internal accounts should have a debit card or a balance.
Balance for external accounts may be possible but also may not be;
because of this, they should not be set.
Only in external accounts is the bankNumber truly relevant, but for consistency, all internal accounts should include out bank number.

The Decimal object should implement Binary Coded Decimals to allow for high accuracy, arbitrary precision calculations.
Types, like double, simply can't give the granularity for accurate withdraws or deposits from an account.
[decimal.js](https://github.com/MikeMcl/decimal.js/) look's promising as it does just that.

This object should make no logic for such functionality

The ACL should be some kind of list of users and their roles on the account.
They should be in a form like:

	{
		<username>: [role1, role2]
	}

roles should be one of the following:

  * read, they can see the account's details
  * send, they can send money to the account, but not necessarily see the details.
  * charge, they can charge up to a limit, should be reversible
  * owner, they can completely control the account, by default the user who created the account has this role.

Debit card should be an object that includes an indeterminate member variable/s that describe an ATM card for the account.
It should at least have a card number.

### 3.2.3. Transactions

The transaction object shall allow a user to defer or to set a recurring transfer from one account to another.

In the bill pay type, the job is a recurrent transfer to an organization's account.

  * String TransactionId
  * Boolean isRecurring 
  * Date startAt <- when to fire off
  * String to <- an account id
  * String from <- an account id
  * Decimal transferAmount
  * String notes <- optional

### 3.2.4. History

  * String accountId <- account effected
  * Date date <- date of transaction
  * String notes <- what happened
  * Decimal amount <- changed amount

The notes field should have a message that describes what happened.
For instance:

	%TYPE - %USER_ACCOUNT to %OTHER_ACCOUNT
