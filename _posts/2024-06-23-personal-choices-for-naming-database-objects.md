---
title: Personal Choice for Naming Database Objects
date: 2024-06-23 18:00:00 +0800
categories: [Backend, Database]
tags: [initial version]
description: My personal flavored naming conventions for database objects are presented in this post, which is definitely not a standard or perfect solution and, hopefully, I will update this post when I get more experienced in the future.
---

Naming things is hard, and it seems to be even harder when it comes to database objects since we can easily find different opinions on this on the Internet, so we have to make choice and the following is mine.



## TL; DR

Read [My Choices](#my-choices) for my personal flavored naming conventions if you're in a hurry but **DO NOT** treat them as standard or perfect solutions. 



## My Principles

Basically I made my choices based on two principles: 

* **Industrial Conventions**: means that this is **accepted by most** of the engineers in the industry. 
  * But I can't prove my choice is really "accepted by most" with figures so it's really empirical and may not be accurate. 
* **Possibility to be Correct**: means that, by adopting this convention, I would be more likely to be correct, rather than wrong, when defining and/or manipulating those database objects. 
  * To achieve this, my choices should be **unambiguous and intuitive**. 



## My Choices

| Possible Choices                           | My Choice                                      | Why                                                          |
| ------------------------------------------ | ---------------------------------------------- | ------------------------------------------------------------ |
| `CamelCase` or `underscore_name`           | `underscore_name`                              | 1. I've seen large scale commercial system uses this. <br/>2. It's unambiguous for both human and the RDBMS and/or OS. <br/>(1) For example, phase "under value" and word "undervalue" is not the same but when using CamelCase form of name in a case-insensitive OS, they are going to be the same word "undervalue". |
| Plural or Singular table (relation) name   | Singular                                       | It increases the chances to be correct. For example, should we choose "persons" or "people" if we use plural form of table names? |
| Prefixed an app name to table name or not  | No                                             | There is better solution for this purpose in modern database management systems. For example, [MySQL](https://dev.mysql.com/doc/refman/8.4/en/identifier-qualifiers.html) and [PostgreSQL](https://www.postgresql.org/docs/current/ddl-schemas.html). |
| Uppercase or Lowercase                     | Lowercase                                      | Similar to why we should use `underscore_name`               |
| Abbreviate or not                          | No for most of the time but Yes for some cases | Reasons for No: <br/>1. Abbreviations may be vary which increases the chances to be wrong. <br/>2. Different words can be abbreviated to one same word which increases ambiguity and confuses people. <br/>The Yes case: <br/>Wildly used abbreviations like `i18n` and `l10n`. Just do not use abbreviations when in doubt. |
| `prefixed_id` or pure `id`                 | Yes for foreign keys but No for primary key    | For primary key, some may argue `person.person_id` is much more unambiguous than `person.id` but it's kind of redundant and some may insist arguing that, by doing this, we can avoid mistakes like `person.id = email.id`. Well, I think it should be obviously wrong for you, being a sophisticated engineer. |
| Use reserved words (with backticks) or not | No                                             | 1. Kind of a virtue that we, being software engineer, should have. <br/>2. It's more compatible with some less well designed systems. |



## References

1. [How I Write SQL, Part 1: Naming Conventions](https://launchbylunch.com/posts/2014/Feb/16/sql-naming-conventions/)
2. [Database Naming Standards - DEV Community](https://dev.to/ovid/database-naming-standards-2061)
3. [Best practices for naming tables and columns in MySQL 8 - Sling Academy](https://www.slingacademy.com/article/best-practices-for-naming-tables-and-columns-in-mysql-8/)
4. [MySQL :: MySQL 8.4 Reference Manual :: 11.2.2 Identifier Qualifiers](https://dev.mysql.com/doc/refman/8.4/en/identifier-qualifiers.html)
