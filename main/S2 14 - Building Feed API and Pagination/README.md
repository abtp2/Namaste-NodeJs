# DevTinder Project - API Development: Feed API and Pagination

## Code Demonstration Link

* [DevTinder Backend Repository](https://github.com/akshadjaiswal/devTinder-backend) Project
---

## Overview
Today's focus is on enhancing the **Get /user/feed** API by implementing pagination. The API is designed to retrieve user profiles while filtering out specific users and limiting the number of results per request.

---

## API Details

### Endpoint:
- **GET `/user/feed`**

### Purpose:
- Fetch profiles of other users while excluding:
  - The logged-in user.
  - Existing connections.
  - Ignored users.
  - Users who have already received a connection request.

---

## Thought Process for API Development

### 1. Filtering Out Unwanted Users
- Use a **Set data structure** to collect and store the following user IDs:
  - `fromUserId` and `toUserId` from all connection requests associated with the logged-in user.
  - This prevents duplicate filtering and ensures an optimized query.

- Use **MongoDB operators**:
  - **$nin**: Exclude multiple user IDs in a single query.
  - **$ne**: Ensure the logged-in user's profile is not included in the query results.

### 2. Implementing Pagination
- **Why Pagination?**
  - If there are **1000+ users**, returning all users at once would be inefficient.
  - Pagination ensures that only a specific number of users are retrieved per request.

- **Fetching `page` and `limit` from Request Parameters**:
  - `page`: Determines which page of users the client is requesting.
  - `limit`: Defines the maximum number of users to be returned.

- **Calculating the Skip Value**:
  - The formula for calculating skipped records:
    ```
    skip = (page - 1) * limit
    ```
  - `skip`: Number of users to ignore before returning results.

- **Applying Skip and Limit in the Query**:
  - `skip()` is used to move past the number of users from previous pages.
  - `limit()` ensures only the requested number of users is retrieved.

---

## Key Concepts

### 1. **Set-Based Filtering for Efficient Querying**
- Using a **Set** prevents duplicates and ensures only valid user IDs are excluded from the query.
- This helps in maintaining fast query performance.

### 2. **MongoDB Query Optimization**
- **$nin**: Excludes all users in the filter list.
- **$ne**: Ensures the logged-in user's profile does not appear in the results.

### 3. **Pagination for Better Performance**
- **Pagination prevents excessive data loading**, reducing server response time.
- Allows for smooth user experience with "Load More" or infinite scrolling features.

---

```javascript
   userRouter.get("/user/feed", userAuth, async (req, res) => {
  try {
    const loggedInUser = req.user;

    const page = parseInt(req.query.page || 1);
    let limit = parseInt(req.query.limit || 10);
    limit = limit > 50 ? 50 : limit;
    const skip = (page - 1) * limit;

    const connectionRequest = await ConnectionRequestModel.find({
      $or: [{ fromUserId: loggedInUser._id }, { toUserId: loggedInUser._id }],
    }).select("fromUserId toUserId");

    const hideUsersFromFeed = new Set();
    connectionRequest.forEach((req) => {
      hideUsersFromFeed.add(req.fromUserId.toString());
      hideUsersFromFeed.add(req.toUserId.toString());
    });

    const users = await User.find({
      $and: [
        { _id: { $nin: Array.from(hideUsersFromFeed) } },
        { _id: { $ne: loggedInUser._id } },
      ],
    })
      .select(USER_SAFE_DATA)
      .skip(skip)
      .limit(limit);

    res.send(users);
  } catch (error) {
    res.status(400).send("ERROR: " + error.message);
  }
});
module.exports = userRouter;

```

## Benefits of This Approach

1. **Improved Performance**:
   - Querying a subset of users per request optimizes response times.

2. **Scalability**:
   - Ensures that the API remains efficient even with a large number of users.

3. **Better User Experience**:
   - Users receive paginated data, making the browsing experience smooth.

---

## Conclusion
The **Get /user/feed** API now supports **pagination**, ensuring that user profiles are efficiently retrieved while maintaining a smooth and scalable user experience. Filtering with **MongoDB queries** and **pagination techniques** enhances the performance and usability of the DevTinder app.
