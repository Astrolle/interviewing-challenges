# Challenge #1

## Identify which are the pitfalls this functions have

```Javascript
async function fetchUserData(userId) {
  try {
    const user = await fetch(`/api/users/${userId}`).then(r => r.json());
    const posts = await fetch(`/api/users/${userId}/posts`).then(r => r.json());
    const comments = await fetch(`/api/users/${userId}/comments`).then(r => r.json());
    
    return {
      user,
      posts,
      comments
    };
  } catch (error) {
    console.log('Error:', error);
  }
}

async function processUsers(userIds) {
  const results = [];
  
  for (let id of userIds) {
    const userData = await fetchUserData(id);
    results.push(userData);
  }
  
  return results;
}
```
