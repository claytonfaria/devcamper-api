# DevCamper API

Backend API for the DevCamper application to manager bootcamps, courses, reviews, users and authentication

## Indices

- [Authentication](#authentication)

  - [Forgot Password](#1-forgot-password)
  - [Get Logged in User via Token](#2-get-logged-in-user-via-token)
  - [Login User](#3-login-user)
  - [Logout User](#4-logout-user)
  - [Register User](#5-register-user)
  - [Reset password](#6-reset-password)
  - [Update User Details](#7-update-user-details)
  - [Update User Password](#8-update-user-password)

- [Bootcamps](#bootcamps)

  - [Create New Bootcamp](#1-create-new-bootcamp)
  - [Delete Bootcamp](#2-delete-bootcamp)
  - [Get All Bootcamps](#3-get-all-bootcamps)
  - [Get Bootcamp by distance](#4-get-bootcamp-by-distance)
  - [Get Single Bootcamp](#5-get-single-bootcamp)
  - [Update Bootcamp](#6-update-bootcamp)
  - [Update Photo](#7-update-photo)

- [Courses](#courses)

  - [Create Course](#1-create-course)
  - [Delete Course](#2-delete-course)
  - [Get All Courses](#3-get-all-courses)
  - [Get Courses for Bootcamp](#4-get-courses-for-bootcamp)
  - [Get Single Course](#5-get-single-course)
  - [Update Course](#6-update-course)

- [Reviews](#reviews)

  - [Add Review for Bootcamp](#1-add-review-for-bootcamp)
  - [Delete Review](#2-delete-review)
  - [Get All Reviews](#3-get-all-reviews)
  - [Get Reviews for Bootcamp](#4-get-reviews-for-bootcamp)
  - [Get Single Review](#5-get-single-review)
  - [Update Review](#6-update-review)

- [Users](#users)

  - [Create User](#1-create-user)
  - [Delete User](#2-delete-user)
  - [Get All Users](#3-get-all-users)
  - [Get a Single User](#4-get-a-single-user)
  - [Update User](#5-update-user)

---

## Authentication

Routes for user authentication including register, login, reset password, etc

### 1. Forgot Password

Generat password Token and send email

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/auth/forgotpassword
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
|              |                  |             |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "email":"kevin@gmail.com"
}
```

### 2. Get Logged in User via Token

**_Endpoint:_**

```bash
Method: GET
Type: RAW
URL: {{URL}}/api/v1/auth/me
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 3. Login User

login user

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/auth/login
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "email":"john@gmail.com",
    "password":"123456"
}
```

### 4. Logout User

logout current user

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/auth/logout
```

### 5. Register User

Add user to database with encrypted password

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/auth/register
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "name":"Paul smith",
    "email":"paul@gmail.com",
    "password":"123456",
    "role":"user"
}
```

### 6. Reset password

Reset user password using token

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/auth/resetpassword/9db736b95648f3d9302ef2a41dd51ccc71980033
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "password":234567
}
```

### 7. Update User Details

Update logged in user name and email

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/auth/updatedetails
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "email":"john1@gmail.com",
    "name":"John Smith"
}
```

### 8. Update User Password

Update logged user password

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/auth/updatepassword
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "currentPassword":"123456",
    "newPassword":"234567"
}
```

## Bootcamps

Bootcamps CRUD functionality

### 1. Create New Bootcamp

Add new bootcamp to database. Must be authenticated and must be publisher or admin

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/bootcamps/
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "name": "Test",
		"description": "ModernTech has one goal, and that is to make you a rockstar developer and/or designer with a six figure salary. We teach both development and UI/UX",
		"website": "https://moderntech.com",
		"phone": "(222) 222-2222",
		"email": "enroll@moderntech.com",
		"address": "220 Pawtucket St, Lowell, MA 01854",
		"careers": ["Web Development", "UI/UX", "Mobile Development"],
		"housing": false,
		"jobAssistance": true,
		"jobGuarantee": false,
		"acceptGi": true
}
```

### 2. Delete Bootcamp

Delete bootcamp from database

**_Endpoint:_**

```bash
Method: DELETE
Type: RAW
URL: {{URL}}/api/v1/bootcamps/5f45f11a46f995769aaf8c93
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "name":"Clayton Faria",
    "email":"clayton@faria.com"
}
```

### 3. Get All Bootcamps

Fetch all bootcamps from database. Includes pagination, filtering, etc

**_Endpoint:_**

```bash
Method: GET
Type: RAW
URL: {{URL}}/api/v1/bootcamps
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "name":"Clayton Faria",
    "email":"clayton@faria.com"
}
```

### 4. Get Bootcamp by distance

Get bootcamps within a radius of a specific zipcode

**_Endpoint:_**

```bash
Method: GET
Type: RAW
URL: {{URL}}/api/v1/bootcamps/radius/02118/10
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "name":"Clayton Faria",
    "email":"clayton@faria.com"
}
```

### 5. Get Single Bootcamp

Get single bootcamp by ID

**_Endpoint:_**

```bash
Method: GET
Type: RAW
URL: {{URL}}/api/v1/bootcamps/1
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "name":"Clayton Faria",
    "email":"clayton@faria.com"
}
```

### 6. Update Bootcamp

Update single bootcamp in database

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/bootcamps/5f45f11a46f995769aaf8c93
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "careers":["Web Development", "Business"]
}
```

### 7. Update Photo

Route to upload a bootcamp photo

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/bootcamps/5d725a1b7b292f5f8ceff788/photo
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "careers":["Web Development", "UI/UX"]
}
```

## Courses

Create, read, update and delete courses

### 1. Create Course

Create a course for a specific bootcamp

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/bootcamps/5f45f9e2e0327f788323907f/courses
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json |             |

**_Body:_**

```js
{
    "title": "UI/UXm2",
		"description": "In this course you will learn to create beautiful interfaces. It is a mix of design and development to create modern user experiences on both web and mobile",
		"weeks": 12,
		"tuition": 10000,
		"minimumSkill": "intermediate",
		"scholarhipsAvailable": true
}
```

### 2. Delete Course

Remove Course from Database

**_Endpoint:_**

```bash
Method: DELETE
Type: RAW
URL: {{URL}}/api/v1/courses/5f45fa0de0327f7883239080
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 3. Get All Courses

Get all courses from the database

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/courses
```

### 4. Get Courses for Bootcamp

Get the specific courses for a bootcamp

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/bootcamps/5d713995b721c3bb38c1f5d0/courses
```

### 5. Get Single Course

Show a single course by ID

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/courses/5d725a4a7b292f5f8ceff789
```

### 6. Update Course

Update Course in the database by ID

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/courses/5f45fa0de0327f7883239080
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "tuition":15000,
    "minimumSkill":"advanced"
}
```

## Reviews

Manage course reviews

### 1. Add Review for Bootcamp

Insert review for a specific bootcamp

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/bootcamps/5f4757c3a4d069a732f55af2/reviews
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "title":"Add review from mary",
    "text":"shit a lt",
    "rating": 9
}
```

### 2. Delete Review

Delete review from the databse

**_Endpoint:_**

```bash
Method: DELETE
Type:
URL: {{URL}}/api/v1/reviews/5f4758a5a4d069a732f55af6
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 3. Get All Reviews

Get all reviews from database and populate with bootcamp name and description

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/reviews
```

### 4. Get Reviews for Bootcamp

Fetch the reviews for a specific bootcamp

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/bootcamps/5d725a1b7b292f5f8ceff788/reviews
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 5. Get Single Review

Fetch a review from database by id and populate Bootcamp name and description

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/reviews/5d7a514b5d2c12c7449be027
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 6. Update Review

Update Review in the database

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/reviews/5f4757faa4d069a732f55af3
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "title":"Great"
}
```

## Users

CRUD functionality for users only available to Admins

### 1. Create User

Add user to database (admin)

**_Endpoint:_**

```bash
Method: POST
Type: RAW
URL: {{URL}}/api/v1/users/
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "name": "Clayton Faria",
    "email": "clayton@gmail.com",
    "password":"123456"
}
```

### 2. Delete User

Delete an user from database (admin)

**_Endpoint:_**

```bash
Method: DELETE
Type: RAW
URL: {{URL}}/api/v1/users/5f4721b7ba9cca9e86cddea7
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 3. Get All Users

Get all users (admin)

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/users
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 4. Get a Single User

Get a single user (admin)

**_Endpoint:_**

```bash
Method: GET
Type:
URL: {{URL}}/api/v1/users/5c8a1d5b0190b214360dc036
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

### 5. Update User

Update user in database (admin)

**_Endpoint:_**

```bash
Method: PUT
Type: RAW
URL: {{URL}}/api/v1/users/5f4721b7ba9cca9e86cddea7
```

**_Headers:_**

| Key          | Value            | Description |
| ------------ | ---------------- | ----------- |
| Content-Type | application/json | JSON type   |

**_Body:_**

```js
{
    "name": "Clayton Rogerio",
    "email": "rogerio@gmail.com"
}
```

---

[Back to top](#devcamper-api)

> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2020-08-27 17:20:24 by [docgen](https://github.com/thedevsaddam/docgen)
