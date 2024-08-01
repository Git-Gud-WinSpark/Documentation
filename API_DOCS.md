# API DOCS FOR STUDY-CO PLATFORM

# Table of contents  
1. [Introduction](#introduction)
2. [Base URL](#base-url)
3. [Authentication](#authentication)
4. [User Management](#1-user-management)
   1. [Sign Up](#11-sign-up)
   2. [Sign In](#12-sign-in)
   3. [Fetch User](#13-fetch-user)
   4. [Get User](#211-get-user)
5. [Study Group Management](#2-study-group-management)
   1. [Create Community](#21-create-community)
   2. [Create Channel](#22-create-channel)
   3. [Send Chat Message](#23-send-chat-message)
   4. [Get Channel Chats](#24-get-channel-chats)
   5. [Add User to Community](#25-add-user-to-community)
   6. [List All Communities](#26-list-all-communities)
   7. [List User's Communities](#27-list-users-communities)
   8. [Send P2P Chat Message](#28-send-p2p-chat-message)
   9. [Get P2P Chats](#29-get-p2p-chats)
   10. [List P2P Conversations](#210-list-p2p-conversations)
6. [Progress Tracking](#3-progress-tracking)
   1. [Set Progress Track](#31-set-progress-track)
   2. [Get Live Tasks](#32-get-live-tasks)
   3. [Get Subtasks](#33-get-subtasks)
   4. [Complete Task](#34-complete-task)
   5. [Set Live Tasks](#35-set-live-tasks)
   6. [Set Time Spent](#36-set-time-spent)
7. [Error Responses](#error-responses)

## Introduction

Study-co platform API categorizes into 3 major categories:
1. **User Management**: This category includes all the APIs related to user creation, login, account management, profile management, etc.
2. **Study Group Management**: This category includes all the APIs related to study group creation, addition of members, group chat, joining of study groups, etc.
3. **Resource Management**: This category includes all the APIs related to resource sharing, file upload, progress tracking, etc.

## Base URL

All API endpoints are relative to: `http://localhost:3000`

## Authentication

Most endpoints require a JWT token for authentication. This token should be included in the request body as the `token` field.

## User Management

### 1.1 Sign Up

Create a new user account.

- **URL**: `/signup`
- **Method**: `POST`
- **Body**:
```json
  {
    "username": "string",
    "email": "string",
    "password": "string"
  }
```
- Success Response:

    - Code: 200
    - Content: JWT token

### 1.2 Sign In

Authenticate a user and receive a JWT token.

- **URL**: `/signin`
- **Method**: `POST`
- **Body**:
```json
{
  "email": "string",
  "password": "string"
}
```

- Success Response:

    - Code: 200
    - Content: JWT token



### 1.3 Fetch User

Retrieve information about a specific user by ID.

- **URL**: `/api/fetchUser`
- **Method**: `POST`
- **Body**:
```json
{
  "userID": "string"
}
```
- Success Response:

    - Code: 200
    - Content: User object

### 2.11 Get User

Retrieve information about a user by their username.

- **URL**: `/api/getUser`
- **Method**: `POST`
- **Body**:

  ```json
  {
    "userName": "string"
  }
## 2. Study Group Management

### 2.1 Create Community

Create a new study group community.

- **URL**: `/api/createCommunity`
- **Method**: `POST`
- **Body**:

```json
{
  "token": "string",
  "communityName": "string",
  "tags": ["string"]
}
```

- Success Response:

    - Code: 200
    - Content: Confirmation message

### 2.2 Create Channel

Create a new channel within a study group community.

- **URL**: `/api/createChannel`
- **Method**: `POST`
- **Body**:
```json
{
  "communityID": "string",
  "channelName": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Confirmation message



### 2.3 Send Chat Message

Send a chat message in a channel.

- **URL**: `/api/chat`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "receiverID": "string",
  "message": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Confirmation message



### 2.4 Get Channel Chats

Retrieve chat messages from a channel.

- **URL**: `/api/getChats`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "receiverID": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Array of chat messages


### 2.5 Add User to Community

Add a user to an existing study group community.

- **URL**: `/api/addCommunity`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "communityID": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Confirmation message



### 2.6 List All Communities

Retrieve a list of all study group communities.

- **URL**: `/api/listAllCommunity`
- **Method**: ``GET``
- Success Response:

    - Code: 200
    - Content: Array of community objects



### 2.7 List User's Communities

Retrieve a list of study group communities the authenticated user belongs to.

- **URL**: `/api/listUserCommunity`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Array of community objects



### 2.8 Send P2P Chat Message

Send a direct message to another user.

- **URL**: `/api/p2pChat`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "receiverID": "string",
  "message": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Confirmation message



### 2.9 Get P2P Chats

Retrieve direct messages between two users.

- **URL**: `/api/getP2PChats`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "receiverID": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Array of chat messages



### 2.10 List P2P Conversations

Retrieve a list of all direct message conversations for the authenticated user.

- **URL**: `/api/listP2PConversations`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string"
}
```

- Success Response:

    - Code: 200
    - Content: Array of conversation objects



## 3. Progress Tracking

### 3.1 Set Progress Track

Set progress tracking information for a user in a specific community and channel.

- **URL**: `/progressTrack`
- **Method**: `POST`
- **Body**:
``` json
{
  "token": "string",
  "commnuityID": "string",
  "channelID": "string",
  "liveTask": ["string"],
  "subtask": ["string"]
}
```

- Success Response:

  - Code: 200
  - Content: Confirmation message

### 3.2 Get Live Tasks
Retrieve live tasks for the authenticated user.

- **URL**: `/progressTrack/getLiveTask`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string"
}
```

- Success Response:

  - Code: 200
  - Content: Array of live tasks

### 3.4 Complete Task
Mark a task or subtask as complete.

- **URL**: `/progressTrack/completeTask`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "communityID": "string",
  "channelID": "string",
  "liveTaskID": "string",
  "subtaskID": "string"
}
```
- Success Response:

  - Code: 200
  - Content: Confirmation message



### 3.5 Set Live Tasks
Set multiple live tasks for a user in a specific community and channel.

- **URL**: `/progressTrack/setLiveTask`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "communityID": "string",
  "channelID": "string",
  "liveTask": [
    {
      "name": "string",
      "status": boolean,
      "completionTime": "string"
    }
  ]
}
```
- Success Response:

  - Code: 200
  - Content: Confirmation message



### 3.6 Set Time Spent
Record time spent on a specific task or subtask.

- **URL**: `/progressTrack/setTime`
- **Method**: `POST`
- **Body**:
```json
{
  "token": "string",
  "communityID": "string",
  "channelID": "string",
  "liveTaskID": "string",
  "subtaskID": "string",
  "timeSpent": "string"
}
```

- Success Response:

  - Code: 200
  - Content: Confirmation message

### Error Responses

All endpoints may return the following error responses:

- ***Code 400*** : BAD REQUEST

    - Content: Error message explaining the bad request


- ***Code 401*** : UNAUTHORIZED

    - Content: Error message indicating invalid or missing authentication


- ***Code 500** : INTERNAL SERVER ERROR

   - Content: Error message describing the server error

- ***Code 403*** : FORBIDDEN
   - Content: Error message indicating that the user does not have permission to access the requested resource.  