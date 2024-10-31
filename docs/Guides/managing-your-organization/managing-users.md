---
layout: default
title: Manage users and roles
description: Learn about user permissions and how to add and remove users in a Firebolt account.
nav_order: 8
parent: Manage organization
---

# Manage users and roles
{: .no_toc}

In Firebolt, an **organization** can have multiple **accounts**, each serving as a separate workspace for managing resources and data. Within each account, users are created to control access, with their identities defined through logins or service accounts. **Logins** are associated with individual human users, each authenticated by unique credentials, allowing them to interact directly with Firebolt's resources according to assigned roles. **Service accounts** provide programmatic access for applications and automated processes within the account, such as data pipelines or monitoring tools. Each login and service account is linked to specific **roles**, which define their permissions, ensuring that access is managed efficiently and securely across the organization.

## <img src="../../assets/images/icon-user-bangs.png" alt="Icon for a Firebolt user." width="30"/> Users

 A **user** is a distinct identity that interacts with the Firebolt platform. Each user is assigned specific **roles**, which determine what actions they can perform and which resources they can access. Users are essential for controlling access in Firebolt and are managed through **role-based access control (RBAC)**. Users authenticate via **logins** or **service accounts**, depending on whether they are human users or machine-based processes.

## <img src="../../assets/images/icon-login.png" alt="Icon for a Firebolt login for human access." width="30"/> Logins

A **login** in Firebolt represents a **human user** and is associated with an individual’s credentials, identified by an **email address**. Logins are tied to user roles, which define what the individual can access or modify. A login is primarily used for human authentication and allows a user to access the platform, run queries, and interact with databases and other resources. For instance, a login object might be created for a specific person such as `kate@acme.com`, and this login is linked to roles that control the permissions.

## <img src="../../assets/images/icon-service-account.png" alt="Icon for a Firebolt service account for programmatic access." width="30"/> Service accounts

A **service account** is used to represent a **machine or application** rather than a human user. It allows automated processes to authenticate and interact with Firebolt resources. A service account is used for programmatic access, such as in pipelines, monitoring systems, application data access, and scheduled queries. Service accounts are associated with roles just like logins but are designed to operate without human intervention. For example, a service account might be used for a data pipeline that regularly ingests data into Firebolt. Each service account must be associated with a user. For more information about how to create and manage service accounts, see [Manage programmatic access to Firebolt](./service-accounts.md).








Users are managed at the account level and are linked to logins or service accounts for programmatic use to gain access to Firebolt. Roles are granted to users to determine access to objects in Firebolt. You can add, edit or delete users using SQL or in the UI. 

To view all users, click **Govern** to open the govern space, then choose **Users** from the menu, or query the [information_schema.users](../../sql_reference/information-schema/users.md) view. 

{: .note}
Managing users requires the account_admin role.

## Create a new user

### SQL 
To create a user using SQL, use the [CREATE USER](../../sql_reference/commands/access-control/create-user.md) statement. For example:

```sql
CREATE USER alex;
```

### UI
To create a user via the UI:

![Govern > Users](../../assets/images/userspage.png)

1. Click **Govern** to open the govern space, then choose **Users** from the menu.
2. From the Users management page, choose **Create user**.
3. Enter the new user's name. This user name can be any string - it can contain spaces, and non-alpha-numeric characters such as exclamation points (!), percent signs (%), at sign(@), dot sign (.), underscore sign (_), minus sign (-), and asterisks (*), but if the string contains these spaces or non-alphanumeric characters, it must be enclosed in single or double quotes. 

4. Optionally, you can:
  - Choose **Associate a login** or **Associate a service account**, then choose the relevant login or service account from the list.
  - Choose a **default database** for the user.
  - Choose a **default engine** for the user. 
  - Choose **roles** to be granted to the user. 

## Edit an existing user

### SQL 
To edit an existing user using SQL, use the [ALTER USER](../../sql_reference/commands/access-control/alter-user.md) statement. For example:

```sql
ALTER USER "alex" RENAME TO "alexs";
```
or 
```sql
ALTER USER alex SET LOGIN="alexs@acme.com";
```

### UI
To edit a user via the UI:
1. Click **Govern** to open the govern space, then choose **Users** from the menu.
2. Search for the relevant user using the top search filters or by scrolling through the users' list. Hover over the right-most column to make the user menu appear, then choose **Edit user**.
3. Edit the desired fields and choose **Save**.

<img src="../../assets/images/edituser.png" alt="Edit user" width="500"/>

## Deleting an existing user

### SQL 
To delete an existing user using SQL, use the [DROP USER](../../sql_reference/commands/access-control/drop-user.md) statement. For example:

```sql
DROP USER "alex";
```

### UI
To delete a user via the UI:
1. Click **Govern** to open the govern space, then choose **Users** from the menu.
2. Search for the relevant user using the top search filters or by scrolling through the users list. Hover over the right-most column to make the user menu appear, then choose **Delete user**.
3. Choose **Confirm**.

<img src="../../assets/images/deleteuser.png" alt="Delete user" width="500"/>
