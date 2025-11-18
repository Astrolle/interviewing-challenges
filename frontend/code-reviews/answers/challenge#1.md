# Answers

Issues to identify:

Sequential fetching (should use Promise.all for parallel requests)
Sequential processing of users (should parallelize)
Mixing async/await with .then()
Catch block doesn't re-throw or return error
No status code checking
Function might return undefined on error
