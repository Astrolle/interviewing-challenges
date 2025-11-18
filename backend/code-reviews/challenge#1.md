# Challenge #1

## Describe the errors that you see

```typescript
@Get()
async getUsers() {
  return this.service.getAllUsers().then((users) => {
    console.log(users)
    return users
  })
}
```
