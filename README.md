# graphql-express
Nodejs and Express based application for demostrate the GraphQL features

## Main Reference: 
**Ref:**:https://www.youtube.com/watch?v=ZQL7tL2S0oQ&list=PLqWtPHZ2ZkWZVw35pFvGXis0a7W91Ed3F&index=9

## GraphQL API call from client using fetch: 
**Ref:**: https://www.youtube.com/watch?v=0ZJI4cBS4JM&list=PLqWtPHZ2ZkWZVw35pFvGXis0a7W91Ed3F&index=3&t=651s

# Usage

## Sample :
```javascript
query {
    message
}
```

or

```javascript
{
    message
}

```

## Other Query Samples:

```javascript

{
    books{
        id
        name
    }
}

{
    books{
        id
        author{
            name
        }
    }
}

{
    authors{
        id
        name
    }
}

{
    authors{
        id
        name
        books{
            name
        }
    }
}

```

## Query based on Search params

```javascript

{
    book(id: 1){
        name
    }
}

{
    book(id: 1){
        name
        author{
            name
        }
    }
}

{
    author(id: 2){
            name
        }
}

```

## Mutation(POST/DELETE/PUT) query samples

```javascript

/** Add new Book */

mutation {
    addBook(name: 'Jithin Sebastian', authorId: 2){
        id
    }
}

/* */

/* For Fetch all books data */

{
    books{
        id
        name
    }
}

/* */

/** Add new Author */

mutation {
    addAuthor(name: 'New Author') {
        id
        name
    }
}

/* */

/* For Fecth all authors data */
{
    authors{
        id
        name
        books {
            name
        }
    }
}

/* */

```

# Additional Info
## Sample API call from a Javascript Client(Using native 'fetch' method)

```javascript

function queryFetch(query, variables) {
  return fetch('https://countries.trevorblades.com/', {
    method: 'POST',
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      query: query,
      variables: variables
    })
  }).then(res => res.json())
}

* Sample Query *

function getContinentCountries(continentCode) {
  return queryFetch(`
    query getCountries($code: String) {
      continent(code: $code) {
        countries {
          name
        }
      }
    }
  `, { code: continentCode }).then(data => {
    return data.data.continent.countries
  })
}

```

