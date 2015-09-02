# API Query Parameter Spec

Let's face it - query parameters to search API endpoints are getting pretty crazy. Certain people like to use the `q` parameter, some people search by field name, some through some other bunch of standards. People look to existing APIs to help them define a consistent approach but there is no _de facto_ standard.

We here at Member get Member Company want to change that.

## Query Parameters?

What the hell are we going on about, you say?

```
https://api.example.com/users?username=steve
```

This works well enough to find a user with the username of "steve", but an exact text match may not be what you want to find.

So without further ado, here's how we propose APIs should be queried!

### An exact string match

```
https://api.example.com/users?username=steve
```

### A partial string match

```
https://api.example.com/users?username=*steve*
```

### A range of values

```
https://api.example.com/users?age=18...25
```

### Greater than + Lesser than (or equal to)

We use familiar operators - `>`, `<`, `>=`, `<=` (shown URI-encoded)

```
https://api.example.com/users?age%3D%3E18
https://api.example.com/users?age%3D%3C25
https://api.example.com/users?age%3D%3E%3D18
https://api.example.com/users?age%3D%3C%3D25
```

### Sorting by a value

Default is ascending, negating with a `-` sets to descending.

```
https://api.example.com/users?order=createdAt
https://api.example.com/users?order=-createdAt
```

### Amount of results

A `limit=0` sets no limit.

```
https://api.example.com/users?limit=5
https://api.example.com/users?limit=0
```

### Pagination

```
https://api.example.com/users?page=1&perPage=20
```
