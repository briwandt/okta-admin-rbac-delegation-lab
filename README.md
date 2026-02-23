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

## 🎯 Step 3 — Assign Groups to Application

Each RBAC group was assigned to the OIDC app under Assignments → Groups.

This ensures group membership can be evaluated during token issuance.

📸 Application Group Assignments

![App Group Assignments](images/app-group-assignments.png)

## 🧾 Step 4 — Configure Custom Groups Claim

Configured a custom claim in the Authorization Server:

Name: groups

Token Type: ID Token

Value Type: Groups

Filter: Matches regex ^RBAC-.*

Included in: Any scope

This dynamically injects only RBAC-related groups into the ID token.

📸 Custom Claim Configuration
![Groups Claim Configuration](images/groups-claim-config.png)

## 🔄 Step 5 — Authorization Code Flow

Executed Authorization Code Flow:

/oauth2/default/v1/authorize

Scopes requested:

openid profile email groups

Returned authorization code was exchanged for ID Token.

