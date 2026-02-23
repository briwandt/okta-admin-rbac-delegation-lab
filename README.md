## 🛡️ Okta OIDC RBAC Authorization Lab
## 🔐 Role-Based Access Control (RBAC) with OIDC & Custom Claims

This lab demonstrates how to implement group-based authorization using:

Okta OIDC (Authorization Code Flow)

Custom ID Token claims

Authorization Server configuration

Group-to-role mapping

JWT validation

The goal was to dynamically inject RBAC group membership into an ID token and validate access logic based on that claim.

## 🧠 Architecture Overview

User authenticates via Okta (Authorization Code Flow)

Okta issues ID Token

Custom groups claim is injected

Application reads group claim

Authorization logic is enforced based on group membership

## 🏗️ Step 1 — Create OIDC Application

Configured a Web Application using:

Grant Type: Authorization Code

Client Authentication: Client Secret

Redirect URI: http://localhost:8080/authorization-code/callback

📸 OIDC App Configuration

![OIDC App Configuration](images/oidc-app-config.png)

## 👥 Step 2 — Create RBAC Groups

Created three role groups:

RBAC-Admins

RBAC-Analysts

RBAC-Viewers

Users were assigned based on role.

📸 RBAC Groups Created

![RBAC Groups](images/rbac-groups.png)

