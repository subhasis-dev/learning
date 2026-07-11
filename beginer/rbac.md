# RBAC (Role-Based Access Control) - Beginner Implementation Guide

## Objective

The goal of this task is to understand and implement a basic **Role-Based Access Control (RBAC)** system for a web application using **Python (FastAPI)** as the backend and **React JS** as the frontend.

This document is intended for developers who are new to RBAC and provides the scope, concepts, and implementation roadmap.

---

# Learning Objectives

By completing this task, you should understand:

* What RBAC is and why it is needed
* Authentication vs Authorization
* Roles, Permissions, and Users
* Database relationships
* How permissions are validated in the backend
* How permissions are used in the frontend
* How JWT works with RBAC
* Basic enterprise RBAC design principles

---

# What is RBAC?

RBAC (Role-Based Access Control) is a security model that controls what users are allowed to do within an application.

Instead of assigning permissions directly to users, permissions are assigned to **roles**, and users are assigned one or more roles.

Example:

```
User

↓

Role

↓

Permissions

↓

Application Access
```

Example:

```
Admin
    Create User
    Update User
    Delete User
    Manage Roles

Manager
    View Users
    Update Projects

Employee
    View Dashboard
```

---

# Authentication vs Authorization

## Authentication

Verifies the identity of the user.

Example:

* Login
* Username/Password
* JWT Token

Question answered:

> Who are you?

---

## Authorization

Determines what the authenticated user is allowed to access.

Question answered:

> What are you allowed to do?

---

# Core RBAC Concepts

## User

A person who logs into the application.

Example:

```
John
Alice
David
```

---

## Role

A collection of permissions.

Example:

```
Admin

Manager

Employee
```

---

## Permission

A single action that can be performed.

Examples

```
user.read

user.create

user.update

user.delete

dashboard.view

project.create
```

---

# High-Level Architecture

```
Login

↓

Authentication

↓

JWT Token

↓

Authorization

↓

Roles

↓

Permissions

↓

Protected API
```

---

# Scope of Implementation

The implementation should include the following modules.

## Backend

* User Management
* Role Management
* Permission Management
* User-Role Assignment
* Role-Permission Assignment
* JWT Authentication
* Authorization Middleware
* Permission Validation

---

## Frontend

* Login
* Store JWT
* Fetch logged-in user permissions
* Protect routes
* Show/Hide UI based on permissions
* Display "Access Denied" when required

---

# Suggested Database Design

## User

```
id
name
email
password
```

---

## Role

```
id
name
description
```

---

## Permission

```
id
module
action
code
```

---

## UserRole

```
user_id
role_id
```

---

## RolePermission

```
role_id
permission_id
```

---

# Backend Learning Scope (FastAPI)

The developer should learn and implement:

* FastAPI project structure
* JWT authentication
* Dependency Injection
* Authorization middleware/dependencies
* CRUD APIs for Users, Roles, and Permissions
* Role and Permission mapping
* Protecting APIs using permissions
* Returning HTTP 403 for unauthorized requests

---

# Frontend Learning Scope (React)

The developer should learn and implement:

* Login flow
* JWT storage
* API authentication
* Route protection
* Permission-based component rendering
* Navigation/menu visibility based on permissions
* Handling unauthorized pages

---

# Expected API Flow

```
User Login

↓

JWT Generated

↓

React Stores Token

↓

API Request

↓

Validate JWT

↓

Load User Roles

↓

Load Permissions

↓

Permission Check

↓

Allow / Deny Request
```

---

# Example Permissions

```
dashboard.view

user.read

user.create

user.update

user.delete

role.read

role.create

role.update

permission.read

permission.update
```

---

# Deliverables

The developer should deliver:

* Database schema
* Backend APIs
* JWT authentication
* RBAC middleware/dependencies
* User-Role mapping
* Role-Permission mapping
* Protected APIs
* React authentication flow
* Route protection
* Permission-based UI rendering
* Basic documentation explaining the implementation

---

# Out of Scope (Phase 1)

The following features are **not** required in the initial implementation:

* Multi-tenant support
* Organization-level roles
* Hierarchical roles
* Dynamic policy engine
* Attribute-Based Access Control (ABAC)
* Row-level security
* Audit logs
* Permission caching
* Single Sign-On (SSO)
* OAuth/OpenID Connect integration

These can be considered in future phases after the basic RBAC implementation is complete.

---

# Success Criteria

The implementation will be considered complete when:

* Users can log in successfully.
* Users are assigned one or more roles.
* Roles have one or more permissions.
* Backend APIs enforce permission checks.
* Unauthorized requests return **403 Forbidden**.
* The frontend displays only the features the user is authorized to access.
* The code is modular, readable, and easy to extend.

---

# Recommended Learning Order

1. Understand Authentication vs Authorization.
2. Learn the RBAC concepts (User, Role, Permission).
3. Design the database schema.
4. Implement JWT authentication.
5. Implement Role and Permission CRUD APIs.
6. Map Users to Roles and Roles to Permissions.
7. Protect backend APIs.
8. Build React authentication.
9. Implement permission-based UI rendering.
10. Test different user roles and verify access control.
